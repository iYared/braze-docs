---
nav_title: TLS 1.0 & amp; 1.1 減価償却
page_order: 2

page_type: update
description: "2018年5月に完成したTLS 1.0とTLS 1.1のBrazeの減価償却について述べた。"
---
# TLS 1.0 & 1.1 非推奨

{% alert update %}
PCI Security Standards Council の勧告に従って、TLS 1.0 と1.1 の両方でTransport Layer Security (TLS) 暗号のサポートが削除されました。2018年5月に完成したこのサポートの廃止を2段階で実施しました。
{% endalert %} 

## バックグラウンド

Braze は、2018年5 月に終了した2 つのフェーズでPCI Security Standards Council によって作成された推奨に従って、TLS 1.0 と1.1 の両方で、既知の弱いTransport Layer Security (TLS) 暗号を廃止しています。

この変更は、Brazeのプラットフォームに関連するいかなる違反や問題にも対応するものではなく、クラス最高のセキュリティとデータ標準を維持し、顧客とその顧客を積極的に保護するための予防措置として行われています。

近年、TLSとその前身であるSecure Sockets Layer(SSL)の両方に関連する多くのシステマティックなセキュリティ問題があります。これには、[POODLE][1]、[Heartbleed][2]、[LOGJAM][3]Brazeは、他のテクノロジー企業とともに、攻撃が発見されたとき、例えば2014年にSSLv3のサポートを削除するなど、弱い暗号化プロトコルと暗号を無効にするための行動をとってきました。

最近では、PCI Security Standards Council が2015年4 月に[Payment Card Industry Data Security Standard][4](PCI-DSS)の暗号化関連ガイダンスを発表しました。このガイダンスは、SSL 3.0、TLS 1.0、およびTLS 1.1でサポートされている暗号スイートの一部を、強力な暗号のプロトコルリストから除外し、企業がインターネットユーザのセキュリティを確保するために、これらのプロトコルや暗号のサポートを中止することを奨励します。

暗号スイートは、セキュアなSSL またはTLS 接続をネゴシエートするときに、暗号化、認証、および通信の整合性を提供するアルゴリズムの組み合わせです。特定の暗号が壊れる可能性があることが判明した場合(現在の既知の攻撃があるかどうかにかかわらず)、暗号は"weaknesses"を持つと見なされ、将来の攻撃を可能にします。PCI DSS 準拠要件からこれらのTLS 暗号を除外することにより、PCI DSS Council はサービスプロバイダにクラス最高の暗号化標準のみをサポートするよう要求しています。PCI DSS Council は、TLS 1.0 およびTLS 1.1 のサポートを削除するために、暗号化要件に準拠する期限を2018年6 月30 日に設定しました。

## Brazeの減価償却計画
PCI DSS Council の推奨事項に準拠するため、Braze は当社のサービスでサポートするTLS の最小バージョンを引き上げます。私たちのコンプライアンス計画と、そのブランドとユーザーへの潜在的な影響について、より良いアイデアをお伝えするために、私たちの計画には2つの主なフェーズがあります。

### フェーズ1:2017年10月1日

Braze は、Braze のWeb ダッシュボードおよびREST API から次の暗号を使用する機能を削除します。

- `TLS_RSA_WITH_AES_256_CBC_SHA`
- `TLS_RSA_WITH_AES_128_CBC_SHA`
- `TLS_RSA_WITH_AES_256_CBC_SHA256`
- `TLS_RSA_WITH_AES_256_GCM_SHA384`
- `TLS_RSA_WITH_AES_128_CBC_SHA256`
- `TLS_RSA_WITH_AES_128_GCM_SHA256`
- `TLS_RSA_WITH_3DES_EDE_CBC_SHA`

