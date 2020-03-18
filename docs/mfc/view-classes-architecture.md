---
title: Třídy zobrazení (architektura)
ms.date: 09/17/2019
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: 7235ccfea1f41dd185f0b5b6be9b39ea16250d94
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447175"
---
# <a name="view-classes-architecture"></a>Třídy zobrazení (architektura)

`CView` a jeho odvozené třídy jsou podřízená okna, která představují klientskou oblast okna rámce. Zobrazení zobrazují data a přijímají vstup pro dokument.

Třída zobrazení je asociována s třídou dokumentu a třídou okna s rámečkem pomocí objektu šablony dokumentu.

[CView](../mfc/reference/cview-class.md)<br/>
Základní třída pro zobrazení dat dokumentu v konkrétní aplikaci. Zobrazení zobrazují data a přijímají uživatelský vstup pro úpravy nebo výběr dat. Odvodit vaše třídy zobrazení od `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Základní třída pro zobrazení s možnostmi posouvání Odvodíte třídu zobrazení z `CScrollView` pro automatické posouvání.

## <a name="form-and-record-views"></a>Zobrazení formulářů a záznamů

Zobrazení formuláře jsou také posouvání zobrazení. Jsou založeny na šabloně dialogového okna.

Zobrazení záznamů jsou odvozena z zobrazení formuláře. Kromě šablony dialogového okna mají také připojení k databázi.

[Třídy CFormView](../mfc/reference/cformview-class.md)<br/>
Zobrazení posuvníku, jehož rozložení je definováno v šabloně dialogového okna. Odvození třídy z `CFormView` k implementaci uživatelského rozhraní na základě šablony dialogového okna.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Poskytuje zobrazení formuláře přímo připojené k objektu sady záznamů DAO (Data Access Object). Podobně jako u všech zobrazení formulářů je `CDaoRecordView` založena na šabloně dialogového okna. Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

[CHtmlView –](../mfc/reference/chtmlview-class.md)<br/>
Podporuje ovládací prvek pro procházení webu v rámci aplikace. Ovládací prvek podporuje dynamické HTML v knihovně MFC.

[COleDBRecordView –](../mfc/reference/coledbrecordview-class.md)<br/>
Poskytuje podporu OLE DB knihovny MFC pro zobrazení formulářů.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Poskytuje zobrazení formuláře přímo připojené k objektu sady záznamů rozhraní ODBC (Open Database Connectivity). Podobně jako u všech zobrazení formulářů je `CRecordView` založena na šabloně dialogového okna.

## <a name="control-views"></a>Zobrazení ovládacích prvků

Zobrazení ovládacích prvků zobrazují ovládací prvek jako své zobrazení.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Základní třída pro všechna zobrazení přidružená k ovládacím prvkům Windows. Zobrazení založená na ovládacích prvcích jsou popsána níže.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Zobrazení, které obsahuje standardní ovládací prvek Windows pro úpravy (viz [CEdit](../mfc/reference/cedit-class.md)). Ovládací prvky pro úpravy podporují úpravy textu, hledání, nahrazování a posouvání možností.

[CRichEditView –](../mfc/reference/cricheditview-class.md)<br/>
Zobrazení, které obsahuje ovládací prvek Windows Rich Edit (viz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Kromě možností ovládacího prvku pro úpravy podporují ovládací prvky s bohatou úpravou písma, barvy, formátování odstavců a vložené objekty OLE.

[CListView –](../mfc/reference/clistview-class.md)<br/>
Zobrazení, které obsahuje ovládací prvek seznamu systému Windows (viz [CListCtrl](../mfc/reference/clistctrl-class.md)). Ovládací prvek seznam zobrazuje ikony a řetězce podobným způsobem jako v pravém podokně Průzkumníka souborů.

[CTreeView –](../mfc/reference/ctreeview-class.md)<br/>
Zobrazení, které obsahuje ovládací prvek stromu systému Windows (viz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Ovládací prvek stromu zobrazuje ikony a řetězce uspořádané v hierarchii způsobem podobným levému podoknu Průzkumníka souborů.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
