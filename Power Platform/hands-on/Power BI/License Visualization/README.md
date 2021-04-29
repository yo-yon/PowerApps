<h1>ライセンスの見える化-Power BIレポート作成</h1>
<h2>初めに</h2>
<p>これは2021/3/27に開催されたOffice365勉強会で登壇した内容のPower BI部分にフォーカスした内容です。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116347928-1803ea00-a828-11eb-9233-91bf984f4ab9.png" width="500px" />
</p>

<h2>Power BIデスクトップをインストール</h2>
<p>まず、準備としてPower BIデスクトップをインストールしましょう。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116348112-6fa25580-a828-11eb-9994-eaaad69af905.png" width="500px" />
</p>

<ol>
  <li>Microsoftストアを開きます。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116348883-d8d69880-a829-11eb-9e7e-ae2b28b9b305.png" /><br /><br />
  </li>
  <li>検索欄で「Power BI」と検索します。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116348985-03c0ec80-a82a-11eb-82de-d400c5d79f3b.png" /><br /><br />
  </li>
  <li>Power BI Desktopをクリックします。<br />
     <img src="https://user-images.githubusercontent.com/62197237/116349221-821d8e80-a82a-11eb-84c4-664411bf587b.png" /><br /><br />
  </li>
  <li>右上にダウンロードもしくはインストールと出ているのでクリックします。<br />
     <img src="https://user-images.githubusercontent.com/62197237/116349289-9e213000-a82a-11eb-89ba-3e0bb32946fa.png" width="500px" /><br /><br />
  </li>
  <li>インストールが終わったらこのような表示に変わります。<br />
     <img src="https://user-images.githubusercontent.com/62197237/116349323-b2652d00-a82a-11eb-8d6f-d33b48df15d5.png" width="500px" /><br /><br />
  </li>
</ol>

<h2>SharePointリストの作成</h2>
<p>本ディレクトリに今回の演習で使用するリストをまとめたデータを格納しています。(リスト関連.xlsx)<br /> 
 まずはそれをダウンロードして下さい。
</p>

<ol>
  <li>SharePointを開き、リストを追加したいサイトを開きます。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116353195-4df99c00-a831-11eb-92fe-014b5d0c232e.png"  width="500px" /><br /><br />
  </li>
  <li>新規をクリックし、リストをクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116353178-489c5180-a831-11eb-8648-19de3523d090.png"  width="500px" /><br /><br />
  </li>
  <li>Excelからをクリックします。<br />
   <img src="https://user-images.githubusercontent.com/62197237/116353207-50f48c80-a831-11eb-9fe6-b6076a2dd575.png" width="500px" /><br /><br />
  </li>
  <li>ファイルをアップロードをクリックし、最初にダウンロードしたデータを選択します。<br />
   <img src="https://user-images.githubusercontent.com/62197237/116353213-5225b980-a831-11eb-80aa-cd1e03d2f9cb.png" width="500px" /><br /><br />
  </li>
  <li>エクセルデータのテーブルを読み込みます。(テーブルは計4つ(ELIST、MLIST、OMLIST、LLIST))<br />
   <img src="https://user-images.githubusercontent.com/62197237/116353215-5356e680-a831-11eb-891f-c94b77d94838.png" width="500px" /><br />
   【注意ポイント】<br /> EmployeeNoなどのように「0」始まりの数字のみの値の場合、自動的に「数値」として変換されてしまいます。<br />
   「0」始まりの状態を保持したい際は必ず「1行テキスト」に変換するようにしましょう。<br /><br />
  </li>
  <li>リストの名前をテーブル名と同じものにして作成をクリックします。<br />
   <img src="https://user-images.githubusercontent.com/62197237/116353218-5520aa00-a831-11eb-9f5f-7088ca7967b3.png" width="500px" /><br /><br />
  </li>
</ol>
<p>上記2～6をテーブルの数の分だけ繰り返してください。</p>
<br /><br />
<h2>Power BI Desktopでデータセットに接続してみよう。</h2>
<p>取り込んだリストをデータベースとして、Power BI Desktopから接続します。</p>

