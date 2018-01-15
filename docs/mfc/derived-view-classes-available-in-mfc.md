---
title: "Odvozené třídy zobrazení dostupné v prostředí MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2426f3e547da6eaab6a4b38bb5199e87c93ef933
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="derived-view-classes-available-in-mfc"></a>Odvozené třídy zobrazení dostupné v prostředí MFC
Následující tabulka uvádí třídy MFC na zobrazení a jejich vzájemných vztahů. Možnosti zobrazení třídy závisí na třídy MFC zobrazení, ze kterého pochází.  
  
### <a name="view-classes"></a>Třídy zobrazení  
  
|Třída|Popis|  
|-----------|-----------------|  
|[CView](../mfc/reference/cview-class.md)|Základní třída všech zobrazení.|  
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Základní třída `CTreeView`, `CListView`, `CEditView`, a `CRichEditView`. Tyto třídy umožňují používat document/view – architektura s uvedené běžné ovládací prvky Windows.|  
|[CEditView](../mfc/reference/ceditview-class.md)|Pole ovládacích prvků pro úpravy jednoduché zobrazení založeného na systému Windows. Umožňuje zadávání a úpravy textu a může sloužit jako základ pro jednoduchý textový editor aplikace. Viz také `CRichEditView`.|  
|[Cricheditview –](../mfc/reference/cricheditview-class.md)|Zobrazení obsahující [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) objektu. Tato třída je obdobou `CEditView`, ale na rozdíl od `CEditView`, `CRichEditView` popisovače formátovaného textu.|  
|[CListView](../mfc/reference/clistview-class.md)|Zobrazení obsahující [CListCtrl](../mfc/reference/clistctrl-class.md) objektu.|  
|[CTreeView](../mfc/reference/ctreeview-class.md)|Zobrazení obsahující [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt, pro zobrazení, které se podobají okno Průzkumník řešení v jazyce Visual C++.|  
|[CScrollView](../mfc/reference/cscrollview-class.md)|Základní třída `CFormView`, `CRecordView`, a `CDaoRecordView`. Implementuje posouvání obsah zobrazení.|  
|[Třídy CFormView](../mfc/reference/cformview-class.md)|Zobrazení formuláře, zobrazení, která obsahuje ovládací prvky. Formulářové aplikace obsahuje jeden nebo více těchto formuláře rozhraní.|  
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Zobrazení webové prohlížeče, se kterým uživatel aplikace můžete procházet weby na webu, jakož i složky v místním systému souborů a v síti. Webové prohlížeče zobrazení může spolupracovat taky jako kontejner pro aktivní dokument.|  
|[CRecordView](../mfc/reference/crecordview-class.md)|Zobrazení formuláře, které zobrazí záznamů rozhraní ODBC databáze v ovládacích prvcích. Pokud vyberete podpora rozhraní ODBC do projektu, zobrazení základní třída má `CRecordView`. Zobrazení je připojený k `CRowset` objektu.|  
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Zobrazení formuláře, které zobrazí záznamů rozhraní DAO databáze v ovládacích prvcích. Pokud vyberete rozhraní DAO podporu ve vašem projektu, zobrazení základní třída má `CDaoRecordView`. Zobrazení je připojený k `CDaoRecordset` objektu.|  
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Formulář zobrazení záznamů technologie OLE DB v ovládacích prvcích. Pokud vyberete podporu technologie OLE DB ve vašem projektu, zobrazení základní třída má `COleDBRecordView`. Zobrazení je připojený k `CRowset` objektu.|  
  
> [!NOTE]
>  Od verze knihovny MFC verze 4.0 `CEditView` je odvozený od `CCtrlView`.  
  
 K použití těchto tříd ve vaší aplikaci, odvozovat aplikace zobrazení z nich. Související informace najdete v tématu [posouvání a změna měřítka zobrazení](../mfc/scrolling-and-scaling-views.md). Další informace o databázové třídy najdete v tématu [přehled: programování databáze](../data/data-access-programming-mfc-atl.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití zobrazení](../mfc/using-views.md)

