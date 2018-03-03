---
title: "Vytvoření ovládacího prvku matrice | Microsoft Docs"
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
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 263541d9dc462b067caf763fe969f3809f1daa7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-rebar-control"></a>Vytvoření ovládacího prvku matrice
[Crebarctrl –](../mfc/reference/crebarctrl-class.md) objekty by měl být vytvořen, než je viditelná pro nadřazený objekt. Tím se minimalizují možnosti vykreslování problémů.  
  
 Například ovládací prvky matrice (používá se v objekty oken rámečkem) běžně se používají jako nadřazené windows pro ovládací prvky panelu nástrojů. Proto nadřazeného ovládacího prvku matrice je objekt rámce okna. Protože objekt rámce okna je nadřazeným prvkem, `OnCreate` členské funkce (nadřazené) je vhodné místo pro vytvoření ovládacího prvku matrice.  
  
 Použít `CReBarCtrl` objektu, bude obvykle postupujte podle těchto kroků:  
  
### <a name="to-use-a-crebarctrl-object"></a>Použít crebarctrl – objekt  
  
1.  Vytvořit [crebarctrl –](../mfc/reference/crebarctrl-class.md) objektu.  
  
2.  Volání [vytvořit](../mfc/reference/crebarctrl-class.md#create) běžné prvku matrice Windows a vytvořte jej do `CReBarCtrl` objekt, zadat všechny požadované styly.  
  
3.  Načíst rastrový obrázek s volání [CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), který se má použít jako pozadí objekt ovládacího prvku matrice.  
  
4.  Vytvoření a inicializace okno podřízené objekty (panely nástrojů, ovládací prvky dialogového okna a tak dále), které bude obsahovat objekt ovládacího prvku matrice.  
  
5.  Inicializace **REBARBANDINFO** struktura nezbytné informace pro vzdálené chystáte vložit.  
  
6.  Volání [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) vložit existující podřízená okna (například `m_wndReToolBar`) do nového ovládacího prvku matrice. Další informace o vkládání pruhy do existujícího ovládacího prvku matrice najdete v tématu [matrice – ovládací prvky a pruhy](../mfc/rebar-controls-and-bands.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

