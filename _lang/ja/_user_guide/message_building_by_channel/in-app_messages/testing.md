---
nav_title: テスト中...
article_title: アプリ内メッセージのテスト
page_order: 4.5
description: "この参考記事では、アプリ内メッセージをテストすることの価値、テスト方法、および送信前に考慮すべき事項のチェックリストについて説明します。"
channel:
  - in-app messages
  
---

# アプリ内メッセージのテスト

> キャンペーンを送信する前に、必ずアプリ内メッセージをテストすることが非常に重要です。プレビューとテストの機能により、アプリ内メッセージを確認する方法が 2 つ提供されます。メッセージをプレビューして作成中に視覚的に確認したり、自分のデバイスまたは特定のユーザーのデバイスにテスト メッセージを送信したりできます。両方を活用することをお勧めします。

## プレビュー

アプリ内メッセージを作成しながらプレビューできます。これにより、最終的なメッセージがユーザーの視点からどのように見えるかを視覚化できるようになります。

{% alert warning %}
**プレビュー**では、メッセージの表示がユーザーのデバイス上での実際のレンダリングと一致しない場合があります。メディア、コピー、パーソナライゼーション、カスタム属性が正しく生成されることを確認するために、常にデバイスにテスト メッセージを送信することをお勧めします。
{% endalert %}

### アプリ内メッセージ生成プレビュー

ランダムなユーザー、特定のユーザー、またはカスタマイズされたユーザーに対してメッセージがどのように表示されるかをプレビューします。最後の 2 つは、メッセージにパーソナライズや複数の言語が含まれている場合に特に便利です。また、モバイル デバイスまたはタブレットのメッセージをプレビューして、ユーザーがどのような体験をするかをよりよく把握することもできます。

![アプリ内メッセージを作成するときに、メッセージがどのように表示されるかのプレビューを表示する [作成] タブ。ユーザーは選択されていないため、本文セクションに追加されたLiquidがそのまま表示されます。][1]

Braze では、3 世代のアプリ内メッセージが利用できます。サポートされている世代に基づいて、メッセージを送信するデバイスを微調整できます。

![アプリ内メッセージをプレビューするときに世代を切り替えます。][2]{: height="50%" width="50%"}

## テスト

{% alert warning %}
[コンテンツ テスト グループ]({{site.baseurl}}/user_guide/administrative/app_settings/developer_console/internal_groups_tab/#content-test-groups) または個々のユーザーにテストを送信するには、送信前にテスト デバイスでプッシュを有効にする必要があります。<br><br>たとえば、テスト メッセージが表示される前に通知をタップするには、iOS デバイスでプッシュを有効にする必要があります。
{% endalert %}

### ユーザーとしてメッセージをプレビュー

ユーザーと同じように、**[テスト]** タブからメッセージをプレビューすることもできます。特定のユーザー、ランダムなユーザーを選択したり、カスタム ユーザーを作成したりできます。

![アプリ内メッセージを作成するときのテストタブ。「ユーザーとしてメッセージをプレビュー」は「カスタム ユーザー」に設定されており、使用可能なプロファイル フィールドが構成可能なオプションとして表示されます。][3]

### テストチェックリスト

- 画像やメディアは期待どおりに表示され、動作しますか?
- Liquid は期待通りに機能しますか?Liquid が情報を返さない場合に備えて、 [デフォルトの属性値]({{site.baseurl}}/user_guide/personalization_and_dynamic_content/liquid/conditional_logic/#accounting-for-null-attribute-values) を考慮しましたか?
- あなたのコピーは明確、簡潔、そして正確ですか?
- ボタンはユーザーを適切な場所に誘導しますか?

[1]: {%image_buster /assets/img/in-app-message-preview.png %}
[2]: {% image_buster /assets/img/iam-generations.gif %}
[3]: {% image_buster /assets/img/iam-user-preview.png %}
