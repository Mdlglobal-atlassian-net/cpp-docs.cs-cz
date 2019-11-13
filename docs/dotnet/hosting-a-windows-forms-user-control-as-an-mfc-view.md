---
title: Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: bf91730f98685935d50ee0076739b436e8d9da60
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964935"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC

Knihovna MFC používá ke hostování model Windows Forms uživatelského ovládacího prvku v zobrazení knihovny MFC třídu CWinFormsView. Zobrazení model Windows Forms knihovny MFC jsou ovládací prvky ActiveX. Uživatelský ovládací prvek je hostován jako podřízený objekt nativního zobrazení a zabírá celou klientskou oblast nativního zobrazení.

Konečný výsledek se podobá modelu používanému [třídou CFormView](../mfc/reference/cformview-class.md). To vám umožní využít návrháře model Windows Forms a modul runtime k vytváření bohatých zobrazení na základě formulářů.

Vzhledem k tomu, že zobrazení model Windows Forms knihovny MFC jsou ovládací prvky ActiveX, nemají stejné `hwnd` jako zobrazení MFC. Nelze je také předat jako ukazatel na zobrazení [CView](../mfc/reference/cview-class.md) . Obecně použijte .NET Framework metody pro práci s model Windows Forms zobrazeními a používejte méně na Win32.

Ukázkovou aplikaci, která zobrazuje model Windows Forms používané v prostředí MFC, naleznete v tématu [integrace MFC a model Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Postupy: Vlastnosti volání a metody ovládacího prvku modelu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Viz také:

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Postupy: Vytváření složených ovládacích prvků](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
