---
title: Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374489"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC

Knihovna MFC hostuje ovládací prvek Windows Forms jako zvláštní druh ovládacího prvku ActiveX a <xref:System.Windows.Forms.Control> komunikuje s ovládacím prvkem pomocí rozhraní ActiveX a vlastností a metod třídy. Doporučujeme použít vlastnosti a metody rozhraní .NET Framework pro provoz s ovládacím prvkem.

Ukázková aplikace, která zobrazuje formuláře systému Windows používané s knihovnou MFC, naleznete v [tématu Knihovna MFC a integrace formulářů systému Windows .](https://www.microsoft.com/download/details.aspx?id=2113)

> [!NOTE]
> V aktuální verzi `CDialogBar` objekt nemůže být hostitelem ovládacích prvků windows forms.

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Vytvoření uživatelského ovládacího prvku a jeho hostování v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Postup: Do DDX/DDV Data Binding with Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Referenční informace

[Třída CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [třída CDialog](../mfc/reference/cdialog-class.md) &#124; [třída CWnd](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Viz také

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Rozdíly v programování formulářů a knihovny MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
