---
title: Vytvoření ovládacího prvku záhlaví | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18517f969dc64b0c1d9a51bcdc67a1655ec82d7c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214006"
---
# <a name="creating-the-header-control"></a>Vytvoření ovládacího prvku záhlaví
Ovládacího prvku záhlaví není k dispozici přímo v editoru dialogových oken (i když můžete přidat ovládací prvek seznamu, který obsahuje ovládací prvek záhlaví).  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>V dialogovém okně Vložit ovládacím prvkem záhlaví  
  
1.  Ručně vložit členské proměnné typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) ve vlastní třídy dialogového okna.  
  
2.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), vytvoření a nastavení stylů `CHeaderCtrl`, polohy a zobrazit je.  
  
3.  Přidání položek do ovládacího prvku záhlaví.  
  
4.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládacího prvku záhlaví zprávy je potřeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Vložit ovládací prvek záhlaví v zobrazení (nikoli CListView)  
  
1.  Vložit [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objekt ve třídě zobrazení.  
  
2.  Styl, pozice a zobrazit okno Ovládací prvek záhlaví v zobrazení [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) členskou funkci.  
  
3.  Přidání položek do ovládacího prvku záhlaví.  
  
4.  Použití mapování obslužné rutiny funkce ve třídě zobrazení pro všechna oznámení ovládacího prvku záhlaví zprávy v okně Vlastnosti potřeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).  
  
 V obou případech se vytvoří vloženému ovládacímu prvku objektu při vytvoření objektu zobrazení nebo dialogového okna. Pak je nutné volat [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) vytvořit okno ovládacího prvku. Pro umístění ovládacího prvku, volejte [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) určíte, počáteční velikost a pozice ovládacího prvku a [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) pozice chcete nastavit. Pak přidejte položky, jak je popsáno v [přidávání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).  
  
 Další informace najdete v tématu [vytvoření ovládacího prvku záhlaví](/windows/desktop/Controls/header-controls) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