<ol>
  <li>「データを取得」から「詳細」をクリックします。<br />
   <img src="https://user-images.githubusercontent.com/62197237/116361167-a2a21480-a83b-11eb-8555-dd2d62ed5013.png" /><br /><br />
   因みにPower BI Desktopを立ち上げた際に表示されるオレンジ色のウィンドウで「データを取得」をクリックしても同じように2の画面が表示されるのでお好みで実施してください。<br />
   <img src="https://user-images.githubusercontent.com/62197237/116491859-d3368c80-a8d5-11eb-9274-58ceabb1de81.png" width="500px" /><br /><br />
  </li>
  <li>検索欄で「SharePont」と入力し「SharePoint Online リスト」をクリックし、「接続」をクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493392-9d93a280-a8d9-11eb-931d-f7260b8ae142.png" width="500px" /><br /><br />
  </li>
  <li>サイトURLに先ほどリストを作成したSharePointサイトのホームをクリックしURL欄に表示されたURLをコピー、Power BIで表示されているウィンドウのサイトURL欄に貼り付け、「OK」をクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116492945-91f3ac00-a8d8-11eb-824e-aff52f96820e.png" width="500px" /><br/><br />
    因みに実装の部分で「2.0(ベータ)」を選択するとSharePointリストで「既定のビュー」に定義された列のみを取得することが可能になります。<br /> 
    ですのであらかじめ、SharePointリストの既定のビューで今回のPower BIで集計に使う列のみの表示にしておくことで後程、Power Query画面での作業工数の低減につながります。ただしPower Query画面での操作も説明をする為、今回は「1.0」を使用します。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116492970-a172f500-a8d8-11eb-84f7-e11cf7a76bd4.png" width="500px" /><br/>
    <a href="https://docs.microsoft.com/ja-jp/power-query/connectors/sharepointonlinelist">Sharepoint Online リスト v2.0 (ベータ版) に接続する(Microsoft Docs)<br /><br /></a>
  </li>
  <li>SharePointリストに接続する為の認証方法の選択画面が表示されます。<br /> 
    基本的には「Microsoftアカウント」を使用します。<br /> 
    「Microsoftアカウント」をクリックし、「サインイン」をクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493077-e72fbd80-a8d8-11eb-8d31-1a06b3067e3c.png" width="500px" /><br /><br />
  </li>
  <li>サインインする為のアカウントを選択します。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493499-d92e6c80-a8d9-11eb-97ca-70e537fd9c8a.png" /><br /><br />
  </li>
  <li>パスワードを入力し「サインイン」をクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493562-f82cfe80-a8d9-11eb-86ce-9dbc30250bc9.png" /><br /><br />
  </li>
  <li>画面が変わるので「接続」をクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493614-0a0ea180-a8da-11eb-8eed-94c8ea35d893.png" width="500px" /><br /><br />
    【補足事項1】<br /> 
    認証の種類は「匿名」「Windows」「Microsoftアカウント」の3つあります。<br /> 
    匿名は文字通り匿名でのアクセスとなります。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493671-29a5ca00-a8da-11eb-9a21-bb630bd9d0ca.png" width="500px" /><br />
    Windowsは現在ログインしているWindowsの資格情報を使用、もしくは代替の資格情報を使用してアクセスする形になります。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493750-56f27800-a8da-11eb-9bbd-db99c39936ae.png" width="500px" /><br />
    上記でも案内した通り、基本的にはMicrosoftアカウントを利用していただければ問題ありません。<br /><br /> 
    【補足情報2】<br /> 
    認証を適用する対象レベルの変更も可能です。<br /> 
    下図のように「これらの設定の適用対象レベルの選択」をクリックするとサイトの階層URLが表示され、<br /> 
    いずれかを選択することで、ここで設定する認証がどの階層のレベルに割り当てるか指定できます。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493795-6ec9fc00-a8da-11eb-856b-c5d59b936f29.png" width="500px" /><br />
    これは上位の階層に対して特定の認証方法を設定したくない場合に使用します。<br /> 
    詳細はこちらのDocsを参照していただければと思います。<br />
    <a href="https://docs.microsoft.com/ja-jp/power-query/connectors/sharepointonlinelist">SharePoint Online リストに接続する<br /><br /></a>
  </li>
  <li>先ほど追加したリストにチェックを入れ「データの変換」をクリックします。<br />
    <img src="https://user-images.githubusercontent.com/62197237/116493829-7be6eb00-a8da-11eb-9e54-ce094c593098.png" width="500px" /><br /><br />
  </li>
