---
title: Třídy zobrazení (Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: a3e0f837bc13c022bec91bfff6e38c1513abaf16
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302969"
---
# <a name="view-classes-windows"></a>Třídy zobrazení (Windows)

`CView` a jeho odvozené třídy jsou podřízená okna, která představují klientskou oblast okna rámce. Zobrazení zobrazují data a přijímají vstup pro dokument.

Třída zobrazení je asociována s třídou dokumentu a třídou okna s rámečkem pomocí objektu šablony dokumentu.

[CView](../mfc/reference/cview-class.md)<br/>
Základní třída pro zobrazení dat dokumentu v konkrétní aplikaci. Zobrazení zobrazují data a přijímají uživatelský vstup pro úpravy nebo výběr dat. Odvodit třídu zobrazení nebo třídy z `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Základní třída pro zobrazení s možnostmi posouvání Odvodíte třídu zobrazení z `CScrollView` pro automatické posouvání.

## <a name="form-and-record-views"></a>Zobrazení formulářů a záznamů

Zobrazení formuláře jsou také posouvání zobrazení. Jsou založeny na šabloně dialogového okna.

Zobrazení záznamů jsou odvozena z zobrazení formuláře. Kromě šablony dialogového okna mají také připojení k databázi.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Zobrazení posuvníku, jehož rozložení je definováno v šabloně dialogového okna. Odvození třídy z `CFormView` k implementaci uživatelského rozhraní na základě šablony dialogového okna.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Poskytuje zobrazení formuláře přímo připojené k objektu sady záznamů DAO (Data Access Object). Podobně jako u všech zobrazení formulářů je `CDaoRecordView` založena na šabloně dialogového okna. Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Poskytuje zobrazení formuláře přímo připojené k objektu sady záznamů rozhraní ODBC (Open Database Connectivity). Podobně jako u všech zobrazení formulářů je `CRecordView` založena na šabloně dialogového okna.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Zobrazení formuláře, které poskytuje funkce platformy pro úpravy HTML WebBrowser

## <a name="control-views"></a>Zobrazení ovládacích prvků

Zobrazení ovládacích prvků zobrazují ovládací prvek jako své zobrazení.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Základní třída pro všechna zobrazení přidružená k ovládacím prvkům Windows. Zobrazení založená na ovládacích prvcích jsou popsána níže.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Zobrazení, které obsahuje standardní ovládací prvek Windows pro úpravy (viz [CEdit](../mfc/reference/cedit-class.md)). Ovládací prvky pro úpravy podporují úpravy textu, hledání, nahrazování a posouvání možností.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Zobrazení, které obsahuje ovládací prvek Windows Rich Edit (viz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Kromě možností ovládacího prvku pro úpravy podporují ovládací prvky s bohatou úpravou písma, barvy, formátování odstavců a vložené objekty OLE.

[CListView –](../mfc/reference/clistview-class.md)<br/>
Zobrazení, které obsahuje ovládací prvek seznamu systému Windows (viz [CListCtrl](../mfc/reference/clistctrl-class.md)). Ovládací prvek seznam zobrazuje kolekci položek, z nichž každý se skládá z ikony a popisku, podobně jako v pravém podokně Průzkumníka souborů.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Zobrazení, které obsahuje ovládací prvek stromu systému Windows (viz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Stromový ovládací prvek zobrazí hierarchický seznam ikon a popisků seřazený podobným způsobem jako v levém podokně Průzkumníka souborů.

## <a name="related-classes"></a>Související třídy

`CSplitterWnd` umožňuje mít více zobrazení v rámci jednoho okna rámce. `CPrintDialog` a `CPrintInfo` podporují možnosti tisku a tisku ve verzi Preview zobrazení. `CRichEditDoc` a `CRichEditCntrItem` se používají s `CRichEditView` k implementaci schopností kontejneru OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Okno, které může uživatel rozdělit do několika podoken. Velikost těchto podoken může měnit uživatel nebo pevná velikost.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Poskytuje standardní dialogové okno pro tisk souboru.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Struktura obsahující informace o úloze tisku nebo náhledu tisku. Používá se v architektuře tisku `CView`.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Udržuje seznam položek klienta OLE, které jsou v `CRichEditView`.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Poskytuje přístup na straně klienta k položce OLE uložené v `CRichEditView`.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../mfc/class-library-overview.md)
