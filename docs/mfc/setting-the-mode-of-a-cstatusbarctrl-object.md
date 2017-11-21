---
title: "Nastavení režimu objektu CStatusBarCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 35f48a87a0b9526ad6150a700190f4509e1128d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Nastavení režimu objektu CStatusBarCtrl
Existují dva režimy pro `CStatusBarCtrl` objektu: jednoduché a nejednoduché. Ve většině případů budou mít ovládací prvek panelu Stav jedné nebo více částí, spolu s textem a případně ikonu nebo ikony. Toto je voláno nejednoduché režimu. Další informace o tomto režimu najdete v tématu [inicializace částí objektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).  
  
 Ale existují případy, kdy je potřeba jenom zobrazit na jednom řádku textu. Jednoduchý režim v takovém případě stačí pro vaše potřeby. Chcete-li změnit režim `CStatusBarCtrl` objektu na jednoduchý, ujistěte se, volání [setsimple –](../mfc/reference/cstatusbarctrl-class.md#setsimple) – členská funkce. Jakmile ovládacího prvku panel stav v stručném režimu, nastavení textu voláním **SetText –** – členská funkce, jako hodnotu předávání 255 **nPane** parametr.  
  
 Můžete použít [issimple –](../mfc/reference/cstatusbarctrl-class.md#issimple) funkce k určení jakém režimu `CStatusBarCtrl` objekt je v.  
  
> [!NOTE]
>  Pokud objekt panelu Stav se změní z hodnoty nonsimple na jednoduchý, nebo naopak, okamžitě bude překreslen okna a pokud jsou k dispozici žádné definované částí se automaticky obnoví.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

