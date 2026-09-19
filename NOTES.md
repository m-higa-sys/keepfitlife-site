# 作業メモ

- `CNAME` ファイルは GitHub の Settings → Pages（カスタムドメイン設定）から自動生成される。
- ローカルでの編集・コミットを始める前に、必ず `git pull origin main` を実行してから作業すること（`CNAME` など、ローカルにない変更が origin 側に入っていることがあるため）。

## 法人ページ（keepfitlife.com）2026-09-19 公開時の記録

### 基本情報
- 公開URL：https://keepfitlife.com（www.keepfitlife.com も同じページ。HTTPS強制ON）
- 仮URL：https://m-higa-sys.github.io/keepfitlife-site/（外部に伝えない。今は keepfitlife.com へ自動転送）
- リポジトリ：m-higa-sys/keepfitlife-site（public）／GitHub Pages：main ブランチ・/(root)
- 構成：index.html 1枚（静的HTML・JavaScriptなし）＋ CNAME（GitHub自動生成、中身 keepfitlife.com）
- 作成：2026-09-19

### ページの中身（確定済み）
- 代表挨拶：2026-09-19 社長確定。「柔道整復師」の語は入れない（社長判断）
- 会社概要：商号 株式会社キープフィットライフ／設立 2012年（平成24年）3月5日／代表取締役 比嘉 学／本店所在地 〒355-0047 埼玉県東松山市高坂3-3-13 カームハウス松田1階（登記上の本店＝事業所と同住所）／事業内容 介護保険法に基づく地域密着型通所介護事業／電話 0493-81-5125
- 事業所一覧：リハビリデイサービスyawaragi（正式名称。yawaragi は半角英小文字。「やわらぎ」表記は使わない）→ https://www.keepfitlife-yawaragi.com/
- 事業所を増やすとき：office-card ブロックを1つ複製して書き換える
- 載せないもの：メールアドレス、スタッフ名、利用者情報、GASのURL/トークン、アクセス解析

### 運用ルール
- 編集前に必ず git pull origin main（GitHubがCNAMEを自動コミットするため）
- push は deny-guard により社長がターミナルで行う。クロコはコミットまで＋pushコマンドをチャットに書く
- yawaragi-apps とは完全に別リポジトリ。混ぜない

### ドメイン・DNS（keepfitlife.com）
- 管理会社：ムームードメイン（ムームーID m-higa@keepfitlife.com）／ムームーDNS → カスタム設定「設定2」で管理
- 2026-09-19 に変更した行（これ以外は変更していない）
  - A（サブドメイン空欄）×4：185.199.108.153／185.199.109.153／185.199.110.153／185.199.111.153（旧：23.236.62.147 = Wix）
  - www CNAME：m-higa-sys.github.io（旧：www221.wixdns.net = Wix）
- 絶対に触らない行（メール関係）：MX smtp.google.com（優先度1）、TXT google-site-verification、TXT v=spf1…、_dmarc（TXT/CNAME）、sel1/s1/s2._domainkey、sg
- 「カスタム設定解除」ボタンは押さない（設定2のレコードが全消去され、メールが止まる）
- メール：Google Workspace（keepfitlife.com で契約中）

### 残っている別件（未着手・社長判断待ち）
- ムームーDNSに旧ムームーメールのMX行（mx01.muumuu-mail.com、優先度50）が残っている。2026年2月にムームーメール契約終了済み。実害は出ていない見込み（推論）だが、メールに関わるため整理する場合は1行ずつ確認して行う
- Wixのドメイン一覧に keepfitlife.com（やわらぎHPへのリダイレクト設定）が残っている。DNSがWixを向いていないため現在は無害。Wixのメール配信機能（_dmarc wixemails、sg ascend 等）の認証に使われている可能性があるため、社長判断で「今は残す」。外す場合は影響を調べてから
- keepfitlife.online も所有（ムームー管理）。今回は未使用・無変更
