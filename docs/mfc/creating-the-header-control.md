---
title: "Vytvoření ovládacího prvku záhlaví | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c47e458d4cd6e9df556eef5e1f61806633208011
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-header-control"></a>Vytvoření ovládacího prvku záhlaví
Ovládací prvek záhlaví není přímo k dispozici v editoru dialogových oken (i když můžete přidat ovládací prvek seznamu, který zahrnuje ovládacím prvkem záhlaví).  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>V dialogovém okně uvést ovládacího prvku záhlaví  
  
1.  Ručně vložit členské proměnné typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) ve vlastní třídy dialogového okna.  
  
2.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), vytvoření a nastavení stylů pro `CHeaderCtrl`, umístěte ho a jejich zobrazení.  
  
3.  Přidání položek do ovládacího prvku záhlaví.  
  
4.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládacího prvku záhlaví zprávy je zapotřebí zpracovat (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Umístění ovládacího prvku záhlaví v zobrazení (není CListView)  
  
1.  Vložení [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objekt ve třídě zobrazení.  
  
2.  Styl, pozice a zobrazit okno ovládacího prvku záhlaví v zobrazení [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) – členská funkce.  
  
3.  Přidání položek do ovládacího prvku záhlaví.  
  
4.  Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě zobrazení pro všechna oznámení ovládacího prvku záhlaví zprávy je zapotřebí zpracovat (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
 V obou případech je vytvořen objekt vloženému ovládacímu prvku, když je vytvořen objekt zobrazení nebo dialogové okno. Pak musí volat [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) vytvořit okno pro řízení. Chcete-li umístění ovládacího prvku, volejte [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) k určení počáteční velikost a umístění ovládacího prvku a [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) nastavit požadované místo. Pak přidat položky, jak je popsáno v [přidávání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).  
  
 Další informace najdete v tématu [vytvoření ovládacího prvku záhlaví](http://msdn.microsoft.com/library/windows/desktop/bb775238) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

