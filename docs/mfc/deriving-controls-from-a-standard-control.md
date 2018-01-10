---
title: "Odvozování ovládacích prvků ze standardního ovládacího prvku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b93bc07fc5ab4680caaa276daaeca86189b8ce5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deriving-controls-from-a-standard-control"></a>Odvozování ovládacích prvků ze standardního ovládacího prvku
Stejně jako u některé [CWnd](../mfc/reference/cwnd-class.md)-odvozené třídy, můžete upravit chování ovládacího prvku odvozením novou třídu z existující třídy ovládacího prvku.  
  
### <a name="to-create-a-derived-control-class"></a>Pro vytvoření třídy odvozené ovládací prvek  
  
1.  Třídě odvozena z existující třídy řízení a volitelně přepsat **vytvořit** člen fungovat, takže poskytuje potřebné argumenty, které mají základní třídy **vytvořit** funkce.  
  
2.  Zadejte popisovač zpráv členských funkcí a položek mapy zpráv chcete upravit chování ovládacího prvku v reakci na konkrétní zpráv systému Windows. V tématu [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md).  
  
3.  Zadejte nové členské funkce rozšířit funkce ovládacího prvku (volitelné).  
  
 Použití odvozené ovládacího prvku v dialogovém okně vyžaduje další práci. Typy a umístění ovládacích prvků v dialogovém okně jsou obvykle určené v prostředku šablony dialogového okna. Pokud vytvoříte třídu odvozenou ovládacího prvku, nelze zadat v dialogovém okně šabloně vzhledem k tomu, že kompilátor prostředků neví nic o odvozené třídy.  
  
#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Umístit odvozené ovládací prvek v dialogovém okně  
  
1.  Vložte objekt třídy odvozené ovládacího prvku v deklaraci vlastní třídy odvozené dialogového okna.  
  
2.  Přepsání `OnInitDialog` členské funkce ve vlastní třídy dialogového okna pro volání `SubclassDlgItem` – členská funkce pro odvozené ovládací prvek.  
  
 `SubclassDlgItem`"dynamicky podtřídy" ovládacího prvku vytvořené z šablony dialogového okna. Když podtřídou dynamicky ovládacího prvku, můžete připojit do systému Windows, zpracovat některé zprávy v rámci vlastní aplikace a pak předat zbývající zprávy k systému Windows. Další informace najdete v tématu [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) funkce člena třídy `CWnd` v *odkaz knihovny MFC*. Následující příklad ukazuje, jak může zapsat přepsání `OnInitDialog` volat `SubclassDlgItem`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]  
  
 Protože odvozené ovládací prvek, je vložena do třídy dialogového okna, bude vypočten když dialogové okno je vytvořený a bude být zničený, když je zničení dialogových oken. Tento kód v příkladu v porovnání [přidávání ovládacích prvků By ruční](../mfc/adding-controls-by-hand.md).  
  
## <a name="see-also"></a>Viz také  
 [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

