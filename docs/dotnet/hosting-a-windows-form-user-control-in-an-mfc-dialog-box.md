---
title: Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 1a688870f4700e8e3b935245f2c9243f8d5aa823
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704089"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC

Knihovna MFC hostuje ovládací prvek model Windows Forms jako speciální druh ovládacího prvku ActiveX a komunikuje s ovládacím prvkem pomocí rozhraní ActiveX a vlastností a metod <xref:System.Windows.Forms.Control> třídy. Pro práci s ovládacím prvkem doporučujeme použít .NET Framework vlastnosti a metody.

Ukázkovou aplikaci, která zobrazuje model Windows Forms používané v prostředí MFC, naleznete v tématu [integrace MFC a model Windows Forms](https://www.microsoft.com/en-us/download/details.aspx?id=2113).

> [!NOTE]
>  V aktuální verzi `CDialogBar` objekt nemůže hostovat ovládací prvky model Windows Forms.

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Vytvoření uživatelského ovládacího prvku a jeho hostování v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Postupy: vytvoření datové vazby DDX/DDV pomocí model Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Odkaz

&#124; Třída [CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) třídy [CDialog](../mfc/reference/cdialog-class.md) &#124; třídy [CWnd](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Viz také:

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Rozdíly v programování model Windows Forms/MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
