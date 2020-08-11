---
ms.openlocfilehash: f1671f4f40e3eb44465431d39994cf5e623665a1
ms.sourcegitcommit: 08290d004d1a7e7ac579bf1f96abf8437921dc70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87919298"
---
# <a name="visual-studio"></a>[Visual Studio](#tab/vswin)

1. **[MainPage.xaml]** で、[`TextChanged`](xref:Xamarin.Forms.InputView.TextChanged) イベントと [`Completed`](xref:Xamarin.Forms.Editor.Completed) イベントのハンドラーを設定するように [`Editor`](xref:Xamarin.Forms.Editor) 宣言を変更します。

    ```xaml
    <Editor Placeholder="Enter multi-line text here"
            HeightRequest="200"
            TextChanged="OnEditorTextChanged"
            Completed="OnEditorCompleted" />
    ```

    このコードは、[`TextChanged`](xref:Xamarin.Forms.InputView.TextChanged) イベントを `OnEditorTextChanged` という名前のイベント ハンドラーに設定し、[`Completed`](xref:Xamarin.Forms.Editor.Completed) イベントを `OnEditorCompleted` という名前のイベント ハンドラーに設定します。 どちらのイベント ハンドラーも次の手順で作成されます。

1. **ソリューション エクスプローラー**の **[EditorTutorial]** プロジェクトで **[MainPage.xaml]** を展開し、 **[MainPage.xaml.cs]** をダブルクリックして開きます。 次に、 **[MainPage.xaml.cs]** で、`OnEditorTextChanged` と `OnEditorCompleted` のイベント ハンドラーをクラスに追加します。

    ```csharp
    void OnEditorTextChanged(object sender, TextChangedEventArgs e)
    {
        string oldText = e.OldTextValue;
        string newText = e.NewTextValue;
    }

    void OnEditorCompleted(object sender, EventArgs e)
    {
        string text = ((Editor)sender).Text;
    }
    ```

    [`Editor`](xref:Xamarin.Forms.Editor) のテキストが変更されると、`OnEditorTextChanged` メソッドが実行されます。 `sender` 引数は、`TextChanged` イベントの発生を担当する `Editor` オブジェクトであり、`Editor` オブジェクトへのアクセスに使用できます。 [`TextChangedEventArgs`](xref:Xamarin.Forms.TextChangedEventArgs) 引数は、テキストの変更前と変更後の古いテキスト値と新しいテキスト値を提供します。

    編集が完了すると、`OnEditorCompleted` メソッドが実行されます。 これは、[`Editor`](xref:Xamarin.Forms.Editor) からフォーカスを外すか、さらに iOS では [完了] ボタンを押して行います。 `sender` 引数は、`TextChanged` イベントの発生を担当する `Editor` オブジェクトであり、`Editor` オブジェクトへのアクセスに使用できます。

    > [!IMPORTANT]
    > [`Editor`](xref:Xamarin.Forms.Editor) に入力されたテキストはすべて [`Text`](xref:Xamarin.Forms.InputView.Text) プロパティに格納されます。

