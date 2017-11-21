---
title: "Práce s objekty oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3061787d4be2b85cb1b3776d499e53df83128387
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="working-with-window-objects"></a>Práce s objekty oken
Práce s windows volání pro dva druhy aktivity:  
  
-   Zpracování zpráv systému Windows  
  
-   Kreslení v okně  
  
 Zpracování zpráv systému Windows v jakémkoli okně, včetně vlastní podřízené windows, najdete v tématu [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md) k mapování zpráv na třídě C++ okna. Zapište obslužné rutiny zpráv členské funkce ve třídě.  
  
 Většina kreslení v aplikaci framework dojde v zobrazení, jejichž [OnDraw –](../mfc/reference/cview-class.md#ondraw) – členská funkce je volána, když je nutné vykreslit obsah okna. Pokud je vaše okno podřízené zobrazení, které může delegovat některé kreslení zobrazení do podřízeného okna tak, že `OnDraw` volání jednoho z okna aplikace členské funkce.  
  
 V každém případě budete potřebovat kontextu zařízení pro vykreslování. Můžete použít uložených pera, štětce a jiné grafické objekty obsažené v kontextu zařízení, které jsou přidružené k vaší okno. Nebo můžete upravit tyto objekty kreslení důsledky, které potřebujete získat. S váš kontext zařízení, nastavit, jak se vám líbí, zavolejte členské funkce tříd [CDC](../mfc/reference/cdc-class.md) (kontextu zařízení třída) k vykreslení čar, tvary a text; použít barvy; a pracovat s souřadnicový systém.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)  
  
-   [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)  
  
-   [Kontexty zařízení](../mfc/device-contexts.md)  
  
-   [Grafické objekty](../mfc/graphic-objects.md)  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

