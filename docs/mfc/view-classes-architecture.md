---
title: Třídy zobrazení (architektura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: 15b120f0354c483480351b8d3abf995334779411
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299410"
---
# <a name="view-classes-architecture"></a>Třídy zobrazení (architektura)

`CView` a odvozené třídy jsou podřízených oken, které představují klientské oblasti okna rámce. Zobrazení zobrazit data a přijímat vstup pro dokument.

Zobrazit třídu souvisí s dokumentové třídy a použití objektu šablony dokumentu třídy oken s rámečkem.

[CView](../mfc/reference/cview-class.md)<br/>
Základní třída pro zobrazení specifické pro aplikace z dat dokumentu. Zobrazení zobrazovat data a přijímat uživatelský vstup pro úpravy nebo vyberte data. Odvození třídy, které vaše zobrazení z `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Základní třída pro zobrazení s možností posouvání. Odvodit třídu vaše zobrazení z `CScrollView` pro automatické posouvání.

## <a name="form-and-record-views"></a>Formuláře a zobrazení záznamů

Zobrazení formuláře jsou také posouvání zobrazení. Jsou založeny na šablony dialogového okna.

Zobrazení záznamů jsou odvozeny z zobrazení formuláře. Kromě šablony dialogového okna mají taky připojení k databázi.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Posunout zobrazení, jejichž rozložení je definován v šabloně dialogu pole. Odvodit třídu z `CFormView` k implementaci uživatelského rozhraní založené na šablony dialogového okna.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů objekt DAO (Data Access). Všechna zobrazení formulářů, jako jsou `CDaoRecordView` je založen na šabloně dialogu pole.

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
Podporuje ovládací prvek pro procházení webu v rámci aplikace. Ovládací prvek podporuje dynamické HTML v MFC.

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
Poskytuje podporu knihovny MFC OLE DB pro zobrazení formuláře.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů připojení ODBC (Open Database). Všechna zobrazení formulářů, jako jsou `CRecordView` je založen na šabloně dialogu pole.

## <a name="control-views"></a>Zobrazení ovládacích prvků

Ovládací prvek zobrazení ovládacího prvku jako jejich zobrazení.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Základní třída pro všechna zobrazení související s ovládacími prvky Windows. Zobrazení založená na ovládací prvky jsou popsané níže.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Zobrazení, která obsahuje standardní Windows ovládacích prvků pro úpravy (viz [CEdit](../mfc/reference/cedit-class.md)). Upravte úpravy textu podpora ovládacích prvků, vyhledávání, nahrazení a možností posouvání.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Zobrazení, které obsahuje Windows bohatých ovládacích prvků pro úpravy (viz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Kromě funkcí textové pole pro úpravy s formátováním ovládací prvky písma, barvy, formátování odstavce a vložené objekty OLE.

[CListView](../mfc/reference/clistview-class.md)<br/>
Zobrazení, která obsahuje ovládací prvek seznamu Windows (viz [CListCtrl](../mfc/reference/clistctrl-class.md)). Ovládací prvek seznamu zobrazuje ikony a řetězce do pravého podokna podobným způsobem v Průzkumníku souborů.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Zobrazení, která obsahuje ovládací prvek stromu Windows (viz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Ovládací prvek stromu se zobrazí ikony a řetězce, které jsou uspořádány do hierarchie do levého podokna podobným způsobem v Průzkumníku souborů.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
