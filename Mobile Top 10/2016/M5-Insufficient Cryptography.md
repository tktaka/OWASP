# M5：不十分な暗号化

| <center>脅威エージェント</center> | <center>攻撃経路</center> | <center>セキュリティ上の弱点</center> || <center>技術的な影響</center> | <center>ビジネスへの影響</center> |
| -- | -- | -- | -- | -- | -- |
| <center>アプリケーション依存</center> | <center>攻撃難易度：容易</center> | <center>普及度：中</center> | <center>検出難易度：普通</center> | <center>深刻な影響</center> | <center>アプリケーション/ビジネス依存</center> |
| 脅威エージェントは以下です。 <br> 不適切に暗号化されたデータに物理的にアクセスできる人、もしくは、攻撃者のために動作するモバイルマルウェア | 攻撃経路は以下です。 <br> デバイスへの物理アクセスやネットワークトラフィックキャプチャを通したデータの解読、もしくは暗号化されたデータへのアクセスを持つデバイス上のマルウェアアプリ | この脆弱性を悪用するには、攻撃者は、暗号プロセスでの脆弱な暗号アルゴリズムや欠陥により、暗号化されたコードや機密データを暗号化されていないオリジナルな形に戻さなければなりません。 || 本脆弱性はモバイルデバイスから機密データの不正な取得という結果につながります。 | 本脆弱性は様々なビジネスへの影響をもたらす可能性があります。通常、脆弱な暗号は以下の結果につながります。 <br> -プライバシー侵害 <br> - 情報の窃取 <br> - コードの盗用 <br> - 知的財産の窃盗 <br> - 風評被害 |

## 脆弱性有無の確認
暗号を利用するほとんどのモバイルアプリで、安全でない暗号が使用されています。脆弱な暗号がモバイルアプリで使用されているのが見られる点が2つあります。
1つ目は、モバイルアプリが、根本的な欠陥があり攻撃者によって悪用され機密データが復号される可能性があるプロセスを、暗号化/復号に使用している場合です。2つ目は、モバイルアプリが、本質的に脆弱であり攻撃者によって直接解読される可能性がある暗号化/復号アルゴリズムを実装または使用している場合です。以下のサブセクションでは、これらの両方のシナリオをより詳しく解説します。
 
### 組み込みコード暗号化プロセスの依存
デフォルトでは、iOSアプリケーションはコードの暗号化によりリバースエンジニアリングから(理論上は)保護されています。iOSのセキュリティモデルは、非Jailbreak環境で実行するために、信頼できるソースによってアプリが暗号化され署名されることを要求しています。起動時に、iOSによって署名が検証された後、iOSアプリローダーはメモリ上でアプリを復号しコードを実行します。この機能により、理論上は攻撃者によるiOSモバイルアプリへのバイナリ攻撃を防止することができます。
ClutchModやGBDのようなフリーツールを使用することで、攻撃者はJailbreakしたデバイスに暗号化されたアプリをダウンロードし、iOSローダーがメモリに読み込み復号した時点で(ローダーが実行する直前)、復号されたアプリのスナップショットを取得するでしょう。攻撃者はスナップショットを取得しディスクに保存すると、攻撃者は容易にアプリの静的/動的解析を行い、さらなるバイナリ攻撃を行うためにIDA ProやHopperのようなツールを使用することができます。
組み込みコードの暗号化アルゴリズムを回避することは、ささいなことです。モバイルOSによって提供されている組み込みコードの暗号化を攻撃者はいつも回避することができると想定してください。リバースエンジニアリング防止のレイヤーを追加するために必要なステップについては、M9を参照してください。

### 不十分な鍵管理プロセス
鍵の取り扱いを誤るのなら、最良のアルゴリズムを使用するかどうかは重要ではありません。多くの人が適切な暗号化アルゴリズムを間違って使用しており、独自のプロトコルで実装してしまっています。以下に、問題となる例をいくつか挙げます。
 - 攻撃者が読み取り可能なディレクトリに暗号化されたコンテンツと鍵を保存している。
 - 攻撃者が取得可能な鍵を生成している。
 - バイナリ内でハードコードされた鍵の使用を避ける。
 - 鍵はバイナリ攻撃で傍受される可能性がある。バイナリ攻撃を防ぐための情報はM10を参照すること。
 
### カスタム暗号化プロトコルの作成と使用
モバイルやその他において、独自の暗号化アルゴリズムやプロトコルを作成して使用することほど、暗号化を間違って扱う方法はありません。
セキュリティコミュニティによって強度だと認められている最新のアルゴリズムを常に使用し、可能な限りモバイルプラットフォームが提供する最新の暗号化APIを使用してください。バイナリ攻撃によって、バイナリ内でハードコードされた鍵とアプリで使用されている共通ライブラリを、攻撃者によって特定される可能性があります。暗号化に関する非常に高いセキュリティ要件が要求される場合、ホワイトボックス暗号の使用を検討すべきです。共通ライブラリの悪用につながるバイナリ攻撃を防ぐためには、M10を参照してください。
 
### 安全でないアルゴリズム使用と非推奨アルゴリズム使用の両方またはいずれか一方
多くの暗号アルゴリズムとプロトコルは、重大な脆弱性が存在したりまたは現在のセキュリティ要件と比較して不十分であるため、使用するべきではありません。これには以下が含まれます。
 - RC4
 - MD4
 - MD5
 - SHA1


## 防止方法
機密データを扱う場合は、以下を実施することが最善です。
 - 可能な限り、モバイルデバイスに機密データを保存することを避けること。
 - 少なくとも今後10年間は使われ続ける暗号標準を適用すること。
 - 推奨アルゴリズムに関するNISTのガイドラインに従うこと(参考資料のその他を参照してください)。


## 攻撃シナリオの例


## 参考資料
### OWASP
 - [OWASP Cryptographic Storage Cheat Sheet](https://www.owasp.org/index.php/Cryptographic_Storage_Cheat_Sheet)
 - [OWASP Key Management Cheat Sheet](https://www.owasp.org/index.php/Key_Management_Cheat_Sheet)
 
### その他
 - [NIST Encryption Guidelines](http://csrc.nist.gov/publications/drafts/800-175/sp800-175b_draft.pdf)