</ol>

<h2>Power Queryを使ってデータを成型してみよう。</h2>
<p>取り込んだデータから不要な列などを削除していきます。 Power BIで視覚化する場合、この作業が非常に重要になります。</p>

<h3>ELIST</h3>
<p>まずはELISTから成型します。 このリストはライセンス集計に使用します。</p>
<ol>
 <li>EmployeeNo、EDisplayName、Department、Office、LicenseA～O列を選択し、「ホーム」タブ、「列の削除」で「他の列を削除」をクリックします。 尚、注意点として列を選択する際に基本的にCtrlキーを押しながら選択していきますが列をあけて連続選択する場合(A列を選択後、C~F列を選択するなど)、連続選択列に対してShiftキーを押して選択すると、最初にCtrlキーを押して選択した列が解除されてしまいます。 この場合は連続選択する起点となる列をCtrlキーを押しながら選択したのち、Ctrlキー+Shiftキーを押しながら最終選択列をクリックすると最初に単体で選択した列が解除されず選択状態になったままになります。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116542845-1b7e9a80-a928-11eb-8170-6008b83a9a5c.png" width="500px" /><br /><br />
 </li>
 <li>LicenseA～O列を選択し、変換タブから「値の置換」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116542875-23d6d580-a928-11eb-84f3-9eeeb5a2fb33.png" width="500px" /><br /><br />
 </li>
 <li>検索する値を「null」、置換後を"-"にして「OK」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116542904-2c2f1080-a928-11eb-857f-5ac24eb23013.png" width="500px" /><br /><br />
 </li>
 <li>LicenseB列を選択し、変換タブから「値の置換」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116542934-34874b80-a928-11eb-94eb-9650f3cc48be.png" width="500px" /><br /><br />
 </li>
 <li>検索する値を「○」、置換後を「LicenseB」にして「OK」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543065-5da7dc00-a928-11eb-81ba-f68620a92dd5.png" width="500px" /><br /><br />
 </li>
 <li>4、5をLicenseC列からO列まで実施します。置換後の値はそれぞれの列名にして下さい。<br /><br /></li>
 <li>カスタム列を追加し、LicenseA～O列をカンマ区切りで結合します。(列名をライセンス結合とする)<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543108-6ac4cb00-a928-11eb-8c94-48019b2f658a.png" width="500px" /><br />
  <img src="https://user-images.githubusercontent.com/62197237/116543143-757f6000-a928-11eb-859d-280871d5da4c.png" width="500px" /><br /><br />
 </li>
 <li>LicenseA～O列は不要となりますので削除してしまいましょう。<br /><br /></li>
 <li>先ほど作成したカスタム列「ライセンス結合」を選択し、変換タブの列の分割をクリックし「区切り記号による列の分割」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543208-9051d480-a928-11eb-8250-57371458b2e3.png" width="500px" /><br /><br />
 </li>
 <li>詳細オプションをクリックし分割方向を「行」にして「OK」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543316-afe8fd00-a928-11eb-8c8e-f901bd106f81.png" width="500px" /><br />
   もともとEmployeeNoを一意のキーとしてライセンスを横並び(列)で表示していましたがこの処理をすることでEmployeeNoに対し、どのライセンスが割り当たっているかを行単位に変換することができました。<br /><br />
 </li>
 <li> LLISTより集計に必要な情報を持ってくるため、ELISTとLLISTを「ホーム」タブの「クエリをマージ」を使って結合します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543339-b8d9ce80-a928-11eb-90b5-7ebb70799d58.png" width="500px" /><br /><br />
 </li>
 <li>ELIST ライセンス結合列-LLIST Licemse列をリレーション、結合の種類は「内部(一致する行のみ)」を選択。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543565-fb031000-a928-11eb-9954-91c88dfe8228.png" width="500px" /><br />
  ※補足情報<br />左
  結合の種類によって返ってくる結果は変わってきます。<br />
  左外部：マージ画面上部に表示されているテーブルのすべてを残したうえで下部のテーブルは一致したもののみのデータを返す。<br />
  右外部：マージ画面上部に表示されているテーブルから下部のテーブルと一致したもの+下部のテーブルのすべてのデータを返す。<br />
  完全外部：マージ画面上部に表示されているテーブル、下部のテーブルすべてのデータを返す。<br />
  内部：マージ画面上部に表示されているテーブルから下部のテーブルと一致したもののみのデータを返す。<br />
  左反：マージ画面上部に表示されているテーブルで下部のテーブルと一致しないもののみのデータを返す。<br />
  右反：マージ画面下部に表示されているテーブルで上部のテーブルと一致しないもののみのデータを返す。<br /><br />
 </li>
 <li>追加されたLLIST列の矢印マークをクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543606-05bda500-a929-11eb-98ac-1d51ca0eb1e4.png" width="500px" /><br /><br />
 </li>
 <li>SystemName、Value、Price、NoofLicensesにチェックを入れ「元の列名を...」のチェックを外し、OKをクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543697-238b0a00-a929-11eb-8966-cf037cb72687.png" width="500px" /><br />
  ※Value、Price、NoofLicenses列の型が文字列になっている場合は列を選択し、右クリック、メニューから「型の変更」をクリックし「整数」を選択します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543759-3e5d7e80-a929-11eb-96ea-b363c798d733.png" width="500px" /><br /><br />
 </li>
 <li>カスタム列の追加でPrice列とValue列の差を求めます。(列名をCRとする)<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543813-4ddcc780-a929-11eb-906a-13eb89b40ceb.png" width="500px" /><br /><br />
 </li>
 <li>14で作成したカスタム列の型を10進数に変更します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116543851-57fec600-a929-11eb-810d-a6ab17f45045.png" width="500px" /><br /><br />
 </li>
