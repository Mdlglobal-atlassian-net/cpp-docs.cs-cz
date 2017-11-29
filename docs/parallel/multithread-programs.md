---
title: "Programy s více vlákny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: effbb235ef678253f5258d3eb01a3a82292385cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multithread-programs"></a>Programy s více vlákny
Vlákno je v podstatě cesta provádění prostřednictvím programu. Je také nejmenší jednotkou provádění, která plánuje Win32. Vlákno se skládá z zásobníku, stav registrů CPU a položku v seznamu spuštění plánovače systému. Každé vlákno sdílí všech procesů prostředky.  
  
 Proces se skládá z jednoho nebo více vláken a kód, datům a jiným prostředkům programu v paměti. Typické program prostředky jsou otevřených souborů, semaforů a dynamicky přidělené paměti. Program provede, když se systém Plánovač poskytuje jeden z jeho vláken řízení provádění. Plánovač Určuje, které vláken spuštěna, a pokud by měly být spuštěny. Vlákna s nižší prioritou možná muset počkejte na dokončení úloh vlákna s vyšší prioritou. Na počítačích s více procesory můžete přesunout Plánovač jednotlivých vláken různé procesory, aby Vyrovnávání zatížení procesoru.  
  
 Každé vlákno v procesu funguje nezávisle. Pokud jste je zpřístupněte k sobě navzájem, vláken provést jednotlivě a neberou v jiných vláken v procesu. Sdílení společných prostředků, vláken, musí však koordinovat práci pomocí semaforů nebo použijte jinou metodu meziprocesová komunikace. Další informace o synchronizaci vláken najdete v tématu [psaní programů s více vlákny Win32](../parallel/writing-a-multithreaded-win32-program.md).  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a Win32](../parallel/multithreading-with-c-and-win32.md)