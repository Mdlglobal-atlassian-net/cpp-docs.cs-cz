---
title: "Vytvoření ovládacího prvku rozšířené pole se seznamem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96903fabd5ec0a0cff4d55eb97e7d06271b79990
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-extended-combo-box-control"></a>Vytvoření ovládacího prvku rozšířené pole se seznamem
Vytvoření ovládacího prvku rozšířené pole se seznamem pole závisí na tom, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo jeho vytváření v okně nondialog.  
  
### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Chcete-li použít CComboBoxEx přímo v dialogovém okně  
  
1.  V editoru dialogového okna přidáte do šablony zdroje dialogové okno ovládacího prvku rozšířené pole se seznamem. Zadejte své ID ovládacího prvku.  
  
2.  Zadejte všechny styly potřeby pomocí dialogového okna vlastnosti ovládacího prvku rozšířené pole se seznamem.  
  
3.  Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidání členské proměnné typu [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) s vlastností ovládacího prvku. Tento člen mohou využít k volání `CComboBoxEx` členské funkce.  
  
4.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog zprávy oznámení ovládacího prvku pole rozšířeného pole se seznamem je potřeba zpracovat (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení pro všechny další stylů `CComboBoxEx` objektu.  
  
### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>V okně nondialog používat CComboBoxEx  
  
1.  Definování ovládacího prvku ve třídě zobrazení nebo okno.  
  
2.  Volání ovládacího prvku [vytvořit](../mfc/reference/ctabctrl-class.md#create) člen funkce, které by mohly mít v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), pravděpodobně časná jako nadřazeného okna [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkce obslužné rutiny. Nastavení stylů pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