1. Visual Studio ツール バーで、 **[開始]** ボタン ([再生] ボタンに似た三角形のボタン) を押し、選択したリモート iOS シミュレーターまたは Android エミュレーター内でアプリケーションを起動します。

    [![iOS および Android でのテキストを含む Editor のスクリーンショット](../images/text-changes.png "テキストを含む Editor")](../images/text-changes-large.png#lightbox "テキストを含む Editor")

    2 つのイベント ハンドラーにブレークポイントを設定し、[`Editor`](xref:Xamarin.Forms.Editor) にテキストを入力して、[`TextChanged`](xref:Xamarin.Forms.InputView.TextChanged) イベントの発生を確認します。 `Editor` からフォーカスを外して、[`Completed`](xref:Xamarin.Forms.Entry.Completed) イベントの発生を確認します。

    [`Editor`](xref:Xamarin.Forms.Editor) イベントの詳細については、「[Xamarin.Forms Editor](~/xamarin-forms/user-interface/text/editor.md)」ガイドの「[Events and Interactivity](~/xamarin-forms/user-interface/text/editor.md#events-and-interactivity)」(イベントとインタラクティビティ) をご覧ください。

# <a name="visual-studio-for-mac"></a>[Visual Studio for Mac](#tab/vsmac)

1. **[MainPage.xaml]** で、[`TextChanged`](xref:Xamarin.Forms.InputView.TextChanged) イベントと [`Completed`](xref:Xamarin.Forms.Editor.Completed) イベントのハンドラーを設定するように [`Editor`](xref:Xamarin.Forms.Editor) 宣言を変更します。

    ```xaml
    <Editor Placeholder="Enter multi-line text here"
            HeightRequest="200"
            TextChanged="OnEditorTextChanged"
            Completed="OnEditorCompleted" />
    ```

    このコードは、[`TextChanged`](xref:Xamarin.Forms.InputView.TextChanged) イベントを `OnEditorTextChanged` という名前のイベント ハンドラーに設定し、[`Completed`](xref:Xamarin.Forms.Editor.Completed) イベントを `OnEditorCompleted` という名前のイベント ハンドラーに設定します。 どちらのイベント ハンドラーも次の手順で作成されます。

1. **Solution Pad** の **[EditorTutorial]** プロジェクトで **[MainPage.xaml]** を展開し、 **[MainPage.xaml.cs]** をダブルクリックして開きます。 次に、 **[MainPage.xaml.cs]** で、`OnEditorTextChanged` と `OnEditorCompleted` のイベント ハンドラーをクラスに追加します。

    ```csharp
    void OnEditorTextChanged(object sender, TextChangedEventArgs e)
    {
        string oldText = e.OldTextValue;
        string newText = e.NewTextValue;
    }

    void OnEditorCompleted(object sender, EventArgs e)
    {
        string text = ((Editor)sender).Text;
    }
    ```

    [`Editor`](xref:Xamarin.Forms.Editor) のテキストが変更されると、`OnEditorTextChanged` メソッドが実行されます。 `sender` 引数は、`TextChanged` イベントの発生を担当する `Editor` オブジェクトであり、`Editor` オブジェクトへのアクセスに使用できます。 [`TextChangedEventArgs`](xref:Xamarin.Forms.TextChangedEventArgs) 引数は、テキストの変更前と変更後の古いテキスト値と新しいテキスト値を提供します。

    編集が完了すると、`OnEditorCompleted` メソッドが実行されます。 これは、[`Editor`](xref:Xamarin.Forms.Editor) からフォーカスを外すか、さらに iOS では [完了] ボタンを押して行います。 `sender` 引数は、`TextChanged` イベントの発生を担当する `Editor` オブジェクトであり、`Editor` オブジェクトへのアクセスに使用できます。

    > [!IMPORTANT]
    > [`Editor`](xref:Xamarin.Forms.Editor) に入力されたテキストはすべて [`Text`](xref:Xamarin.Forms.InputView.Text) プロパティに格納されます。

1. Visual Studio for Mac ツール バーで、 **[開始]** ボタン ([再生] ボタンに似た三角形のボタン) を押し、選択した iOS シミュレーターまたは Android エミュレーター内でアプリケーションを起動します。

    [![iOS および Android でのテキストを含む Editor のスクリーンショット](../images/text-changes.png "テキストを含む Editor")](../images/text-changes-large.png#lightbox "テキストを含む Editor")

    2 つのイベント ハンドラーにブレークポイントを設定し、[`Editor`](xref:Xamarin.Forms.Editor) にテキストを入力して、[`TextChanged`](xref:Xamarin.Forms.InputView.TextChanged) イベントの発生を確認します。 `Editor` からフォーカスを外して、[`Completed`](xref:Xamarin.Forms.Entry.Completed) イベントの発生を確認します。

    [`Editor`](xref:Xamarin.Forms.Editor) イベントの詳細については、「[Xamarin.Forms Editor](~/xamarin-forms/user-interface/text/editor.md)」ガイドの「[Events and Interactivity](~/xamarin-forms/user-interface/text/editor.md#events-and-interactivity)」(イベントとインタラクティビティ) をご覧ください。
