---
title: "Run – členská funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bf874dc0d5b2ec8d814bd59a0cfd7fedab3370c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="run-member-function"></a>Run – členská funkce
Aplikace framework tráví většinu času v [spustit](../mfc/reference/cwinapp-class.md#run) funkce člena třídy [CWinApp](../mfc/reference/cwinapp-class.md). Po inicializaci `WinMain` volání **spustit** ke zpracování zpráv smyčky.  
  
 **Spustit** procházení zpráva smyčky, kontrola fronty zpráv pro zprávy k dispozici. Pokud je k dispozici, zprávu **spustit** odešle pro akci. Pokud jsou k dispozici žádné zprávy, což je často nastavena hodnota true, **spustit** volání `OnIdle` udělat všechny doby nečinnosti zpracování, které jste nebo framework může být nutné provést. Pokud je třeba provést žádné zprávy a žádné zpracování při nečinnosti, aplikace počká, až se stane něco. Když se aplikace ukončí, **spustit** volání `ExitInstance`. Na obrázku v [ONIDLE – členská funkce](../mfc/onidle-member-function.md) zobrazuje posloupnost akcí ve smyčce zpráv.  
  
 Odeslání zprávy závisí na druhu zprávy. Další informace najdete v tématu [zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – Třída aplikace](../mfc/cwinapp-the-application-class.md)
