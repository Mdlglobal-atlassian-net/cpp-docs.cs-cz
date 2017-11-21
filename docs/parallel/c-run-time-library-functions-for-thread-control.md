---
title: "Funkce běhové knihovny jazyka C pro řízení vláken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f9691a4edcbf617be415ba8d48d80938cba4979
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-run-time-library-functions-for-thread-control"></a>Funkce běhové knihovny jazyka C pro řízení vláken
Všechny programy Win32 mít alespoň jedno vlákno. Jakékoli vlákno můžete vytvořit další vlákna. Vlákno můžete rychle dokončit svou práci a pak ukončete, nebo může zůstat aktivní po dobu trvání programu.  
  
 Běhové knihovny C LIBCMT a MSVCRT poskytují následující funkce pro vytváření a ukončení vlákna: [_beginthread _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) a [_endthread _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).  
  
 `_beginthread` a `_beginthreadex` funkce vytvořit nové vlákno a vrátí identifikátor vlákna, pokud byla operace úspěšná. Vlákno se automaticky ukončí pokud dokončí provádění nebo jej můžete ukončit pomocí volání `_endthread` nebo `_endthreadex`.  
  
> [!NOTE]
>  Pokud chcete volat C běhové rutiny z programu vytvořené s Libcmt.lib, je nutné spustit vaší vláken s `_beginthread` nebo `_beginthreadex` funkce. Nepoužívají funkce Win32 `ExitThread` a `CreateThread`. Pomocí `SuspendThread` může vést k vzájemnému zablokování, když je více než jedno vlákno zablokuje čekáním na pozastavené vlákno dokončí přístup k C Runtime datová struktura.  
  
##  <a name="_core_the__beginthread_function"></a>_Beginthread – a _beginthreadex – funkce  
 `_beginthread` a `_beginthreadex` funkce vytvořit nové vlákno. Vlákno sdílí kód a data segmenty procesu s jiná vlákna v procesu, ale má svůj vlastní jedinečný registr hodnot, místa v zásobníku a aktuální adresa instrukce. Systém přiřadí času procesoru pro každé vlákno tak, aby všechny vláken v procesu můžete současně provést.  
  
 `_beginthread`a `_beginthreadex` jsou podobné [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkce v rozhraní API Win32 má ale tyto rozdíly:  
  
-   Inicializují určité proměnné běhové knihovny jazyka C. To je důležité, pouze pokud používáte běhové knihovny jazyka C ve vašem vláken.  
  
-   `CreateThread`pomáhá poskytovat kontrolu nad atributů zabezpečení. Tato funkce vám pomůže spustit vlákno v pozastaveném stavu.  
  
 `_beginthread`a `_beginthreadex` vrací popisovač nové vlákno v případě úspěchu nebo kód chyby, pokud došlo k chybě.  
  
##  <a name="_core_the__endthread_function"></a>_Endthread – a _endthreadex – funkce  
 [_Endthread](../c-runtime-library/reference/endthread-endthreadex.md) funkce ukončí vlákno vytvořené `_beginthread` (a podobně `_endthreadex` ukončí vlákno vytvořené `_beginthreadex`). Vlákna ukončit automaticky při ukončení. `_endthread`a `_endthreadex` jsou užitečné pro podmíněné ukončení zevnitř vlákna. Vlákno vyhrazené ke zpracování komunikace může například skončit, pokud nelze získat kontrolu nad komunikační port.  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a Win32](../parallel/multithreading-with-c-and-win32.md)