# V5: ネットワーク通信要件

## 本章の目的

本章の目的は、モバイルアプリケーションとリモートサービスエンドポイントの間でやりとりされる情報の機密性と完全性を確認することです。少なくとも、モバイルアプリケーションは、適切な設定のTLSプロトコルを用いた暗号化された通信経路のようセキュリティを考慮した設定をしなければなりません。レベル2では、SSLピンニングなどの追加の多層防御策があります。

## セキュリティ検証要件

| # | 説明 | L1 | L2 |
| --- | --- | --- | --- |
| **5.1** | データはネットワーク上において、TLSを使用して暗号化されている。アプリケーション全体を通して安全な通信路が一貫して使用されている。 | ✓ | ✓ |
| **5.2** | TLS設定は今日のベストプラクティスに合わせる。モバイルオペレーティングシステムが推奨基準規格をサポートしていない場合、可能な限り近い基準に一致するようにする。 | ✓ | ✓ |
| **5.3** | 安全な通信路が確立する際、アプリケーションがリモートエンドポイントのX.509証明書を検証する。信頼されたCAによって署名された証明書のみを受け入れる。 | ✓ | ✓ |
| **5.4** | アプリケーションは自身の証明書ストアを使用したり、エンドポイントの証明書や公開鍵をピンニングしたりする。そしてその後、信頼されたCAによって署名されたとしても、異なる証明書や鍵がエンドポイントより提供されたら、そのエンドポイントとの通信路を確立しない。 |   | ✓ |
| **5.5** | アプリケーションは、登録やアカウント回復などの重要操作のための、安全とは言い難い単方向通信(たとえば、EメールやSMS)を信頼しない。 |  | ✓ |
| **5.6** | アプリケーションは最新の接続ライブラリとセキュリティライブラリのみに依存している。 |  | ✓ |

## 参考文献

OWASP モバイルセキュリティテストガイドは、本章に記載されている要件を検証するための詳細な指示を提供しています。

- Android - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05g-Testing-Network-Communication.md
- iOS - https://github.com/OWASP/owasp-mstg/blob/master/Document/0x06g-Testing-Network-Communication.md

詳細は以下参照：

- OWASP Mobile Top 10:  M3 - Insecure Communication(安全でない通信): https://www.owasp.org/index.php/Mobile_Top_10_2016-M3-Insecure_Communication
- CWE: https://cwe.mitre.org/data/definitions/319.html
- CWE: https://cwe.mitre.org/data/definitions/295.html