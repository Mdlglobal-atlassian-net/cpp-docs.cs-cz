---
title: Unwind – procedura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2a5af5d8db5974aa10595bbd3bac1cd032a0f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382020"
---
# <a name="unwind-procedure"></a>Unwind – procedura
Unwind kódu jsou rozděleny na sestupném pořadí. Když dojde k výjimce celý kontext uložen operační systém v záznamu kontextu. Logika pro odesílání výjimek je pak vyvolána, která provádí následující kroky k nalezení obslužné rutiny výjimek.  
  
1.  Aktuální RIP uložené v kontextu záznamu slouží k vyhledání položky v tabulce runtime popisující aktuální funkci (nebo část funkce v případě zřetězených položek UNWIND_INFO).  
  
2.  Pokud se nenajde žádný záznam tabulky funkcí, pak je v listu funkcí a konfigurace přímo vyřeší návratový ukazatel. Návratový ukazatel [Konfigurace] je uložená v aktualizované kontextu, simulované konfigurace se zvýší o 8 a krok 1 se opakuje.  
  
3.  Pokud se najde záznam tabulky funkcí, RIP může nacházet ve třech oblastech a) v epilogu, b) v prologu nebo c) v kódu, která mohou být předmětem obslužnou rutinu výjimky.  
  
    -   Případu) Pokud RIP je v rámci epilogu, pak řízení po skončení funkce, může být přidružené k této výjimce pro tuto funkci žádná obslužná rutina výjimky a musí být dál důsledky epilogu výpočetní kontextu volající funkce. Chcete-li zjistit, jestli RIP v rámci epilogu, kód datového proudu z RIP na je zkontrolován. Pokud tento kód datového proudu je možné přiřadit ke konci část legitimního epilogu, pak je v epilogu a zbývající část epilogu se simuluje, pomocí kontextu záznamu, aktualizovat, protože každý instrukce je zpracovat. Poté se opakuje krok 1.  
  
    -   Případě b) Pokud RIP leží v rámci prologu, pak nemá ovládací vložené funkce, může být přidružené k této výjimce pro tuto funkci žádná obslužná rutina výjimky a důsledky prologu musí odvolat k výpočtu kontextu volající funkce. RIP je v rámci prologu pokud vzdálenost od spuštění funkce do RIP je menší než nebo rovna velikosti prologu kódovaný v unwind informace. Účinky prologu jsou odděleny kontrolu předat prostřednictvím unwind kódů pro první položku s posunem menší než nebo rovno posun RIP od začátku funkce a potom vrátí zpět všechny zbývající položky v poli kód unwind účinek. Krok 1 se pak opakuje.  
  
    -   Case c), pokud RIP není v rámci prolog nebo epilogu a funkce má obslužné rutiny výjimek (UNW_FLAG_EHANDLER je nastaveno) a potom je volána obslužná rutina pro konkrétní jazyk. Obslužná rutina prohledá data a volání funkce jako odpovídající filtru. Obslužná rutina pro konkrétní jazyk může vrátit, že bylo zpracováno výjimku nebo vyhledávání bude pokračovat. Unwind ho také můžete spustit přímo.  
  
4.  Pokud obslužná rutina pro konkrétní jazyk vrátí zpracovávaný stavu, pak se pokračuje pomocí původního kontextu záznamu.  
  
5.  Pokud není žádná obslužná rutina konkrétní jazyk nebo obslužná rutina vrátí stav "pokračovat v hledání", musí být oddělen stavu volající záznamu kontextu. To se provádí zpracování všechny elementy pole kód unwind účinek jednotlivých vrácení zpět. Krok 1 se pak opakuje.  
  
 Pokud zřetězené unwind informace je zahrnuta, jsou stále dodrženy tyto základní kroky. Jediným rozdílem je, že při procházení unwind kódu do unwind prologu důsledky, když je dosaženo konce pole, je nadřazená unwind informace pak propojen a je proveden vaši firmu celý unwind kódu můžete nalezeny. Toto propojení pokračuje v až přicházejících unwind informace bez příznaku UNW_CHAINED_INFO a nedokončí se procházení pole unwind kódu.  
  
 Nejmenší sadu unwind dat je 8 bajtů. To představuje funkci, která přiděleny pouze tehdy, 128 bajtů zásobníku nebo méně a případné uložení jednoho stálého registru. Toto je také velikost zřetězené struktury unwind informace nulové délky prologu s žádnými unwind kódy.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek (x64)](../build/exception-handling-x64.md)