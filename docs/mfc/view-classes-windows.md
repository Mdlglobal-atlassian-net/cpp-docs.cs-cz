---
title: "Zobrazí třídy (Windows) | Microsoft Docs"
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
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0148ead7a978389f763efbe9ee6306ec7a5839cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="view-classes-windows"></a>Třídy zobrazení (Windows)
`CView`a jejich odvozené třídy jsou podřízená okna, které představují klientské oblasti okně s rámečkem. Zobrazení zobrazit data a přijímat vstup pro dokument.  
  
 Třídy zobrazení je přidružen dokumentové třídy a třídy oken s rámečkem pomocí objektu šablony dokumentu.  
  
 [CView](../mfc/reference/cview-class.md)  
 Základní třída pro konkrétní aplikace zobrazení dat dokumentu. Zobrazení zobrazovat data a přijímají vstup uživatele, které chcete upravit, nebo vyberte data. Odvození třídy zobrazení nebo třídy z `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 Základní třída pro zobrazení s možností posouvání. Odvození třídě zobrazení z `CScrollView` pro automatické posouvání.  
  
## <a name="form-and-record-views"></a>Formulář a zobrazení záznamů  
 Zobrazení formulářů jsou také posouvání zobrazení. Jsou založené na pole šablony dialogového okna.  
  
 Zobrazení záznamů jsou odvozeny od zobrazení formulářů. Kromě pole šablony dialogového okna mají taky připojení k databázi.  
  
 [Třídy CFormView](../mfc/reference/cformview-class.md)  
 Posuňte zobrazení, jejichž rozložení je definována v poli šablony dialogového okna. Odvození třídy z `CFormView` implementovat uživatelské rozhraní založené na pole šablony dialogového okna.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů objekt DAO (Data Access). Jako všechna zobrazení formuláře `CDaoRecordView` je založená na šabloně dialogové okno pole.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů připojení ODBC (Open Database). Jako všechna zobrazení formuláře `CRecordView` je založená na šabloně dialogové okno pole.  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 Zobrazení formuláře, které poskytuje funkce úpravy platformy WebBrowser HTML.  
  
## <a name="control-views"></a>Zobrazení ovládacích prvků  
 Zobrazení ovládacích prvků zobrazení ovládacího prvku jako jejich zobrazení.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 Základní třída pro všechna zobrazení související s ovládacími prvky systému Windows. Zobrazení založená na ovládací prvky jsou popsané níže.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Zobrazení, který obsahuje standardní Windows ovládacích prvků pro úpravy (viz [CEdit](../mfc/reference/cedit-class.md)). Upravte úpravy textu podporu ovládací prvky, hledání, nahraďte a posouvání možnosti.  
  
 [Cricheditview –](../mfc/reference/cricheditview-class.md)  
 Zobrazení, který obsahuje bohatou Windows ovládacích prvků pro úpravy (viz [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Kromě možností ovládacích prvků pro úpravy upravte bohaté ovládací prvky písma, barvy, formátování odstavce a vložené objekty OLE.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Zobrazení, který obsahuje seznam ovládacího prvku Windows (viz [CListCtrl](../mfc/reference/clistctrl-class.md)). Ovládací prvek seznamu zobrazí kolekce položek, každý se skládá z ikonu a štítku, v pravém podokně podobným způsobem v Průzkumníku souborů.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Zobrazení, které obsahuje ovládacím prvkem strom systému Windows (viz [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Ovládací prvek stromu zobrazí hierarchické seznam ikon a popisky uspořádané podobným způsobem, v levém podokně v Průzkumníku souborů.  
  
## <a name="related-classes"></a>Související třídy  
 `CSplitterWnd`Můžete mít více zobrazení v rámci jedné rámce okna. `CPrintDialog`a `CPrintInfo` kvůli podpoře možnosti tisku a tiskového náhledu zobrazení. `CRichEditDoc`a `CRichEditCntrItem` se používají s `CRichEditView` implementovat možnosti kontejneru OLE.  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 Okno, které uživatel můžete rozdělit do několika podoken. Tyto podokna může být umožňující změnu velikosti uživatelem nebo pevné velikosti.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Poskytuje standardní dialogové okno pro tisk souboru.  
  
 [Cprintinfo –](../mfc/reference/cprintinfo-structure.md)  
 Struktura obsahující informace o úloze nebo tiskového náhledu. Používá `CView`je tisk architektura.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Udržuje seznam položek OLE klienta, které jsou v `CRichEditView`.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Poskytuje klientský přístup k položky uložené v OLE `CRichEditView`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

