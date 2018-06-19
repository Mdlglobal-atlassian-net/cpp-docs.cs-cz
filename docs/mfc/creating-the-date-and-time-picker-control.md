---
title: Vytvoření ovládacího prvku datum a čas výběr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce7c987bf1284d0287cd0206572209d7ae2d0b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342131"
---
# <a name="creating-the-date-and-time-picker-control"></a>Vytvoření ovládacího prvku pro výběr data a času
Vytváření prvku pro výběr data a času závisí na tom, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo jeho vytváření v okně nondialog.  
  
### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Chcete-li použít CDateTimeCtrl přímo v dialogovém okně  
  
1.  V editoru dialogového okna přidáte do vaší prostředku šablony dialogového okna datum a čas ovládací prvek pro výběr. Zadejte své ID ovládacího prvku.  
  
2.  Zadejte všechny styly potřeby pomocí dialogového okna Vlastnosti prvku pro výběr data a času.  
  
3.  Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidání členské proměnné typu [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) s vlastností ovládacího prvku. Tento člen mohou využít k volání `CDateTimeCtrl` členské funkce.  
  
4.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce v třídy dialogového okna pro ovládací prvek výběru žádné datum čas [oznámení](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) zprávy, které je potřeba zpracovat (najdete v části [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení pro všechny další stylů `CDateTimeCtrl` objektu.  
  
### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>V okně nondialog používat CDateTimeCtrl  
  
1.  Deklarujte ovládacího prvku ve třídě zobrazení nebo okno.  
  
2.  Volání ovládacího prvku [vytvořit](../mfc/reference/ctabctrl-class.md#create) člen funkce, které by mohly mít v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), pravděpodobně časná jako nadřazeného okna [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkce obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