</ol>

<h3>LLIST</h3>
<p>次はLLISTを成型します。 <br />このリストはライセンス残数の計算に利用します。</p>
<ol>
 <li>SystemName、License、Value、Price、Vendor、Uses、NoofLicenses列を選択し、「ホーム」タブ、「列の削除」で「他の列を削除」をクリックします。 <br />
  <img src="https://user-images.githubusercontent.com/62197237/116544640-5da8db80-a92a-11eb-9f89-f59d031dead9.png" width="500px" /><br />
  ※Value、Price、NoofLicenses列の型が文字列になっている場合は列を選択し、右クリック、メニューから「型の変更」をクリックし「整数」を選択します。<br /><br />
 </li>
 <li>カスタム列の追加でコスト合計を求めます。(列名をCostSUMとする)<br />
  <img src="https://user-images.githubusercontent.com/62197237/116544664-65688000-a92a-11eb-9065-f4dc2a5cc831.png" width="500px" /><br /><br />
 </li>
 <li>2で作成したカスタム列を選択し、型の変更で10進数に変更します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116544689-6dc0bb00-a92a-11eb-95a6-540a90c5322f.png" width="500px" /><br /><br />
 </li>
</ol>

<h3>OMLIST</h3>
<p>次にOMLISTを成型します。</p>
<ol>
 <li>Title、Models、Career、User、Dep、Office、Tethering、Cflag、SpareFlag列を選択し、「ホーム」タブ、「列の削除」で「他の列を削除」をクリックします。 <br />
  <img src="https://user-images.githubusercontent.com/62197237/116544925-b5474700-a92a-11eb-96bf-33c1b48dc6b4.png" width="500px" /><br /><br />
 </li>
 <li>OMLISTとMLISTを「クエリをマージ」を使って結合します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116544950-bd9f8200-a92a-11eb-9f39-bcc96efcbcf6.png" width="500px" /><br /><br />
 </li>
 <li>OMLIST Cflag列-MLIST Title列をリレーション、結合の種類は内部。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116544970-c55f2680-a92a-11eb-8b18-75d20467fac9.png" width="500px" /><br /><br />
 </li>
 <li>追加されたMLIST列の矢印マークをクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116544995-cee88e80-a92a-11eb-98e0-bbf654eaa225.png" width="500px" /><br /><br />
 </li>
 <li>Valueにチェックを入れ「元の列名を...」のチェックを外し、OKをクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116545038-de67d780-a92a-11eb-9fc0-cc97eb246935.png" width="500px" /><br />
  ※Value列の型が文字列になっている場合は列を選択し、右クリック、メニューから「型の変更」をクリックし「整数」を選択します。<br /><br /> 
 </li>
