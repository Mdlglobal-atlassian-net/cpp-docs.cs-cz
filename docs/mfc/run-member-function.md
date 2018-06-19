---
title: Run – členská funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be1d7d90b4c13a23e2e3456e7371abbae61be4e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379893"
---
# <a name="run-member-function"></a>Run – členská funkce
Aplikace framework tráví většinu času v [spustit](../mfc/reference/cwinapp-class.md#run) funkce člena třídy [CWinApp](../mfc/reference/cwinapp-class.md). Po inicializaci `WinMain` volání **spustit** ke zpracování zpráv smyčky.  
  
 **Spustit** procházení zpráva smyčky, kontrola fronty zpráv pro zprávy k dispozici. Pokud je k dispozici, zprávu **spustit** odešle pro akci. Pokud jsou k dispozici žádné zprávy, což je často nastavena hodnota true, **spustit** volání `OnIdle` udělat všechny doby nečinnosti zpracování, které jste nebo framework může být nutné provést. Pokud je třeba provést žádné zprávy a žádné zpracování při nečinnosti, aplikace počká, až se stane něco. Když se aplikace ukončí, **spustit** volání `ExitInstance`. Na obrázku v [ONIDLE – členská funkce](../mfc/onidle-member-function.md) zobrazuje posloupnost akcí ve smyčce zpráv.  
  
 Odeslání zprávy závisí na druhu zprávy. Další informace najdete v tématu [zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
