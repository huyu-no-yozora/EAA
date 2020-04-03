# User Authentication in Akamai EAA

## 用語
SAML:
XMLで認証可否の情報（ポリシーのようなもの）をやり取りするという規格。
CloudやSSOでよく使われるようだ。

AD:
単なるディレクトリの一種(認証情報等の保管庫)


IdP:
認証・認可を行う。(関連ワード: Assertion/SAML Assertion)<br>
つまり、 "認可を出す場所" とも言える。<br>
認証の仕組みの部分。<br>
IdPという言葉には "フィルタ" のような感覚も持っていると良い。

* SAMLのIdP
> Keycloakは、RedHatが開発している比較的新しいシングルサインオンのソフトウェアで、SAMLのIdPとして利用することができます。

AD FS:
IdPの一種。<br>
ADを使ったフェデレーションの他にも、LDAP(Light Weight Directory Access Protocol)や、
SQL Serverに格納されたIDなどを用いたユーザ認証が可能。(ref: [書籍:日経BP] Windows Server 2016 p.388)

* EAAによって提供されるoriginal IdP
[EAA as the SAML identity provider](https://learn.akamai.com/en-us/webhelp/enterprise-application-access/enterprise-application-access/GUID-58AB8814-8877-40BD-A967-5E57019FC27B.html)



## SAMLの２種類のFlow Type
1. IdP initiated
1. SP initiated
<br>
参考: [SAML flows](https://learn.akamai.com/en-us/webhelp/enterprise-application-access/enterprise-application-access/GUID-7EA59AA6-F5AB-4402-8F59-AD274FDDA81B.html)

## 社内ADをIdPとして使用する場合の設定
### ディレクトリ(AD)との接続設定
LDAP(or LDAP over SSL(LDAPS))のポートを使用して、ADと通信。<br>
コネクターとADの接続（連携）のため、管理者のID・パスワードが必要。（他ドメイン名等）

### IdPの設定
Akamai側に作成(deploy)するか、サードパーティ製の製品等を使用するか。
```yaml
代表例: Windows Server内部の (ADの一機能としての) AD FS
```

## Reference
* [Microsoft: What's new in Active Directory Federation Services](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/overview/whats-new-active-directory-federation-services-windows-server)
* [IPA: アイデンティティ管理技術解説](https://www.ipa.go.jp/security/idm/index.html)
[PDF: アイデンティティ管理技術解説（ドラフト）](https://www.ipa.go.jp/files/000014270.pdf)

* [SAML](https://learn.akamai.com/en-us/webhelp/enterprise-application-access/enterprise-application-access/GUID-E461CC1B-1E7F-4C0C-ABDE-522713BF4F57.html)
* [SAML flows](https://learn.akamai.com/en-us/webhelp/enterprise-application-access/enterprise-application-access/GUID-7EA59AA6-F5AB-4402-8F59-AD274FDDA81B.html)


* [IdPとは](https://support.trustlogin.com/hc/ja/articles/231828068-IdP-Identity-Provider-%E3%82%A2%E3%82%A4%E3%83%87%E3%82%A3%E3%83%BC%E3%83%94%E3%83%BC)
* [SAML | Security Assertion Markup Language | サムル | サムエル](https://support.trustlogin.com/hc/ja/articles/231915988-SAML-Security-Assertion-Markup-Language-%E3%82%B5%E3%83%A0%E3%83%AB-%E3%82%B5%E3%83%A0%E3%82%A8%E3%83%AB)
* [IdPとは](https://www.designet.co.jp/faq/term/?id=SWRQ)