この変更は、すべての最新のWebブラウザがよりセキュアな暗号をサポートしているため、Brazeダッシュボードにアクセスする顧客に影響を与えるものではありません。ただし、10 月1 日以降にWeb ダッシュボードにアクセスしたときにSSL 暗号化エラーが発生した場合は、Web ブラウザの最新バージョンにアップグレードするだけで問題を修正できます。

エンジニアリングチームは、Braze のREST API とのサーバー間通信にこれらの暗号を使用していないことを確認する必要があります。もしそうであれば、BrazeのAPIを使い続けるために、10月1日より前に、より安全な暗号を使うためにコードを更新する必要があるでしょう。ただし、弱い暗号を使用している可能性のある古く古いモバイルデバイスのサポートを維持するために、Braze は引き続き、SDK からデータを受信したAPIS でこれらの暗号をサポートします。

### フェーズ 2:2018年5月31日

Braze は、Braze ダッシュボード、REST API、およびSDK と通信するAPI を含む、2018年5 月31 日にすべてのBraze Services 全体でTLS 1.0 およびTLS 1.1 のサポートを無効にします。また、SDKデータを受信するAPIに関連して、前のセクションにリストされている暗号のサポートも削除します。つまり、Braze とのすべてのTLS 1.0 および1.1 通信は、この日付現在、当社のネットワークではサポートされません。

この変更の結果、一部の古いまたは古いモバイルデバイス(Androidの初期バージョンを実行している可能性がある)は、Brazeとの通信機能を失い、データをBrazeに送信したり、Brazeからアプリ内メッセージを受信したりすることができなくなることがあります。しかし、この変更はごく少数のデバイスにしか影響しないことが予想される。影響を受けるデバイスは、1 か月後の2018年6 月30 日(TLS 1.0 およびTLS 1.1 暗号の削除についてPCI DSS 理事会が設定した日付) にもPCI 準拠のWeb サイトまたはサービスと通信できなくなります。

## 行動計画
ブランドがBraze のREST API を使用している場合は、エンジニアリングチームに相談して、サービスの中断を避けるために、TLS 1.2 を使用して、すべてのサーバー間でBraze への呼び出しがTLS 1.2 で行われるようにします。Java 7 を使用する古いバージョンのTLS など、一部のプログラミング言語はデフォルトで使用されるため、エンジニアリングチームはアップグレードされた暗号化要件をサポートするためにいくつかのコード変更を行う必要がある場合があります。

Apple は2016年末からTLS 1.2 を必要としているため、Apple デバイスはBraze の計画的な非推奨の影響を受けません。現代のWeb ブラウザにも同じことが当てはまるため、これらの変更がWeb SDK の使用に影響を与えることは予想されません。ただし、Android 4.4 (KitKat) 以下を実行しているAndroid デバイスでは、デフォルトでTLS 1.2 が使用されない場合があるため、2018年5 月31 日までに、Android の統合を少なくともBraze SDK バージョン2.0.3 (特定のデバイスがサポートできる場合は、デフォルトでTLS 1.2 を使用) にアップグレードする手順を実行してください。

最後に、TLS 1.0とTLS 1.1の暗号スイートには既知の弱点があるため、将来、攻撃が発生する可能性があります。これにより、すべての顧客のセキュリティを保護するために、減価償却計画のスピードアップをBrazeに要求することになります。Braze は、TLS 1.0 および1.1 プロトコルに関連するセキュリティの状態および関連する攻撃を監視し、前のセクションでレイアウトされたタイムラインを変更する攻撃を知った場合は、ループを維持します。ただし、この潜在的な影響があるため、エンジニアリングチームと連携して、Braze へのAPI 呼び出しがTLS 1.2 で保護されていること、および今後数か月以内に最新のAndroid SDK にアップグレードすることを確認することを強くお勧めします。


[1]: https://www.us-cert.gov/ncas/alerts/TA14-290A
[2]: https://en.wikipedia.org/wiki/Heartbleed
[3]: https://en.wikipedia.org/wiki/Logjam_(computer_security)
[4]: https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard
