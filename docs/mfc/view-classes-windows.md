---
title: Třídy zobrazení (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: ad58fd6fa2548c2cf320baf75b8fc33a835ddd55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296615"
---
# <a name="view-classes-windows"></a>Třídy zobrazení (Windows)

`CView` a odvozené třídy jsou podřízených oken, které představují klientské oblasti okna rámce. Zobrazení zobrazit data a přijímat vstup pro dokument.

Zobrazit třídu souvisí s dokumentové třídy a použití objektu šablony dokumentu třídy oken s rámečkem.

[CView](../mfc/reference/cview-class.md)<br/>
Základní třída pro zobrazení specifické pro aplikace z dat dokumentu. Zobrazení zobrazovat data a přijímat uživatelský vstup pro úpravy nebo vyberte data. Zobrazit třídu nebo třídy z `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Základní třída pro zobrazení s možností posouvání. Odvodit třídu vaše zobrazení z `CScrollView` pro automatické posouvání.

## <a name="form-and-record-views"></a>Formuláře a zobrazení záznamů

Zobrazení formuláře jsou také posouvání zobrazení. Jsou založeny na šablony dialogového okna.

Zobrazení záznamů jsou odvozeny z zobrazení formuláře. Kromě šablony dialogového okna mají taky připojení k databázi.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Posunout zobrazení, jejichž rozložení je definován v šabloně dialogu pole. Odvodit třídu z `CFormView` k implementaci uživatelského rozhraní založené na šablony dialogového okna.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů objekt DAO (Data Access). Všechna zobrazení formulářů, jako jsou `CDaoRecordView` je založen na šabloně dialogu pole.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů připojení ODBC (Open Database). Všechna zobrazení formulářů, jako jsou `CRecordView` je založen na šabloně dialogu pole.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Zobrazení formuláře, které poskytuje funkce úprav platformy WebBrowser HTML.

## <a name="control-views"></a>Zobrazení ovládacích prvků

Ovládací prvek zobrazení ovládacího prvku jako jejich zobrazení.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Základní třída pro všechna zobrazení související s ovládacími prvky Windows. Zobrazení založená na ovládací prvky jsou popsané níže.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Zobrazení, která obsahuje standardní Windows ovládacích prvků pro úpravy (viz [CEdit](../mfc/reference/cedit-class.md)). Upravte úpravy textu podpora ovládacích prvků, vyhledávání, nahrazení a možností posouvání.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Zobrazení, které obsahuje Windows bohatých ovládacích prvků pro úpravy (viz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Kromě funkcí textové pole pro úpravy s formátováním ovládací prvky písma, barvy, formátování odstavce a vložené objekty OLE.

[CListView](../mfc/reference/clistview-class.md)<br/>
Zobrazení, která obsahuje ovládací prvek seznamu Windows (viz [CListCtrl](../mfc/reference/clistctrl-class.md)). Ovládací prvek seznamu zobrazí kolekci položek, každá se skládá z ikony a jmenovku do pravého podokna podobným způsobem v Průzkumníku souborů.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Zobrazení, která obsahuje ovládací prvek stromu Windows (viz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Ovládacím prvkem Strom zobrazuje hierarchické seznam ikony a popisky, které jsou uspořádány do levého podokna podobným způsobem v Průzkumníku souborů.

## <a name="related-classes"></a>Související třídy

`CSplitterWnd` Můžete mít více zobrazení okna jeden snímek. `CPrintDialog` a `CPrintInfo` kvůli podpoře možnosti tisku a tiskového náhledu zobrazení. `CRichEditDoc` a `CRichEditCntrItem` produkty slouží spolu s `CRichEditView` implementovat možnosti pro kontejnery OLE.

[CSplitterWnd.](../mfc/reference/csplitterwnd-class.md)<br/>
Okno, které můžete uživatele rozdělit do několika podoken. Těchto podoken můžete vizualizaci může být umožňující změnu velikosti uživatelem nebo pevnou velikostí.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Poskytuje standardní dialogové okno pro tisk souboru.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Struktury obsahující informace o úloze tisku nebo náhledu tisku. Používá `CView`je tisk architektury.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Udržuje seznam klientské položky OLE, které jsou v `CRichEditView`.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Poskytuje přístup na straně klienta OLE položky uložené v `CRichEditView`.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
