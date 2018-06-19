---
title: Ovládací prvek seznamu a zobrazení seznamu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3279ae5edc02ec52ded065c4a45d18e3236802f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345996"
---
# <a name="list-control-and-list-view"></a>Ovládací prvek seznamu a zobrazení seznamu
Pro usnadnění práce zapouzdří MFC ovládacího prvku seznam dvěma způsoby. Můžete použít ovládací prvky seznamu:  
  
-   Přímo, vložením [CListCtrl](../mfc/reference/clistctrl-class.md) objekt ve třídě dialog.  
  
-   Nepřímo, s použitím třídy [CListView](../mfc/reference/clistview-class.md).  
  
 `CListView` umožňuje snadno integrovat ovládací prvek seznamu architektuře dokument/zobrazení MFC zapouzdřením ovládacího prvku mnohem jako [CEditView](../mfc/reference/ceditview-class.md) zapouzdří ovládací prvek upravit: ovládací prvek vyplní celé plochy zobrazení knihovny MFC. (Zobrazení *je* prvku přetypovat `CListView`.)  
  
 A `CListView` objekt dědí z [CCtrlView](../mfc/reference/cctrlview-class.md) a jeho základní třídy a přidá členské funkce načíst základní ovládací prvek seznamu. Pomocí zobrazení členů pro práci s zobrazení jako zobrazení. Použití [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) – členská funkce k získání přístupu k členské funkce ovládacího prvku seznam. Pomocí těchto členů na:  
  
-   Přidat, odstranit nebo upravit "položky" v seznamu.  
  
-   Nastavit nebo získat atributy ovládacího prvku seznam.  
  
 Chcete-li získat odkaz na `CListCtrl` základní `CListView`, volání `GetListCtrl` z vaší třídy zobrazení seznamu:  
  
 [!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]  
  
 Toto téma popisuje oba způsoby použití ovládacího prvku seznam.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

