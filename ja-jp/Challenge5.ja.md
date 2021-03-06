﻿# 課題 5 - プロセスの成果

## 背景

アプリケーションでイベントが発生すると、多くの場合、開発者はそのイベントにさまざまな場所や方法で対応する必要があります。 Azure Event Gridは、パブリッシュ/サブスクライブモデルを使用して均一なイベント消費を可能にするインテリジェントなイベントルーティングサービスを提供します。課題5ではあなたのチームにイベントグリッドトピックを作成させ、いくつかのサブスクリプションを作成させます。

ユーザーが開始したボットの会話は、ボットにとって最も一般的で使い慣れた使用例です。しかし、ボットは、積極的なメッセージを通じて全く新しい会話を開始することができます。これは、ボットの非常に一般的な開発者シナリオであり、イベントグリッドのサブスクリプションで実行する機能になります。

この課題では、Microsoft Graphを使用してユーザープロファイルも更新します。 Microsoft Graphを通じて利用可能なデータは、第1者データに限定されません。 Microsoft Graphのリソースは、サードパーティのデータを拡張機能によって拡張することができます。この課題は、ユーザーがトリビアゲームを通じて獲得した達成バッジを保存するための公開拡張を使用します。

## 課題

あなたのボットは、ユーザの達成バッジを返す[Submit Answer](https://msopenhack.azurewebsites.net/swagger/ui/index#!/Trivia/Trivia_SubmitAnswer) APIを呼び出します。 ユーザーが新しいアチーブメントバッジを獲得したら、そのデータを作成してAzureイベントグリッドトピックに送信する必要があります。 Azure関数を使用して、イベントグリッドトピックへのサブスクリプションを作成します。Azure関数は、Microsoftチームの各チームメンバーに個別に積極的なメッセージを送信し、達成状況を発表します。 ロスタ情報を使用して、各ユーザに積極的にメッセージを送るために必要な詳細を見つけることができます（これを自由に記述してください）。 新しい成果バッジが獲得されたときにMicrosoft Graphでユーザーのプロファイルを更新するイベントグリッドトピックの2番目のサブスクリプションを作成します。 達成バッジは、 "com.msopenhack.trivia" extensionNameを使用して、ユーザーオープン拡張の「バッジ」プロパティに格納する必要があります。

注：イベントグリッドは、ボットの会話ロジックから重い処理を切り離すことができるので（ボットがエンドユーザに遅くなるようにするため）、ここではイベントグリッドが使用されます。

## 成功条件

- ユーザーが新しいアチーブメントバッジを獲得した場合、ボットは各チームメンバーにプロアクティブなメッセージを個別に送信する必要があります。
- プロアクティブなメッセージはAzureイベントグリッドトピックのサブスクリプションから送信する必要があります。
- ユーザーが新しいアチーブメントバッジを獲得した場合は、extensionName com.msopenhack.triviaとbadgeという名前のプロパティを使用して、ユーザーオープン拡張にその値を格納する必要があります。

## 注意事項

- リーダーボードと同様に、このプロセスは、Microsoft Graphに対して操作を実行するためのトークンを必要とします。ユーザーオープン拡張を作成/更新するには、委任されたアクセス権User.ReadWriteが必要です。

## 参考資料

- [カスタムイベントを作成してAzureイベントグリッドにルーティングする](https://docs.microsoft.com/ja-jp/azure/event-grid/custom-event-quickstart)
- [Azure関数の使い方](https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-overview)
- [開いている拡張機能を使用してMicrosoft Graphにカスタムデータを追加する](https://developer.microsoft.com/ja-jp/graph/docs/concepts/extensibility_open_users)
- [Bot FrameworkのOAuth用BotAuthパッケージ](https://github.com/MicrosoftDX/botauth)
- [ボット用のMicrosoft Teams認証フロー](https://docs.microsoft.com/ja-jp/microsoftteams/platform/concepts/authentication/auth-flow-bot)
- [Azure Botサービス経由でボットに認証を追加する](https://docs.microsoft.com/ja-jp/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0)
