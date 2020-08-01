# go-gcloud-functions-pubsub-tutorial
Simple gcloud functions with Golang.<br/>
https://cloud.google.com/sdk/docs/cheatsheet?hl=ja
<br/><br/>


#プロジェクト関連

プロジェクトの作成<br/>
`gcloud projects create [PROJECT_ID] `

`[--no-enable-cloud-apis] [--folder=FOLDER_ID] [--labels=[KEY=VALUE,…]] [--name=NAME] [--organization=ORGANIZATION_ID] [--set-as-default] [GCLOUD_WIDE_FLAG …]
`
<br/><br/>
作業するデフォルトのプロジェクト指定<br/>
`gcloud config set project [PROJECT_ID] `<br/>

プロジェクトの確認<br/>
`gcloud config get-value project`

サービス開始 (プロジェクトの確認後)<br/>
`gcloud services enable cloudfunctions.googleapis.com`


#Pub/Sub


トピック作成<br/>
`gcloud alpha pubsub topics create [TOPIC]`




#Cloud Functions

Deploy “Send” function - http trigger<br/>
`gcloud alpha functions deploy api --entry-point Send --runtime go111 --trigger-http --set-env-vars PROJECT_ID=gcloud-func-tutorial1234
`
<br/><br/>
Deploy “consumer” function  - pub/sub trigger<br/>
`gcloud alpha functions deploy consumer --entry-point Consume --runtime go111 --trigger-topic=randomNumbers
`
<br/><br/>
Catching function logs<br/>
`gcloud alpha functions logs read consumer`
