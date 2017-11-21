---
title: "Ovládací prvek seznamu a zobrazení seznamu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 893ff83067c2a7fbc6c375dd6ee03248114ca5ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="list-control-and-list-view"></a>Ovládací prvek seznamu a zobrazení seznamu
Pro usnadnění práce zapouzdří MFC ovládacího prvku seznam dvěma způsoby. Můžete použít ovládací prvky seznamu:  
  
-   Přímo, vložením [CListCtrl](../mfc/reference/clistctrl-class.md) objekt ve třídě dialog.  
  
-   Nepřímo, s použitím třídy [CListView](../mfc/reference/clistview-class.md).  
  
 `CListView`umožňuje snadno integrovat ovládací prvek seznamu architektuře dokument/zobrazení MFC zapouzdřením ovládacího prvku mnohem jako [CEditView](../mfc/reference/ceditview-class.md) zapouzdří ovládací prvek upravit: ovládací prvek vyplní celé plochy zobrazení knihovny MFC. (Zobrazení *je* prvku přetypovat `CListView`.)  
  
 A `CListView` objekt dědí z [CCtrlView](../mfc/reference/cctrlview-class.md) a jeho základní třídy a přidá členské funkce načíst základní ovládací prvek seznamu. Pomocí zobrazení členů pro práci s zobrazení jako zobrazení. Použití [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) – členská funkce k získání přístupu k členské funkce ovládacího prvku seznam. Pomocí těchto členů na:  
  
-   Přidat, odstranit nebo upravit "položky" v seznamu.  
  
-   Nastavit nebo získat atributy ovládacího prvku seznam.  
  
 Chcete-li získat odkaz na `CListCtrl` základní `CListView`, volání `GetListCtrl` z vaší třídy zobrazení seznamu:  
  
 [!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]  
  
 Toto téma popisuje oba způsoby použití ovládacího prvku seznam.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