</ol>
ここまで処理が終わったら最後に「閉じて適用」をクリックします。<br />
<img src="https://user-images.githubusercontent.com/62197237/116545152-09522b80-a92b-11eb-9caa-6c1897379bd8.png" width="500px" /><br /><br />

<h2>リレーションを設定しよう</h2>
<p>取り込んだデータ間でーリレーションの設定をします。<br /> また不要なデータについては非表示しましょう。</p>

<h3>ELISTとLLISTのリレーション</h3>
<p>レポート画面で複数のデータにまたがったレポートを作成する場合、データ同士でリレーションを組むことでお互いのデータに作用するように設定ができます。 <br />
 今回はELIST SystemNameとLLIST SystemNameでリレーションが必要となります。 <br />
 ただし基本的にデータソース間で同一の列タイトルのものはリレーション対象として前段でPower Queryの実行をした際に自動的にリレーションされます。 <br />
 下記はリレーションが張られていなかった場合を想定しリレーションを組む方法について案内します。
</p>

<ol>
 <li>Power BI Desktop画面右側の一番下のアイコンをクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116546977-415a6e00-a92d-11eb-902e-77f0cddf53ee.png" /><br /><br />
 </li>
 <li>ELISTのSystemNameをLLIST SystemNameにドラッグ&amp;ドロップします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116547014-4a4b3f80-a92d-11eb-9a14-f2901ad79f34.png" width="500px" /><br /><br />
 </li>
 <li>データ間に矢印が表示されるので右クリック、プロパティをクリックし、下図の通りになっているか確認します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116547040-53d4a780-a92d-11eb-9994-9a5d7bd74b31.png" width="500px" /><br /><br />
 </li>
</ol>

<h3>データの非表示設定</h3>
<p>レポートを作成する際に不要なデータ列が表示されていると作成しにくいので事前に使わないとわかっているものは非表示設定にしておくことをお勧めします。<br />
 データごと非表示にする場合はデータソース名横に表示されている目のアイコンをクリックするとデータソースごと非表示にできます。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116547075-60590000-a92d-11eb-87cb-5acad6742495.png" width="500px" /><br /><br />
</p>

<h2>レポートを作成しよう</h2>
<p>では下準備は完成したのでレポートを作成しましょう。<br />
 レポートの作り方はあくまで自分の好みなので必ずしもこうしなければならないというものはありません。<br />
 今回は勉強会で発表したものを題材に作成をしていきます。
</p>

<h3>拠点別、部署別のライセンスコスト、使用数(マトリクス)</h3>
<img src="https://user-images.githubusercontent.com/62197237/116547772-49ff7400-a92e-11eb-9fca-bd2bef2a39ce.png" width="500px" /><br />
<p>このマトリクスにはELISTのデータを使用します。<br />
 行：SystemName<br />
 列：Office <br />
 ：Department<br />
 値：Value 　<br />
 ：CR 　<br />
 ：NoofLicensesのカウント<br />
 ※NoofLicensesをカウントにするには下記の手順でできます。
<ol>
 <li>フィールドの矢印をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116547783-4c61ce00-a92e-11eb-9ae1-c60f395f7c8b.png" width="500px" /><br /><br />
 </li>
 <li>「カウント」をクリックします。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116547788-4ec42800-a92e-11eb-9dd4-67e5cb034376.png" /><br /><br />
 </li>
</ol>
</p>

<p>列にOfficeとDepartmentを入れることによってドリルダウンで切り替えができます。<br />
 上記の形でそれぞれのフィールドを入れると下図のような感じになります。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116547818-55529f80-a92e-11eb-8c91-28844e2c386b.png" width="500px" /><br /><br />
 上記の完成形のデータと比較すると下記のようなことが異なっていると思います。<br />
<ul>
 <li> ValueとCRが円表記になっておらず、小数点第2位まで表示されている(数値の書式が違っている)</li>
 <li> フィールドのタイトルが違う</li>
 <li> タイトルがない</li>
 <li> 罫線がない</li>
</ul>
</p>

<p>これらの設定方法についてご案内します。</p>

<h3>数値の書式変更</h3>
<p>数値の書式を変更することでマトリクスの中に表示されている数値の見え方が変わります。<br />
 設定変更の方法は下記の通りです。
</p>

