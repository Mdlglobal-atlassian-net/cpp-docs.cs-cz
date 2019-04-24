---
title: Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 56cf00da71fe6c47e39de2a8fc06df572a301a61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222985"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC

Hostuje ovládacího prvku Windows Forms jako zvláštní druh ovládacího prvku ActiveX knihovny MFC a komunikuje s ovládacím prvkem pomocí rozhraní technologie ActiveX, vlastnosti a metody <xref:System.Windows.Forms.Control> třídy. Doporučujeme provozovat na ovládacím prvku pomocí vlastnosti rozhraní .NET Framework a metod.

Ukázková aplikace, která ukazuje použití s knihovnou MFC modelu Windows Forms, naleznete v tématu [MFC a integrace formulářů Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

> [!NOTE]
>  V aktuální verzi `CDialogBar` objektu nelze umístit ovládací prvky Windows Forms.

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Vytvoření uživatelského ovládacího prvku a jeho hostování v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Postupy: Proveďte DDX/DDV datové vazby pomocí Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Postupy: Zpracování jímky událostí modelu Windows Forms z nativních tříd jazyka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Odkaz

[CWinFormsControl – třída](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog – třída](../mfc/reference/cdialog-class.md) &#124; [třída CWnd](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>Viz také:

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows Forms a MFC programování rozdíly](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
