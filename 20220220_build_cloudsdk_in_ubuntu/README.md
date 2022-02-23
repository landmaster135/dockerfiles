# Test

## Prepare docker image to run docker container.

Use [this repository]().

## Build and Run Docker

DockerイメージをBuildする

```dosbatch
docker build -t my-cloudsdk-container .
```

Dockerイメージを起動する

```dosbatch
docker run -it --rm --name my-running-container my-cloudsdk-container
```

両方まとめて実行する

```dosbatch
docker build -t my-cloudsdk-container . && docker run -it --rm --name my-running-container my-cloudsdk-container
```

## Execute shell script in the CLI in the container after docker run

If you want more information, [refer here](https://dev.classmethod.jp/articles/google-cloud-auth-with-workload-identity/)

### 1-1. Check version of Cloud SDK.

```shell
gcloud -v
```

### 1-2. Initialize

Initialize Cloud-SDK in the built container image

```shell
gcloud init
```

### 2-1. Declare env variables

```shell
export PROJECT_ID="AAAAAAAAAAAAAA"
export SERVICE_ACCOUNT_NAME="BBBBBBBBBBBBB"
export DISPLAY_NAME="CCCCCCCCCCCC"
export DESCRIPTION="DDDDDDDDDDDDDDDDDD"
```

### 2-2. GitHub Actions上で利用するサービスアカウントを作成

```shell
gcloud iam service-accounts create "${SERVICE_ACCOUNT_NAME}" --project "${PROJECT_ID}" --display-name "${DISPLAY_NAME}" --description "${DESCRIPTION}"
```

### 2-3. サービスアカウントに権限を付与する

```shell
gcloud projects add-iam-policy-binding "${PROJECT_ID}" --role="roles/editor" --member="serviceAccount:${SERVICE_ACCOUNT_NAME}@${PROJECT_ID}.iam.gserviceaccount.com"
```

### 2-4. IAM Service Account Credentials APIを有効化する。

サービスアカウントの一時的な認証情報を作成できるようにするために、IAM Service Account Credentials APIを有効化する。

```shell
gcloud services enable iamcredentials.googleapis.com --project "${PROJECT_ID}"
```

### 3-1. Declare env variables

```shell
export POOL_NAME="EEEEEEEEEEEEE"
export DISPLAY_POOL_NAME="FFFFFFFFFFFFFF"
export POOL_DESCRIPTION="GGGGGGGGGGGGGGGGGGGGG"
```

### 3-2. Workload Identityプールを作成する

Workload Identityプールは外部IDとGoogle Cloudとの紐付けを設定したWorkload Identityプロバイダをグループ化し管理するために、Workload Identityプールを作成する。

```shell
gcloud iam workload-identity-pools create "${POOL_NAME}" --project="${PROJECT_ID}" --location="global" --display-name="${DISPLAY_POOL_NAME}" --description="${POOL_DESCRIPTION}"
```

### 3-3. Workload IdentityプールのIDを取得して、環境変数に代入する

```shell
export WORKLOAD_IDENTITY_POOL_ID=`gcloud iam workload-identity-pools describe "${POOL_NAME}" --project="${PROJECT_ID}" --location="global" --format="value(name)"`
```

### 4-1. Declare env variables

```shell
export PROVIDER_NAME="HHHHHHHHHHHHHHHHHH"
export DISPLAY_PROVIDER_NAME="IIIIIIIIIIIIIIIII"
```

### 4-2. Workload Identityプロバイダを作成する

先ほど作成したWorkload Identityプールの中にWorkload Identityプロバイダを作成する

```shell
gcloud iam workload-identity-pools providers create-oidc "${PROVIDER_NAME}" --project="${PROJECT_ID}" --location="global" --workload-identity-pool="${POOL_NAME}" --display-name="${DISPLAY_PROVIDER_NAME}" --attribute-mapping="google.subject=assertion.sub,attribute.actor=assertion.actor,attribute.repository=assertion.repository" --issuer-uri="https://token.actions.githubusercontent.com"
```

### 5-1. Declare env variables

```shell
export REPO="JJJJJJJ/KKKKKKKKKKK"
```

### 5-2. 環境変数のREPOにGitHub Actionsを動かすリポジトリを設定し、IAMポリシーバインディングを作成する

```shell
gcloud iam service-accounts add-iam-policy-binding "${SERVICE_ACCOUNT_NAME}@${PROJECT_ID}.iam.gserviceaccount.com" --project="${PROJECT_ID}" --role="roles/iam.workloadIdentityUser" --member="principalSet://iam.googleapis.com/${WORKLOAD_IDENTITY_POOL_ID}/attribute.repository/${REPO}"
```

### 5-3. Workload Identityプロバイダの名前を取得する。

```shell
export FULL_PROVIDER_NAME=`gcloud iam workload-identity-pools providers describe "${PROVIDER_NAME}" --project="${PROJECT_ID}" --location="global" --workload-identity-pool="${POOL_NAME}" --format="value(name)"`
```

### 5-4. Memorize provider name.

Memorize FULL provider name.

```shell
echo ${FULL_PROVIDER_NAME}
```

### 6-1. Logout Cloud-SDK auth

```shell
gcloud auth revoke
```

## Setup GitHub Actions

### Set secret variables.

workflowに使う変数は以下。

```shell
workload_identity_provider=${FULL_PROVIDER_NAME}
service_account=${SERVICE_ACCOUNT_NAME}@${PROJECT_ID}.iam.gserviceaccount.com
```

### Where is workflow file

The workflow file is [gcloudAuth.yaml](https://github.com/landmaster135/neptunus-note/tree/master/.github/workflows/gcloudAuth.yaml)

## Test with Docker

### Execute in the windows machine while the machine being booted by docker.

[Refer about "docker ps" and "docker cp" to this Markdown.](../README.md)
