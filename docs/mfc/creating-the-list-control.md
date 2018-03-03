---
title: "Vytvoření ovládacího prvku seznam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85afbe49943e06a66cf2fa914cc87f07b0fa8c52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-list-control"></a>Vytvoření ovládacího prvku seznam
Jak řídit seznamu ([CListCtrl](../mfc/reference/clistctrl-class.md)) je vytvořen závisí na tom, jestli jste pomocí ovládacího prvku přímo nebo pomocí třídy [CListView](../mfc/reference/clistview-class.md) místo. Pokud používáte `CListView`, rozhraní framework vytvoří zobrazení v rámci jeho pořadí vytváření dokumentů/zobrazení. Vytváření zobrazení seznamu vytvoří ovládacího prvku seznam také (dva jsou samé). Ovládací prvek je vytvořen v zobrazení [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkce obslužné rutiny. V takovém případě je připraven k přidání položky prostřednictvím volání do ovládacího prvku [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).  
  
### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>K použití přímo v dialogovém okně CListCtrl  
  
1.  V editoru dialogového okna přidáte do šablony zdroje dialogové okno Ovládací prvek seznamu. Zadejte své ID ovládacího prvku.  
  
2.  Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidání členské proměnné typu `CListCtrl` s vlastností ovládacího prvku. Tento člen mohou využít k volání `CListCtrl` členské funkce.  
  
3.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládacího prvku seznam zpráv, které můžete potřebovat pro zpracování (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
4.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení stylů pro `CListCtrl`. V tématu [změna stylů ovládacího prvku seznam](../mfc/changing-list-control-styles.md). Tato hodnota určuje druh "Zobrazit" získání v ovládacím prvku, i když můžete později změnit zobrazení.  
  
### <a name="to-use-clistctrl-in-a-nondialog-window"></a>V okně nondialog používat CListCtrl  
  
1.  Definování ovládacího prvku ve třídě zobrazení nebo okno.  
  
2.  Volání ovládacího prvku [vytvořit](../mfc/reference/clistctrl-class.md#create) člen funkce, které by mohly mít v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), pravděpodobně časná jako nadřazeného okna [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkce obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

