# Mobile Top10  2016 - Top 10

<table>
  <tr>
    <th>リスク</th>
    <th>解説</th>
  </tr>
  <tr>
    <td width="35%"><a href="0xm1-M1-Improper%20Platform%20Usage.md">M1:不適切なプラットフォームの利用</a></td>
    <td width="65%">本カテゴリは、プラットフォーム機能の誤用や、プラットフォームセキュリティコントロールの不使用が対象です。Androidインテント、プラットフォームのアクセス許可、TouchIDの誤用、キーチェーン、モバイルOSの一部である他のセキュリティコントロールが含まれます。モバイルアプリケーションには、本リスクを有してしまう幾つかの状況があります。</td>
  </tr>
  <tr>
    <td><a href="0xm2-M2-Insecure%20Data%20Storage.md">M2:安全でないデータストレージ</a></td>
    <td>本カテゴリは、OWASP Mobile Top10 2014のM2(Insecure Data Storage：安全でないデータストレージ)とM4(Unintended Data Leakage：意図しないデータ漏えい)を組み合わせた新たなカテゴリです。</td>
  </tr>
  <tr>
    <td><a href="0xm3-M3-Insecure%20Communication.md">M3:安全でない通信</a></td>
    <td>本カテゴリは、脆弱なハンドシェイク、不適切なSSLバージョン、脆弱なネゴシエーション、機密情報の平文通信などが対象です。</td>
  </tr>
  <tr>
    <td><a href="0xm4-M4-Insecure%20Authentication.md">M4:安全でない認証</a></td>
    <td>本カテゴリは、エンドユーザの認証やセッション管理の不備が対象です。以下のようなものがあります。<br> - ユーザを特定できない<br> - ユーザの同一性を維持できない<br> - セッション管理の不備</td>
  </tr>
  <tr>
    <td><a href="0xm5-M5-Insufficient%20Cryptography.md">M5:不十分な暗号化</a></td>
    <td>機密情報資産を暗号化するプログラムには、暗号処理が不十分な場合があります。TLSやSSLに関連するあらゆるものは、M3(Insecure Communication：安全でない通信)に含まれるという点に注意してください。また、暗号化すべき時にアプリが暗号を使用しない場合は、M2(Insecure Data Storage：安全でないデータストレージ)に含まれます。本カテゴリは、暗号化が実行されたにもかかわらず、正しく行われていないという問題が対象です。</td>
  </tr>
  <tr>
    <td><a href="0xm6-M6-Insecure%20Authorization.md">M6:安全でない認可制御</a></td>
    <td>本カテゴリは、認可制御の不備(例えば、クライアント側での認可決定や強制ブラウジングなど)が対象です。これは、認証の問題(例えば、デバイス登録やユーザ識別)とは異なるものです。もし、認証が必要な状況でアプリがユーザを全く認証していない場合は (例えば、認証され許可されたアクセスが必要であるにもかかわらず、一部のリソースやサービスに匿名アクセスが許可されているなど)、認証の不備(M4)であり、本カテゴリには含まれません。</td>
  </tr>
  <tr>
    <td><a href="0xm7-M7-Poor%20Code%20Quality.md">M7:クライアントコードの品質</a></td>
    <td>本カテゴリは、以前は下位の「Security Decisions Via Untrusted Inputs：信頼できない入力値によるセキュリティ権限の判定」でした。本カテゴリは、モバイルクライアントのコードレベルの実装の問題が対象です。サーバサイドのコーディングミスとは異なるものです。本カテゴリは、バッファオーバーフローやフォーマットストリングの脆弱性や、他の様々なコードレベルのミスといったモバイルデバイス上で実行されるコードを書き換えることで解決できることが対象です。</td>
  </tr>
  <tr>
    <td><a href="0xm8-M8-Code%20Tampering.md">M8:コード改ざん</a></td>
    <td>本カテゴリでは、バイナリ更新、ローカルリソースの改ざん、メソッドフッキング、メソッドスウィズリング、動的メモリ改ざんについて記載します。
アプリケーションがモバイルデバイスに一旦配信されると、コードとデータといったリソースは端末に常駐することになります。攻撃者は、そのコードを直接改ざんしたり、メモリ内容を動的に改ざんしたり、アプリケーションが使用するシステムAPIを変更や置換したり、アプリケーションのデータやリソースを改ざんしたりすることが可能です。これにより攻撃者は、個人的利益もしくは金銭的利益のために、ソフトウェアが本来意図している使用方法を直接覆すことができるようになります。</td>
  </tr>
  <tr>
    <td><a href="0xm9-M9-Reverse%20Engineering.md">M9:リバースエンジニアリング</a></td>
    <td>本カテゴリでは、ソースコードやライブラリ、アルゴリズム、その他資材を特定しようとする、バイナリ解析について記載します。IDA Pro、Hopper、otool、その他のバイナリ検査ツールのようなソフトウェアを使用することで、攻撃者はアプリケーションの内部構造を把握することができます。これにより、バックエンドサーバや暗号化用の定数や暗号、知的財産に関する情報が晒されるだけでなく、アプリケーションに存在する新たな脆弱性も悪用される恐れがあります。</td>
  </tr>
  <tr>
    <td><a href="0xma-M10-Extraneous%20Functionality.md">M10:余計な機能</a></td>
    <td>開発者は、本番環境にリリースするつもりではない隠されたバックドア機能や内部開発用のセキュリティコントロールを本番用に含めてしまうことがあります。例えば、開発者がうっかりハイブリッドアプリケーションのコメントにパスワードを記載してしまったり、テストで無効化した二要素認証をそのままにしてしまったりする恐れがあります。</td>
  </tr>
</table>
