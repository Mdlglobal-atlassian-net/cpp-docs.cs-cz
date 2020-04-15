---
title: Odvozené třídy zobrazení dostupné v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373505"
---
# <a name="derived-view-classes-available-in-mfc"></a>Odvozené třídy zobrazení dostupné v prostředí MFC

V následující tabulce jsou uvedeny třídy zobrazení knihovny MFC a jejich vzájemné vztahy. Možnosti třídy zobrazení závisí na třídě zobrazení knihovny MFC, ze které je odvozena.

### <a name="view-classes"></a>Zobrazit třídy

|Třída|Popis|
|-----------|-----------------|
|[Cview](../mfc/reference/cview-class.md)|Základní třída všech zobrazení.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Základní třída `CTreeView` `CListView`, `CEditView`, `CRichEditView`a . Tyto třídy umožňují používat architekturu dokumentu nebo zobrazení s uvedenými běžnými ovládacími prvky systému Windows.|
|[Zobrazení CEdit](../mfc/reference/ceditview-class.md)|Jednoduché zobrazení založené na ovládacím prvku editačního rámečku systému Windows. Umožňuje zadávání a editaci textu a může být použit jako základ pro jednoduchou aplikaci textového editoru. Viz `CRichEditView`také .|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Zobrazení obsahující objekt [CRichEditCtrl.](../mfc/reference/cricheditctrl-class.md) Tato třída je obdobou `CEditView`, `CEditView` `CRichEditView` ale na rozdíl od , zpracovává formátovaný text.|
|[Zobrazení CList](../mfc/reference/clistview-class.md)|Zobrazení obsahující objekt [CListCtrl.](../mfc/reference/clistctrl-class.md)|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Zobrazení obsahující objekt [CTreeCtrl](../mfc/reference/ctreectrl-class.md) pro zobrazení, která se podobají oknu Průzkumníka řešení v jazyce Visual C++.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Základní třída `CFormView` `CRecordView`, `CDaoRecordView`a . Implementuje posouvání obsahu zobrazení.|
|[Cformview](../mfc/reference/cformview-class.md)|Formulářové zobrazení, zobrazení, které obsahuje ovládací prvky. Aplikace založená na formulářích poskytuje jedno nebo více takových rozhraní formuláře.|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Zobrazení webového prohlížeče, pomocí kterého může uživatel aplikace procházet weby na webu a také složky v místním systému souborů a v síti. Zobrazení webového prohlížeče může také fungovat jako kontejner aktivního dokumentu.|
|[Crecordview](../mfc/reference/crecordview-class.md)|Zobrazení formuláře, které zobrazuje záznamy databáze ODBC v ovládacích prvcích. Pokud v projektu vyberete podporu ROZHRANÍ ODBC, `CRecordView`základní třída zobrazení je . Pohled je připojen `CRowset` k objektu.|
|[Cdaorecordview](../mfc/reference/cdaorecordview-class.md)|Zobrazení formuláře, které zobrazuje záznamy databáze DAO v ovládacích prvcích. Pokud vyberete podporu DAO v projektu, základní `CDaoRecordView`třída zobrazení je . Pohled je připojen `CDaoRecordset` k objektu.|
|[Coledbrecordview](../mfc/reference/coledbrecordview-class.md)|Zobrazení formuláře, které zobrazuje záznamy TECHNOLOGIE OLE DB v ovládacích prvcích. Pokud vyberete podporu TECHNOLOGIE OLE DB v projektu, `COleDBRecordView`základní třída zobrazení je . Pohled je připojen `CRowset` k objektu.|

> [!NOTE]
> Od knihovny MFC verze `CEditView` 4.0 `CCtrlView`je odvozen od .

Chcete-li použít tyto třídy v aplikaci, odvodit třídy zobrazení aplikace z nich. Související informace naleznete v [tématu Posouvání a škálování zobrazení](../mfc/scrolling-and-scaling-views.md). Další informace o třídách databáze naleznete v [tématu Přehled: Programování databáze](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Viz také

[Použití zobrazení](../mfc/using-views.md)
