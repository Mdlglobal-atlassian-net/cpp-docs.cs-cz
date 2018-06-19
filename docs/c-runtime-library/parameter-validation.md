---
title: Ověření parametru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d39011149de0b2fb81b70d58d768a06dc8a95355
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450248"
---
# <a name="parameter-validation"></a>Ověřování parametru
Většina funkcí Rozšířené zabezpečení CRT a řadu dříve existující funkce ověřit jejich parametrů. To může zahrnovat kontrola ukazatele pro **NULL**, kontrola, že celá spadat do platný rozsah nebo kontrola, zda jsou hodnoty výčtu platná. Pokud je nalezen neplatný parametr, spustit je obslužná rutina neplatný parametr.  
  
## <a name="invalid-parameter-handler-routine"></a>Neplatný parametr rutiny ovladače  
 Zjistí-li funkce běhové knihovny jazyka C neplatný parametr, zaznamená některé informace o této chybě a pak zavolá makro, který zabalí neplatný parametr obslužná rutina odesílání funkce mezi [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md), nebo [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). Volaná funkce odesílání závisí na tom, jestli váš kód je, v uvedeném pořadí, sestavení ladicí verze, prodejní sestavení nebo chyba, nepovažuje použitelná pro obnovení. 
 
 V sestavení pro ladění makro neplatný parametr obvykle vyvolá selhání kontrolního výrazu a ladicí program zarážek předtím, než je volána funkce odesílání. Po provedení kód kontrolní výraz se může hlásit uživateli v dialogu, který má "Zrušení", "Opakování" a "Pokračovat" nebo podobné možnosti, v závislosti na verzi knihovny operačního systému a modulu runtime. Tyto možnosti Povolit uživateli okamžitě ukončení programu, připojit ladicí program, nebo pokud chcete umožnit existující kód upravíte nadále spouštět, která volá funkci odesílání. 
 
 Neplatný parametr obslužná rutina odesílání funkce volá obslužná rutina aktuálně přiřazené neplatný parametr. Ve výchozím nastavení, neplatný parametr volání `_invoke_watson` které způsobí, že aplikace "havárií", který je, ukončete a generovat malý výpis. Pokud je povoleno podle operačního systému, dialogové okno požádá uživatele, pokud chtějí načíst stav systému společnosti Microsoft pro analýzu.   
  
 Toto chování lze změnit pomocí funkce [_set_invalid_parameter_handler –](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) nebo [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) při nastavování obslužné rutiny neplatný parametr pro vlastní funkce. Pokud funkce, které zadáte nezavře aplikace, ovládací prvek se vrátí funkce, která přijal neplatné parametry. V CRT, obvykle tyto funkce přestanou spuštění funkce, nastavení `errno` na kód chyby a vrátí kód chyby. V mnoha případech `errno` hodnoty a návratové hodnoty jsou obě `EINVAL`, označující neplatný parametr. V některých případech konkrétnější vrácený kód chyby je, jako například `EBADF` pro ukazatel chybného souboru předaná jako parametr. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="see-also"></a>Viz také  
 [Funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)