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
ms.openlocfilehash: a658af47723a9c19218b205a17cb46919d7abd59
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932283"
---
# <a name="run-member-function"></a>Run – členská funkce
Aplikace framework tráví většinu času v [spustit](../mfc/reference/cwinapp-class.md#run) funkce člena třídy [CWinApp](../mfc/reference/cwinapp-class.md). Po inicializaci `WinMain` volání `Run` ke zpracování zpráv smyčky.  
  
 `Run` přepínání mezi zpráva smyčky, kontrola fronty zpráv pro zprávy k dispozici. Pokud je k dispozici, zprávu `Run` odešle pro akci. Pokud jsou k dispozici žádné zprávy, což je často nastavena hodnota true, `Run` volání `OnIdle` udělat všechny doby nečinnosti zpracování, které jste nebo framework může být nutné provést. Pokud je třeba provést žádné zprávy a žádné zpracování při nečinnosti, aplikace počká, až se stane něco. Když se aplikace ukončí, `Run` volání `ExitInstance`. Na obrázku v [ONIDLE – členská funkce](../mfc/onidle-member-function.md) zobrazuje posloupnost akcí ve smyčce zpráv.  
  
 Odeslání zprávy závisí na druhu zprávy. Další informace najdete v tématu [zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
