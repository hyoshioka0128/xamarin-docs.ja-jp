---
title: Xamarin.Forms のデュアル画面のトリガー
description: この記事では、Xamarin.Forms のデュアル画面のトリガーを使用して、XAML でのユーザー インターフェイスの変更に応答する方法について説明します。
ms.prod: xamarin
ms.assetid: 2181715D-3995-4E71-9A21-6B892F0B3B59
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 02/28/2020
no-loc:
- Xamarin.Forms
- Xamarin.Essentials
ms.openlocfilehash: 16a76fb06c0ee54e90fa1bf0d44e419be40ee254
ms.sourcegitcommit: 08290d004d1a7e7ac579bf1f96abf8437921dc70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87918290"
---
# <a name="no-locxamarinforms-dual-screen-triggers"></a>Xamarin.Forms のデュアル画面のトリガー

![プレリリース API](~/media/shared/preview.png)

[`Xamarin.Forms.DualScreen`](xref:Xamarin.Forms.DualScreen) 名前空間には、次の 2 つの状態トリガーが含まれています。

- [`SpanModeStateTrigger`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger) は、アタッチされたレイアウトの表示モードが変更されると、[`VisualState`](xref:Xamarin.Forms.VisualState) の変更をトリガーします。
- `WindowSpanModeStateTrigger` は、ウィンドウの表示モードが変更されると、[`VisualState`](xref:Xamarin.Forms.VisualState) の変更をトリガーします。

状態トリガーの詳細については、「[状態トリガー](~/xamarin-forms/app-fundamentals/triggers.md#state-triggers)」を参照してください。

## <a name="span-mode-state-trigger"></a>スパン モードの状態トリガー

[`SpanModeStateTrigger`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger) は、アタッチされたレイアウトのスパン モードが変更されると、[`VisualState`](xref:Xamarin.Forms.VisualState) の変更をトリガーします。 このトリガーには、1 つのバインド可能なプロパティがあります。

- [`SpanMode`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger.SpanMode) ([`TwoPaneViewMode`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger.SpanMode) 型)。[`VisualState`](xref:Xamarin.Forms.VisualState) が適用されるスパン モードを示します。

> [!NOTE]
> [`SpanModeStateTrigger`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger) は [`StateTriggerBase`](xref:Xamarin.Forms.StateTriggerBase) クラスから派生しているため、[`IsActiveChanged`](xref:Xamarin.Forms.StateTriggerBase.IsActiveChanged) イベントに対してイベント ハンドラーをアタッチできます。

次の XAML の例は、`SpanModeStateTrigger` オブジェクトを含む [`Grid`](xref:Xamarin.Forms.Grid) を示しています。

```xaml
<Grid>
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState x:Name="GridSingle">
                <VisualState.StateTriggers>
                    <dualScreen:SpanModeStateTrigger SpanMode="SinglePane"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Property="BackgroundColor" Value="Green" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="GridWide">
                <VisualState.StateTriggers>
                    <dualScreen:SpanModeStateTrigger SpanMode="Wide" />
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Property="BackgroundColor" Value="Red" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="GridTall">
                <VisualState.StateTriggers>
                    <dualScreen:SpanModeStateTrigger SpanMode="Tall" />
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Property="BackgroundColor" Value="Purple" />
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
    ...
</Grid>
```

この例では、ビジュアル状態は [`Grid`](xref:Xamarin.Forms.Grid) オブジェクトに設定されています。 `Grid` の背景色は、1 つのペインのみが表示されている場合は緑、ペインが横に並んで表示される場合は赤、ペインが上下に表示される場合は紫になります。

## <a name="window-span-mode-state-trigger"></a>ウィンドウのスパン モードの状態トリガー

`WindowSpanModeStateTrigger` は、ウィンドウのスパン モードが変更されると、[`VisualState`](xref:Xamarin.Forms.VisualState) の変更をトリガーします。 このトリガーには、1 つのバインド可能なプロパティがあります。

- [`SpanMode`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger.SpanMode) ([`TwoPaneViewMode`](xref:Xamarin.Forms.DualScreen.SpanModeStateTrigger.SpanMode) 型)。[`VisualState`](xref:Xamarin.Forms.VisualState) が適用されるスパン モードを示します。

> [!NOTE]
> `WindowSpanModeStateTrigger` は [`StateTriggerBase`](xref:Xamarin.Forms.StateTriggerBase) クラスから派生しているため、[`IsActiveChanged`](xref:Xamarin.Forms.StateTriggerBase.IsActiveChanged) イベントに対してイベント ハンドラーをアタッチできます。

次の XAML の例は、`WindowSpanModeStateTrigger` オブジェクトを含む [`Grid`](xref:Xamarin.Forms.Grid) を示しています。

```xaml
<Grid>
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState x:Name="NotSpanned">
                <VisualState.StateTriggers>
                    <dualScreen:WindowSpanModeStateTrigger SpanMode="SinglePane"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Property="BackgroundColor" Value="Red" />
                </VisualState.Setters>
            </VisualState>
            <VisualState x:Name="Spanned">
                <VisualState.StateTriggers>
                    <dualScreen:WindowSpanModeStateTrigger SpanMode="Wide" />
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Property="BackgroundColor" Value="Green" />
                </VisualState.Setters>
            </VisualState>
                <VisualState x:Name="Tall">
                    <VisualState.StateTriggers>
                        <dualScreen:WindowSpanModeStateTrigger SpanMode="Tall" />
                    </VisualState.StateTriggers>
                    <VisualState.Setters>
                        <Setter Property="BackgroundColor" Value="Yellow" />
                    </VisualState.Setters>
                </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
    ...
</Grid>    
```

この例では、ビジュアル状態は [`Grid`](xref:Xamarin.Forms.Grid) オブジェクトに設定されています。 `Grid` の背景色は、1 つのペインのみが表示されている場合は赤、ペインが横に並んで表示される場合は緑、ペインが上下に表示される場合は黄になります。

## <a name="related-links"></a>関連リンク

- [Xamarin.Forms のトリガー](~/xamarin-forms/app-fundamentals/triggers.md)
- [Xamarin.Forms Visual State Manager](~/xamarin-forms/user-interface/visual-state-manager.md)
