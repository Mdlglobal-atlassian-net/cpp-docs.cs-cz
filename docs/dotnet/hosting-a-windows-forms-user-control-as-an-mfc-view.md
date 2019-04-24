---
title: Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: 9c59f28739ab94210c16bd800a48997f3f2282df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222868"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC

CWinFormsView – třída knihovny MFC používá k hostování uživatelského ovládacího prvku Windows Forms v zobrazení MFC. Zobrazení formulářů Windows MFC jsou ovládací prvky ActiveX. Uživatelský ovládací prvek je hostovaný jako podřízený objekt nativní zobrazení a zabírá celé oblasti klienta nativní zobrazení.

Konečný výsledek vypadá podobně jako model používaný [třídy CFormView](../mfc/reference/cformview-class.md). To vám umožní využít Návrháře formulářů Windows a modulu runtime a vytvářet bohaté zobrazení založené na formulářích.

Vzhledem k tomu zobrazení MFC Windows Forms – ovládací prvky ActiveX, nemají stejné `hwnd` jako zobrazení MFC. Také nelze předat jako ukazatel [CView](../mfc/reference/cview-class.md) zobrazení. Obecně platí pomocí metod rozhraní .NET Framework pracovat se zobrazeními Windows Forms a využívá méně Win32.

Ukázková aplikace, která ukazuje použití s knihovnou MFC modelu Windows Forms, naleznete v tématu [MFC a integrace formulářů Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Vytvoření uživatelského ovládacího prvku a hostování zobrazení MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[Postupy: Přidání směrování příkazů do ovládacího prvku modelu Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[Postupy: Vlastnosti a metody volání ovládacího prvku modelu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>Viz také:

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Postupy: Vytváření složených ovládacích prvků](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
