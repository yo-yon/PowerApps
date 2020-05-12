検温報告アプリについて
---
## 概要
Power Appsで作成したアプリから検温結果を報告することで自動的に発熱報告のピックアップと未検温者ピックアップがされ所定のTeamsチャネルに対象者が投稿され、さらに対象者へチャットが投稿される仕組みになっています。  
検温アプリ一式.zipをダウンロードして頂き、下記設定をして頂ければ使用できますのでご自由にお使いください。

## 作成した背景
今回、この検温報告アプリを作成した背景としては新型コロナウィルスの感染拡大を受け、4/1より会社で検温報告が義務付けされたことです。

会社ではYammerにて社内の情報共有をしており、当初はYammer上に保管したExcelファイルへ検温結果を入力するという予定でしたがPCを支給されていない社員に関してはスマホのアプリから直接Excelを編集することができず、またPCでも他の人の箇所に誤って記載するなど多くの問題点を抱えていました。

これらの問題点を解消すると同時により後々、カスタマイズしやすいようにPower Appsを用いてこのアプリを作成するに至りました。

# 検温報告アプリのインストール手順
## 1. Sharepointサイトの構築

### 1-1. Sharepointサイトの作成
検温報告データをためる為のサイトを構築します。

1. [Office365ホーム](https://www.office.com/)からSharepointを選択します。  
![1-1-1](https://user-images.githubusercontent.com/62197237/81519075-e970d300-937a-11ea-8989-4356e1f55a4a.JPG)

1. 「サイトの作成」を選択し、「次へ」をクリックします。  
![1-1-2](https://user-images.githubusercontent.com/62197237/81642378-3a0d2c80-945e-11ea-83ec-699d9ff47967.JPG)

1. 「チームサイト」を選択します。  
![1-1-3](https://user-images.githubusercontent.com/62197237/81642428-514c1a00-945e-11ea-804f-3bb60ab19fd4.JPG)

1. サイト名と説明を入力します。  
![1-1-4](https://user-images.githubusercontent.com/62197237/81642448-5f9a3600-945e-11ea-9423-df08ed6b648d.JPG)

1. プライバシー設定は全社員がアクセスできるように「パブリック」を選択します。  
![1-1-5](https://user-images.githubusercontent.com/62197237/81642466-6aed6180-945e-11ea-802c-5ca3aa85584d.JPG)

1. 「次へ」をクリックします。

1. 必要に応じてサイト所有者を追加します。  
![1-1-7](https://user-images.githubusercontent.com/62197237/81642510-82c4e580-945e-11ea-8c86-f4d1daaea7b6.JPG)

1. 「完了」をクリックします。

1. 作成されたサイトが開くのでWebブラウザのアドレス欄でURLをコピーして控えておきます。  
![1-1-9](https://user-images.githubusercontent.com/62197237/81642523-8fe1d480-945e-11ea-9a4f-df5d3e8e855c.JPG)

これでデータをためる為のサイトは作成できました。

次にアプリ用にSharePointのカスタムリストを作成します。

3種類のカスタムリストが必要となる為、カスタムリストの作成にはPower Automateフローを利用します

### 1-2. SharePointリスト作成用のPower Automateフローインポート

1. [Power Automate](https://flow.microsoft.com/)にアクセスします。

1. 「マイフロー」をクリックします。  
![1-2-2](https://user-images.githubusercontent.com/62197237/81643074-c835e280-945f-11ea-8fdf-ec64f6f21bf8.JPG)

1. 「インポート」をクリックします。  
![1-2-3](https://user-images.githubusercontent.com/62197237/81643127-e4d21a80-945f-11ea-9b1b-27f2d3c7f028.JPG)

1. 検温報告用リスト作成.zipをアップロードします  
![1-2-4](https://user-images.githubusercontent.com/62197237/81643150-f5829080-945f-11ea-9c69-49fff367c16a.JPG)

1. インポートしたフローに対して「インポート時に選択」をクリックしSharePointの接続を追加します。  
![1-2-5](https://user-images.githubusercontent.com/62197237/81643170-ffa48f00-945f-11ea-890c-c714326177bd.JPG)

1. もし既存のSharePoint接続が無い場合は、「+新規作成」をクリックし、接続を作成します。  
![1-2-6](https://user-images.githubusercontent.com/62197237/81643192-0c28e780-9460-11ea-85b3-1471e92a1542.JPG)

1. 別のタブが開くので「+新しい接続」をクリックします。  
![1-2-7](https://user-images.githubusercontent.com/62197237/81643220-18ad4000-9460-11ea-9759-793a7e2bc1e9.JPG)

1. 「SharePoint」と検索し、選択します。  
データを接続する方法は「直接接続(クラウドサービス)」を選択し、「作成」をクリックします。  
![1-2-8-1](https://user-images.githubusercontent.com/62197237/81643237-1fd44e00-9460-11ea-91b1-328a0bf7f29f.JPG)  
![1-2-8-2](https://user-images.githubusercontent.com/62197237/81643250-282c8900-9460-11ea-9aeb-7ab7b8731297.JPG)

1. 元のタブに戻って作成した接続を選択します。  
![1-2-9](https://user-images.githubusercontent.com/62197237/81643280-3aa6c280-9460-11ea-9daf-d6f6c80c152a.JPG)

1. 保存をクリックします。

1. インポートをクリックします。

### 1-3. SharePointリスト作成用のフローを編集

1. インポートが完了したら「マイフロー」へアクセスし、フローの一覧を更新します。

1. インポートした「検温報告用リスト作成」フローを選択します。  
![1-3-2](https://user-images.githubusercontent.com/62197237/81643305-48f4de80-9460-11ea-9e32-d58e7632b8ad.JPG)

1. 「編集」をクリックします。  
![1-3-3](https://user-images.githubusercontent.com/62197237/81643330-54e0a080-9460-11ea-8bb9-e928fba44689.JPG)

1. 「リストを作成するSharePointサイトの指定」をクリックします。  
![1-3-4](https://user-images.githubusercontent.com/62197237/81643340-5d38db80-9460-11ea-85ec-4277296db5e7.JPG)

1. 「値」を1-1で作成したSharePointサイトのURLに変更してください。  
![1-3-5](https://user-images.githubusercontent.com/62197237/81643359-675ada00-9460-11ea-947c-dc842e8539cf.JPG)

1. 「保存」をクリックします。  
![1-3-6](https://user-images.githubusercontent.com/62197237/81643381-72ae0580-9460-11ea-904f-20334b3ae86f.JPG)

### 1-4. 「検温報告用リスト作成」フローを実行する

1. 「検温報告用リスト作成」フローの詳細画面に戻ります。  
![1-4-1](https://user-images.githubusercontent.com/62197237/81643407-7c376d80-9460-11ea-8fa3-93725108da13.JPG)

1. 「実行」をクリックします  
![1-4-2](https://user-images.githubusercontent.com/62197237/81643439-8a858980-9460-11ea-9b0f-f4ba5a211f06.JPG)

1. 画面右側に「フローの実行」と表示されるのでクリックします

エラーが出なければリストの作成は完了です。

SharePointのサイトコンテンツを確認して頂ければ下記の3つのリストができているはずです。

| リスト名| 説明 |
----|----
| Employee_list | 社員リストです。所属している社員の情報を入力して下さい。 |
| Workprohibition_list | 出勤停止者リストです。37.5℃以上の発熱があった場合、自動的にこのリストに格納されます。 |
| BodyTempMeasurementResult_list |検温報告リストです。検温報告アプリで入力された内容が格納されます。 |

## 2. Employee_listへのデータ取り込み
検温報告アプリはEmployee_listに入力されている社員氏名や所属部署などの情報を使用します。
事前準備として必要情報Power Automateを使用してEmployee_listへ取り込みします。

### 2-1. 取り込み用データの作成

1. ダウンロードした「Employee_list取り込み用.xlsx」に必要情報を入力します。

1. 作成したSharePointサイトのドキュメントに「Employee_list取り込み用.xlsx」を格納します。

### 2-2. データの取り込み用

1. Excel Onlineで格納したデータを開きます。

1. 「挿入」タブの「Officeアドイン」をクリックします。  
![2-2-2](https://user-images.githubusercontent.com/62197237/81643505-ac7f0c00-9460-11ea-896f-a914f25c5681.JPG)

1. 「ストア」の検索欄で「Automate」検索し、表示された「Microsoft Flow for Excel(Preview)」を追加します。  
![2-2-3](https://user-images.githubusercontent.com/62197237/81643518-b6087400-9460-11ea-9a95-ae5d668eaa3c.JPG)

1. 別ウィンドウが表示されるので「続行」をクリックします。  
![2-2-4](https://user-images.githubusercontent.com/62197237/81643535-bef94580-9460-11ea-9944-e5e87fae6991.JPG)

1. 「データ」タブにアドインが追加されるのでクリックします。  
![2-2-5](https://user-images.githubusercontent.com/62197237/81643561-cc163480-9460-11ea-96a5-ecd5e4b84cbf.JPG)

1. 画面右側にFlowの画面が表示されるので「サインイン」をクリックします。  
![2-2-6](https://user-images.githubusercontent.com/62197237/81643575-d3d5d900-9460-11ea-968d-a886cb46c20a.JPG)

1. 「許可」をクリックします。  
![2-2-7](https://user-images.githubusercontent.com/62197237/81643588-d9332380-9460-11ea-9d7d-5900b6307786.JPG)

1. 「承諾」をクリックします。  
![2-2-8](https://user-images.githubusercontent.com/62197237/81643617-e4864f00-9460-11ea-86e4-4bffdc64f915.JPG)

1. 「選択した行の項目をSharePointで作成」を選択します。  
![2-2-9](https://user-images.githubusercontent.com/62197237/81643636-f0721100-9460-11ea-9edd-9784ab3f86ab.JPG)

1. 「続行」をクリックします。  
![2-2-10](https://user-images.githubusercontent.com/62197237/81643669-0253b400-9461-11ea-8159-981280305714.JPG)

1. 「選択した行」のテーブル欄で「Employeelist」を選択します。  
![2-2-11](https://user-images.githubusercontent.com/62197237/81656210-cbd26500-9471-11ea-84f5-c4fb0445ce0b.JPG)

1. 「Create item」の「サイトのアドレス」で作成したサイトのURLを選択します。  
![2-2-12](https://user-images.githubusercontent.com/62197237/81656311-e0166200-9471-11ea-8756-a6779695583d.JPG)

1. 「Create item」の「リスト名」で「Employee_list」を選択します。  
![2-2-13](https://user-images.githubusercontent.com/62197237/81656371-ee647e00-9471-11ea-9b4f-7d7362dfe9ba.JPG)

1. 各項目に適した列を選択します。(Formattedと書かれていない方を選択）  
![2-2-14](https://user-images.githubusercontent.com/62197237/81656410-f8867c80-9471-11ea-8c76-790da3382472.JPG)

1. 保存をクリックします。

1. 前の画面に戻り、取り込みしたい行を選択します。(行選択ではなくセルを選択)  
![2-2-16](https://user-images.githubusercontent.com/62197237/81656471-03411180-9472-11ea-8e55-41e99bf45aef.JPG)

1. 先ほど作成したフローの実行ボタンが有効化されるのでボタンをクリックします。
![2-2-17](https://user-images.githubusercontent.com/62197237/81656562-16ec7800-9472-11ea-94b9-4cebb4c2220b.JPG)

1. 「続行」をクリックします。(表示されなかったら次の手順へ)  
![2-2-18](https://user-images.githubusercontent.com/62197237/81656609-1fdd4980-9472-11ea-9e88-f10fd76da112.JPG)

1. 「フローの実行」をクリックします。  
![2-2-19](https://user-images.githubusercontent.com/62197237/81656645-279cee00-9472-11ea-8ec4-7f333dd5c7c8.JPG)

これでEmployee_listへのデータ取り込みは完了です。
サイトコンテンツを確認して頂くとEmployee_listのアイテム数が増えていることが確認できます。

## 3. 検温報告アプリのインポートと設定

1で検温報告アプリの結果をためておく箇所が作成されたので次にアプリのインポートを行い、使用する為の設定を行います。

### 3-1. 「検温報告」アプリのインポート

1. [Power Apps](https://make.powerapps.com/)にアクセスします。

1. 左側のメニューから「アプリ」を選択します。  
![3-1-2](https://user-images.githubusercontent.com/62197237/81657127-9a0dce00-9472-11ea-9080-bc9146ad7285.JPG)

1. コマンドバーに表示されている「キャンバスアプリのインポート」をクリックします。  
![3-1-3](https://user-images.githubusercontent.com/62197237/81657269-b4e04280-9472-11ea-835f-440bb6b61593.JPG)

1. 「アップロード」をクリックします。  
![3-1-4](https://user-images.githubusercontent.com/62197237/81659568-ca566c00-9474-11ea-949d-98ef341c9044.JPG)

1. ダウンロードした「検温報告アプリ」.zipを選択します。

1. 「関連リソース」でエラーになっている接続に対し、「インポート時に選択する」をクリックし、  
接続を選択します。接続が無い場合は新規で作成して下さい。  
![3-1-6](https://user-images.githubusercontent.com/62197237/81659986-346f1100-9475-11ea-8396-13a177e3437d.JPG)
   
1. 「インポート」を選択します。

### 3-2. 「検温報告」アプリのデータソース設定

1. 「アプリ」の一覧画面に戻ります。

1. 「検温報告」アプリを選択し編集をクリックします。  
![3-2-2](https://user-images.githubusercontent.com/62197237/81662972-4c489400-9479-11ea-8d8a-7b08580f7be1.JPG)

1. サインインするか、必要な接続を作成して、「許可」をクリックします。  
![3-2-3](https://user-images.githubusercontent.com/62197237/81663074-5f5b6400-9479-11ea-87da-d728e7a3ec60.JPG)

1. 左側のメニューでデータソースに移動します。  
![3-2-4](https://user-images.githubusercontent.com/62197237/81663178-726e3400-9479-11ea-99f9-af52966cd891.JPG)

1. この状態では1で作成したSharePointサイトを差していないのでアプリ内の既存のSharePointリストを削除します。  
マウスオーバーすると表示される「その他のコマンド(･･･)をクリックし、「削除」をクリックします。  
![3-2-5](https://user-images.githubusercontent.com/62197237/81663247-80bc5000-9479-11ea-99cd-0ff1536fff3b.JPG)

1. 検索欄で「SharePoint」と検索します。  
![3-2-6](https://user-images.githubusercontent.com/62197237/81663356-96ca1080-9479-11ea-8263-1562c124db5e.JPG)

1. 下部に「SharePoint」と表示されるのでそれをクリックします。  
![3-2-7](https://user-images.githubusercontent.com/62197237/81663582-c4af5500-9479-11ea-9765-eaa361199a23.JPG)

1. 表示されたメニューでSharePointをクリックします。  
![3-2-8](https://user-images.githubusercontent.com/62197237/81663835-f58f8a00-9479-11ea-86a9-73002478e3b0.JPG)

1. 画面右側に「SharePointサイトに接続」と表示されるのでSharePointサイトのURLを貼り付け、「接続」をクリックします。  
![3-2-9](https://user-images.githubusercontent.com/62197237/81669267-f1b33600-9480-11ea-8100-f90eb7c2eb07.JPG)

1. 「一覧の選択」と表示され、サイト内に格納されているリストやライブラリが表示されるので必要なリストを選択し、「接続」をクリックします。  
![3-2-10](https://user-images.githubusercontent.com/62197237/81669295-fd9ef800-9480-11ea-9033-bfef635bc3cd.JPG)

1. 「保存」をクリックし、「発行」をクリックすればアプリの設定が完了です。

## 4. 未検温者ピックアップ用のPower Automateフローインポートと設定変更

検温報告アプリで当日の検温報告をしていない社員をピックアップし所定のチャネルへ対象者のカードを投稿できます。
インポートした時点では正しいサイトを指定されていないので設定変更を行います。

### 4-1. 未検温者ピックアップのPower Automateフローインポート

1. [Power Automate](https://flow.microsoft.com/)にアクセスします。

1. 「マイフロー」をクリックします。  
![4-1-2](https://user-images.githubusercontent.com/62197237/81669331-08598d00-9481-11ea-92a5-0f39713bc35d.JPG)

1. 「インポート」をクリックします。  
![4-1-3](https://user-images.githubusercontent.com/62197237/81669353-10193180-9481-11ea-80d1-a14d86e8e54e.JPG)

1. 未検温者ピックアップ.zipをアップロードします。  
![4-1-4](https://user-images.githubusercontent.com/62197237/81669366-17403f80-9481-11ea-875f-4d6cbd626dca.JPG)

1. インポートしたフローに対して「インポート時に選択」をクリックし接続を追加します。  
![4-1-5](https://user-images.githubusercontent.com/62197237/81669403-22936b00-9481-11ea-962c-95caf591dcdd.JPG)

1. 保存をクリックします。

1. インポートをクリックします。

### 4-2. 未検温者ピックアップのフローを編集

1. インポートが完了したら「マイフロー」へアクセスし、フローの一覧を更新します。

1. インポートした「未検温者ピックアップ」フローを選択します。  
![4-2-2](https://user-images.githubusercontent.com/62197237/81669425-2cb56980-9481-11ea-8498-4ec4a739c2d0.JPG)

1. 「編集」をクリックします。  
![4-2-3](https://user-images.githubusercontent.com/62197237/81669449-36d76800-9481-11ea-94c5-7bcbc2351ad0.JPG)

1. 「複数項目の取得」をクリックします。  
![4-2-4](https://user-images.githubusercontent.com/62197237/81669473-3e970c80-9481-11ea-9b2c-018017944c07.JPG)

1.  ｢サイトのアドレス」を1-1で作成したSharePointサイトのURLに変更してください。  
![4-2-5](https://user-images.githubusercontent.com/62197237/81669494-45be1a80-9481-11ea-8a7b-982eeeb92189.JPG)

1.  ｢リスト名」を「Employee_list」に変更してください。  
![4-2-6](https://user-images.githubusercontent.com/62197237/81669528-5078af80-9481-11ea-9fb7-7bfe9b4444f0.JPG)

1. 「保存」をクリックします。

これですべての設定が完了です。
後はPower Appsから検温報告アプリを展開して使用して下さい。
