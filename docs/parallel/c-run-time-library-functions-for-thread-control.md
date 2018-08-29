---
title: Funkce knihovny Run-Time jazyka C pro řízení vláken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2eaa1a0589cb001658b18144e06956eebd302287
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131851"
---
# <a name="c-run-time-library-functions-for-thread-control"></a>Funkce běhové knihovny jazyka C pro řízení vláken
Všechny programy Win32 mají alespoň jedno vlákno. Jakékoli vlákno můžete vytvořit další vlákna. Vlákno může rychle dokončí svou práci a pak ukončete, nebo může zůstat aktivní po dobu životnosti programu.  
  
Knihovny runtime LIBCMT a MSVCRT jazyka C poskytují následující funkce pro vytváření a ukončení vlákna: [_beginthread _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) a [_endthread _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).  
  
`_beginthread` a `_beginthreadex` funkce vytvořit nové vlákno a vrací identifikátor vlákna, pokud je operace úspěšná. Vlákno se automaticky ukončí dokončí provádění, nebo jej můžete ukončit volání `_endthread` nebo `_endthreadex`.  
  
> [!NOTE]
> Pokud se chystáte volání rutiny C za běhu z aplikace vytvořené pomocí Libcmt.lib, je nutné spustit vlákna s `_beginthread` nebo `_beginthreadex` funkce. Nepoužívejte funkce Win32 `ExitThread` a `CreateThread`. Pomocí `SuspendThread` může vést k zablokování při více než jedno vlákno je zablokuje čekáním pozastaveného vlákna dokončí přístup do struktury dat za běhu C.  
  
##  <a name="_core_the__beginthread_function"></a> _Beginthread a _beginthreadex funkce  
 
`_beginthread` a `_beginthreadex` funkce vytvořit nové vlákno. Vlákno sdílí segmentů kódu a dat procesů pro ostatní vlákna v procesu, ale má svůj vlastní jedinečný registr hodnoty, místo v zásobníku a aktuální adresa instrukce. Systém přiděluje čas procesoru pro každé vlákno tak, aby všechna vlákna v procesu mohou být prováděna současně.  
  
`_beginthread` a `_beginthreadex` je podobný jako [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) – funkce rozhraní Win32 API, ale nemá tyto rozdíly:  
  
- Inicializují určité proměnné knihovny run-time C. To je důležité, pouze při použití knihovny run-time jazyka C v vlákna.  
  
- `CreateThread` pomáhá zajistit kontrolu nad atributy zabezpečení. Tuto funkci můžete spustit vlákno v pozastaveném stavu.  
  
 `_beginthread` a `_beginthreadex` vrací popisovač do nové vlákno v případě úspěchu nebo kód chyby, pokud došlo k chybě.  
  
##  <a name="_core_the__endthread_function"></a> _Endthread a _endthreadex funkce  
 
[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md) funkce ukončí vlákno vytvořil `_beginthread` (a naopak `_endthreadex` ukončí vlákno vytvořil `_beginthreadex`). Vlákna automaticky ukončit, když jsou dokončeny. `_endthread` a `_endthreadex` jsou užitečné pro podmíněné ukončení v rámci vlákno. Vlákno vyhrazený pro zpracování, komunikace například můžete skončit, pokud nelze získat kontrolu nad komunikační port.  
  
## <a name="see-also"></a>Viz také  
 
[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)