<ol>
 <li>フィールドで書式を変更したいものを選択します。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116548700-97301580-a92f-11eb-95d6-2a764dfa7207.png" /><br /><br />
 </li>
 <li>画面上部のメニューに「列ツール」というタブが表示されるので、その中から$アイコンの横にある矢印をクリック、通貨記号が表示されるのでその中から円マークを選択します。<br /> 
  書式が通貨型になり自動的に小数点以下が表示されなくなります。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116548756-a7e08b80-a92f-11eb-9bdf-ddb4e91efae9.png" width="500px" /><br /><br />
 </li>
 <li>通貨型以外の数値の小数点以下の表記を無くしたい場合は下図の「自動」の部分を「0」にすることで少数点以下無しの表記になります。<br />
  <img src="https://user-images.githubusercontent.com/62197237/116548794-b29b2080-a92f-11eb-8c8f-ba40aff88bf0.png" width="500px" /><br /><br />
 </li>
</ol>

<h3>フィールドのタイトル変更</h3>
<p>マトリクスを選択した状態でフィールドの部分でタイトル部分をダブルクリックをすると名称変更が可能です。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116548842-c0e93c80-a92f-11eb-91bd-4f5b8a991072.png" /><br /><br />
</p>

<h3>タイトルの追加</h3>
<p>タイトルに関しては「書式」で変更ができます。 タイトルをオンにし、タイトルテキストを入力するとタイトルをつけることができます。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116548901-d0688580-a92f-11eb-807a-c1708dc4eb40.png" /><br />
 <img src="https://user-images.githubusercontent.com/62197237/116548978-e6764600-a92f-11eb-9617-31f90a35449c.png" /><br /><br />
</p>

<h3>罫線の追加</h3>
<p>罫線に関しては「書式」で変更ができます。 罫線をオンにするとマトリクスに罫線をつけることができます。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116549023-f4c46200-a92f-11eb-9914-a2b91e9bbe00.png" /><br />
</p>

<h3>各種ライセンス月額コスト(マトリクス)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549304-453bbf80-a930-11eb-9a7b-97edc507784d.png" width="500px" /><br />
 このマトリクスにはLLISTのデータを使用します。<br />
 行：SystemName<br />
 値：CostSUM
</p>

<h3>各種ライセンス残数(マトリクス)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549352-51278180-a930-11eb-834d-115aaa8160ee.png" width="500px" /><br />
 このマトリクスにはELISTとLLISTのデータ、また残数を算出する為にメジャーを使用します。<br />
 行：SystemName(LLIST)<br />
 値：SystemNameのカウント(ELIST) 　<br />
 ：新しいメジャー(下記参照) <br />
 新しいメジャーというのは取り込んだデータを基に新たな集計結果を算出する為の定義です。<br />
 わかりやすく言えば集計されたデータ列を追加する感じです。<br />
 今回は保有しているライセンス数(LLIST NoofLicenses列)から使用済ライセンス数(ELIST SystemNameのカウント)を引き算するのでメジャーに入れる数式は下記になります。<br />
 メジャー = SUM(LLIST[NoofLicenses])-COUNTA(ELIST[SystemName])
</p>

<h3>拠点別、部署別のシステムコスト(積上棒グラフ)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549393-60a6ca80-a930-11eb-87d7-d5f7f808e3a3.png" width="500px" /><br />
 このグラフにはELISTのデータを使用します。<br />
 軸：Office 　<br />
 ：Department <br />
 凡例：SystemName<br />
 値：Value<br />
 軸にOfficeとDepartmentを入れることによってドリルダウンで切り替えができます。
</p>

<h3>導入システムのコスト割合(円グラフ)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549426-6d2b2300-a930-11eb-88e9-b4ac00df4e63.png" width="500px" /><br />
 このグラフにはELISTのデータを使用します。 <br />
 凡例：SystemName<br />
 値：Value
</p>

<h3>携帯総台数(カード)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549458-787e4e80-a930-11eb-981f-6ac321c56560.png" /><br />
 このカードにはOMLISTのデータを使用します。<br />
 フィールド：Titleのカウント
</p>

