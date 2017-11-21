---
title: "Použití seznamů obrázků v ovládacím prvku panel nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e48212de73a614ec7baca9bbd5a919d16941486c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Použití seznamů obrázků v ovládacím prvku panel nástrojů
Ve výchozím nastavení jsou obrázky používané tlačítek v ovládacím prvku panel nástrojů uloženy jako jeden rastrového obrázku. Však také můžete uložit tlačítko bitové kopie v sadě seznamů obrázků. Objekt ovládacího prvku panel nástrojů můžete použít až tři seznamy samostatnou bitovou kopii:  
  
-   Povolit Image obsahuje seznam bitové kopie pro tlačítka panelu nástrojů, které jsou nyní zapnuta.  
  
-   Zakázat Image obsahuje seznam bitové kopie pro tlačítka panelu nástrojů, které jsou aktuálně zakázány.  
  
-   Zvýrazněná Image obsahuje seznam bitové kopie pro tlačítka panelu nástrojů, které jsou aktuálně vyznačené. Tento image se použije jenom v případě, že používá panelu nástrojů **TBSTYLE_FLAT** stylu.  
  
 Pokud je s přidružíte používají tyto seznamy obrázků ovládací prvek panelu nástrojů `CToolBarCtrl` objektu. Toto přidružení se provádí tak, že volání [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), a [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).  
  
 Ve výchozím nastavení používá MFC `CToolBar` třídu pro implementaci panely nástrojů rozhraní MFC aplikace. Ale `GetToolBarCtrl` – členská funkce slouží k načtení vložený `CToolBarCtrl` objektu. Potom můžete provést volání `CToolBarCtrl` členské funkce pomocí vráceného objektu.  
  
 Následující příklad ukazuje tato technika přiřazením povolenu (`m_ToolBarImages`) a zakázané (`m_ToolBarDisabledImages`) seznamu bitové kopie `CToolBarCtrl` objektu (`m_ToolBarCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]  
  
> [!NOTE]
>  Seznamy obrázků použité objektem nástrojů musí být trvalé objekty. Z toho důvodu jsou běžně datové členy třídy knihovny MFC; v tomto příkladu třída hlavního rámce okna.  
  
 Jakmile jsou přidružené seznamů obrázků `CToolBarCtrl` objektu, rozhraní se automaticky zobrazí obrázek správné tlačítka.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

