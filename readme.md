# 意識が低いプロジェクトでも出来る、手動テストのカバレッジ測定

通常カバレッジ率を測定するのはUnitTestがある場合ですが、レガシーコードのみで構成されたプロジェクトの場合、色々な理由によってテストコードを追加することが難しいです。

せめて、自分が手動でテストしたコードでテスト漏れが(分岐を通っていない)がないか、正確にチェックするため「手動テストでカバレッジ率を計測」する手順を記載します。

手動でプログラムを操作してテストを行う場合、1回で全てテストができないため「カバレッジのマージ」を行う必要があります。その方法も説明します。

## 利用ツール

* [opencover](https://github.com/OpenCover/opencover) カバレッジ測定ツール(カバレッジ収集結果を.xmlファイルに保存)

* [ReportGenerator](ReportGenerator) レポート生成ツール(xmlからhtmlなど読みやすい形に成形)

※Visual Studioのカバレッジ測定ツールはEnterprise版が必要なため利用しません。

## 特徴

* コードによる単体テストは不要。プログラムを操作しながら単体テストを行い、手動操作で通ったコードのカバレッジ率を確認できます。

* 複数回テストを行った場合、自動で結果をマージします。分岐のテスト漏れがある場合、その部分だけテスト行えばカバレッジ率が向上します。

* VisualStudioからアタッチすれば、デバッグしながら同時にカバレッジの測定も可能です。【要確認】

## 課題

* コマンドラインから実行する必要があり、実行がとても面倒です(引数が多く、バッチファイルにしても設定が大変)

  ⇒ カバレッジ測定をサポートするWindowsFormプログラムを作成します。プログラムのパスを設定して実行すれば、レポート生成まで行います。

* IIS(asp.net)のカバレッジ測定はできるか？設定はどうすればよいか？
* exeから読み込むdllも一緒にカバレッジ測定できるのか？