<h3>予備機台数(カード)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549493-83d17a00-a930-11eb-867d-af6553137a5f.png" /><br />
 このカードにはOMLISTのデータを使用します。<br />
 またSpareFlag列の○の数のみをカウントする必要がある為、ここでもメジャーを使用します。<br />
 フィールド：新しいメジャー<br />
 携帯の総台数を見るとTitleのカウントで算出しているのがわかると思います。<br />
 ですので考え方としてはSpareFlagに〇が入力されているTitle列をカウントする形になります。<br />
 つまり数式は下記のような感じになります。<br />
 予備機 = CALCULATE(COUNTA(OMLIST[Title]),OMLIST[SpareFlag] IN {​​​​​​​ "○" }​​​​​​​)
</p>

<h3>携帯月額コスト(カード)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549532-90ee6900-a930-11eb-8f7d-fe8e9811bbf2.png" /><br />
 このカードにはOMLISTのデータを使用します。<br />
 フィールド：Value
</p>

<h3>拠点別・部署別携帯コスト(折れ線グラフ+積上棒グラフ)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549608-a9f71a00-a930-11eb-9f6f-a5ba599de347.png" width="500px" /><br />
 このカードにはOMLISTのデータを使用します。<br />
 共有の軸：Office 　 　　<br />
 ：Dep<br />縦棒：Career<br />
 各棒の値：Value<br />
 線の値：Titleのカウント
</p>

<h3>キャリア別コスト(マトリクス)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549734-d0b55080-a930-11eb-9bb6-49d5954fcac9.png" width="500px" /><br />
 このマトリクスにはOMLISTのデータを使用します。<br />
 行：Career<br />
 列：Office 　<br />
 ：Department<br />
 値：Value<br />
 列にOfficeとDepartmentを入れることによってドリルダウンで切り替えができます。
</p>

<h3>拠点別・部署別携帯保有数(マトリクス)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549757-d9a62200-a930-11eb-9109-38da60cad35b.png" width="500px" /><br />
 このマトリクスにはOMLISTのデータを使用します。<br />
 行：Model<br />
 列：Office 　<br />
 ：Department<br />
 値：Value<br />
 列にOfficeとDepartmentを入れることによってドリルダウンで切り替えができます。
</p>

<h3>拠点別・部署別テザリングオプション導入数(マトリクス)</h3>
<p><img src="https://user-images.githubusercontent.com/62197237/116549794-e591e400-a930-11eb-8cd4-c481c467e468.png" width="500px" /><br />
 このマトリクスにはOMLISTのデータを使用します。<br />
 行：Model<br />
 列：Office 　<br />
 ：Department<br />
 値：Tethering <br />
 列にOfficeとDepartmentを入れることによってドリルダウンで切り替えができます。<br />
</p>
<p>あとは体裁を整えればレポート完成です。</p>

<h2>レポートの発行</h2>
<p>レポートの設定が完了しましたがまだこの時点ではクラウド上のPower BIにレポートが発行されていません。<br />
 画面上部からレポートの発行をしましょう。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116552179-b761d380-a933-11eb-8900-26a71656c809.png" /><br />
 <img src="https://user-images.githubusercontent.com/62197237/116552187-b9c42d80-a933-11eb-997b-99bb96b20139.png" width="500px" /><br /><br />
</p>

<h2>データセットを自動更新しよう</h2>
<p>クラウド上にレポートをアップするところまでは完了しましたが最後にデータセットの自動更新設定が必要です。<br />
 レポートの発行でアップしたワークスペースを開き、更新のスケジュール設定アイコンをクリックします。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116552414-f2fc9d80-a933-11eb-99ad-0c718191f84d.png" width="500px" /><br />
 更新頻度や時刻などを設定し、適用をクリックすれば設定完了です。<br />
 <img src="https://user-images.githubusercontent.com/62197237/116552474-04de4080-a934-11eb-805a-014ee00cef94.png" width="500px" /><br /><br />
</p>

<h2>作成後の注意</h2>
<p>Power BIにはレポートをWeb公開する設定があります。<br />
 これは外部への一般公開のことです。<br />
 Power BIでは会社のクリティカルな情報を扱うことが多くなるかと思いますので、間違って一般公開をしてしまわないよう 十分注意をして下さい。<br />
 Power BIのWeb公開と抑止についてわかりやすくまとめた記事がありますので参考にして下さい。<br />
 <a href="https://qiita.com/ishiayaya/items/faddbe227cea8df674b2">Power BIのWeb公開と抑止 - Qiita<br /><br /></a>
</p>
