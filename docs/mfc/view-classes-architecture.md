---
title: "Zobrazí třídy (Architektura) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.view
dev_langs: C++
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b2761253da0907b1736754068fa196dda361a8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="view-classes-architecture"></a>Třídy zobrazení (architektura)
`CView`a jejich odvozené třídy jsou podřízená okna, které představují klientské oblasti okně s rámečkem. Zobrazení zobrazit data a přijímat vstup pro dokument.  
  
 Třídy zobrazení je přidružen dokumentové třídy a třídy oken s rámečkem pomocí objektu šablony dokumentu.  
  
 [CView](../mfc/reference/cview-class.md)  
 Základní třída pro konkrétní aplikace zobrazení dat dokumentu. Zobrazení zobrazovat data a přijímají vstup uživatele, které chcete upravit, nebo vyberte data. Odvození třídy vaše zobrazení z `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 Základní třída pro zobrazení s možností posouvání. Odvození třídě zobrazení z `CScrollView` pro automatické posouvání.  
  
## <a name="form-and-record-views"></a>Formulář a zobrazení záznamů  
 Zobrazení formulářů jsou také posouvání zobrazení. Jsou založené na pole šablony dialogového okna.  
  
 Zobrazení záznamů jsou odvozeny od zobrazení formulářů. Kromě pole šablony dialogového okna mají taky připojení k databázi.  
  
 [Třídy CFormView](../mfc/reference/cformview-class.md)  
 Posuňte zobrazení, jejichž rozložení je definována v poli šablony dialogového okna. Odvození třídy z `CFormView` implementovat uživatelské rozhraní založené na pole šablony dialogového okna.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů objekt DAO (Data Access). Jako všechna zobrazení formuláře `CDaoRecordView` je založená na šabloně dialogové okno pole.  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 Podporuje ovládací prvek pro procházení webu v rámci aplikace. Ovládací prvek podporuje dynamické HTML v prostředí MFC.  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 Poskytuje podporu MFC OLE DB pro zobrazení formulářů.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů připojení ODBC (Open Database). Jako všechna zobrazení formuláře `CRecordView` je založená na šabloně dialogové okno pole.  
  
## <a name="control-views"></a>Zobrazení ovládacích prvků  
 Zobrazení ovládacích prvků zobrazení ovládacího prvku jako jejich zobrazení.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Základní třída pro všechna zobrazení související s ovládacími prvky systému Windows. Zobrazení založená na ovládací prvky jsou popsané níže.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Zobrazení, který obsahuje standardní Windows ovládacích prvků pro úpravy (viz [CEdit](../mfc/reference/cedit-class.md)). Upravte úpravy textu podporu ovládací prvky, hledání, nahraďte a posouvání možnosti.  
  
 [Cricheditview –](../mfc/reference/cricheditview-class.md)  
 Zobrazení, který obsahuje bohatou Windows ovládacích prvků pro úpravy (viz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Kromě možností ovládacích prvků pro úpravy upravte bohaté ovládací prvky písma, barvy, formátování odstavce a vložené objekty OLE.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Zobrazení, který obsahuje seznam ovládacího prvku Windows (viz [CListCtrl](../mfc/reference/clistctrl-class.md)). Ovládací prvek seznamu zobrazí ikony a řetězce v pravém podokně podobným způsobem v Průzkumníku souborů.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Zobrazení, které obsahuje ovládacím prvkem strom systému Windows (viz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Ovládací prvek stromu zobrazí ikony a řetězce, které jsou uspořádány do hierarchie v levém podokně podobným způsobem v Průzkumníku souborů.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

