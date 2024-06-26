# ai_analysis_log_frontend
### ■ 概要
- 課題のフロントエンド。Lamda+API Gatewayで作成したモックAPIを叩いてレスポンスを取得し、バックエンドにPOSTリクエストとして送る。バックエンド側で登録した内容を、画面に表示する。
- 作成したプログラムは、S3+CloudFrontにデプロイし、独自ドメインアクセスができるようにした。
### ■ 動作の概要
1. テキストボックスに、『aaa/bbb/test.jpg』などの画像パスを入力して『取得』ボタンを押す。プログラムは、このときの日時を取得し、『request_timestamp』に値をセットする。
2. 拡張子が、『jpg』『jpeg』『gif』『png』のときは、モックサーバーがランダムで『class』と『confidence』の値を生成し、課題に記載の『リクエスト成功』のフォーマットでレスポンスを返す。
3. 拡張子が上記以外、またはそれ以外の適当な文字列だった場合は、モックサーバーは課題に記載の『リクエスト失敗』のフォーマットでレスポンスを返す。
4. プログラムは、上記の２，または３のレスポンスを受け取った日時を取得し、『response_timestamp』に値をセットする。
5. モックサーバーから受け取ったレスポンスから、Django側に送るリクエストの内容を作成し、POSTリクエストを送る。
6. Django側ではPOSTリクエストを受け取ったら、その内容を整形し、DBへ登録する。
7. DBへの登録処理が完了したら、画面に登録した内容を表示する。
### ■ URL
1. フロントURL：https://februar.org/index.html
### ■ フロントエンド・インフラ使用技術
1. React (18.2.0)
2. TypeScript (5.2.2)
3. Vite (5.2.0)
4. S3
5. CloudFront
6. Certificata Manager
