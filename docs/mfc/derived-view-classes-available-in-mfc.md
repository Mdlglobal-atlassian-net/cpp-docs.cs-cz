---
title: Odvozené třídy zobrazení dostupné v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 61b38f6147a8bde4f6eb42cd144f9f64dac8dbd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152901"
---
# <a name="derived-view-classes-available-in-mfc"></a>Odvozené třídy zobrazení dostupné v prostředí MFC

V následující tabulce jsou uvedeny zobrazení tříd knihovny MFC a jejich vztahy mezi sebou. Možnosti zobrazení třídy závisí na zobrazení třídy knihovny MFC, ze kterého pochází.

### <a name="view-classes"></a>Třídy zobrazení

|Třída|Popis|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Základní třída všech zobrazení.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Základní třída `CTreeView`, `CListView`, `CEditView`, a `CRichEditView`. Tyto třídy umožňují použít architekturu document/view s uvedené běžné ovládací prvky Windows.|
|[CEditView](../mfc/reference/ceditview-class.md)|Zobrazení založené Windows na jednoduché upravit ovládací prvek pole. Umožňuje zadávat a upravovat text a může sloužit jako základ pro aplikace jednoduchý textový editor. Viz také `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Zobrazit obsahující [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) objektu. Tato třída je obdobou `CEditView`, ale na rozdíl od `CEditView`, `CRichEditView` obslužné rutiny formátovaného textu.|
|[CListView](../mfc/reference/clistview-class.md)|Zobrazit obsahující [CListCtrl](../mfc/reference/clistctrl-class.md) objektu.|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Zobrazit obsahující [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objektu pro zobrazení, které se podobají okna Průzkumník řešení v jazyce Visual C++.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Základní třída `CFormView`, `CRecordView`, a `CDaoRecordView`. Implementuje posouvání obsah zobrazení.|
|[CFormView](../mfc/reference/cformview-class.md)|Zobrazení formuláře, zobrazení, která obsahuje ovládací prvky. Aplikace založené na formulářích obsahuje jeden nebo více těchto formuláře rozhraní.|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Zobrazení webového prohlížeče pomocí kterého uživatelé aplikace můžou procházet webů na webu, jakož i složky v místním systému souborů a v síti. Ve webovém prohlížeči zobrazení může spolupracovat také jako kontejner pro aktivní dokument.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Zobrazení formuláře, které zobrazuje záznamy databáze ODBC v ovládacích prvcích. Pokud vyberete podpora rozhraní ODBC ve vašem projektu, v zobrazení základní třída je `CRecordView`. Zobrazení je připojen k `CRowset` objektu.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Zobrazení formuláře, které zobrazuje záznamy databáze DAO v ovládacích prvcích. Pokud vyberete rozhraní DAO podpory ve vašem projektu, v zobrazení základní třída je `CDaoRecordView`. Zobrazení je připojen k `CDaoRecordset` objektu.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Formulářové zobrazení záznamů technologie OLE DB zobrazuje v ovládacích prvcích. Pokud vyberete podporu technologie OLE DB ve vašem projektu, v zobrazení základní třída je `COleDBRecordView`. Zobrazení je připojen k `CRowset` objektu.|

> [!NOTE]
>  Od verze knihovny MFC verze 4.0 `CEditView` je odvozen z `CCtrlView`.

K použití těchto tříd ve vaší aplikaci, odvozovat z nich třídy zobrazení vaší aplikace. Související informace naleznete v tématu [posouvání a změna měřítka zobrazení](../mfc/scrolling-and-scaling-views.md). Další informace o databázových tříd naleznete v tématu [přehled: Databáze programování](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Viz také:

[Použití zobrazení](../mfc/using-views.md)
