---
title: Prolog a Epilog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2939293fe5fbdfd07cb12470790de5b064489d7f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="prolog-and-epilog"></a>Prolog a epilog
Každá funkce, která přiděluje místo v zásobníku, volá jiné funkce, ukládá stálé registry nebo používá zpracování výjimek, musí mít prologu, jejichž adresa limity jsou popsány v unwind data přidružená k položce příslušné funkce tabulky (viz [(X64) zpracování výjimek](../build/exception-handling-x64.md)). Prologu uloží argument registrů v jejich domovské adresy v případě potřeby přesune stálé registry v zásobníku, přidělí pevnou část zásobníku pro místní a dočasné proměnné a volitelně vytváří ukazatel na rámec. Přidružená unwind data musí popisovat akce prologu a poskytne informace potřebné k účinek kód prologu vrátit zpět.  
  
 Pokud pevné přidělení v zásobníku je více než jednu stránku (to znamená, větší než 4096 bajtů), pak je možné, že přidělení zásobníku mohlo rozložit více než jednu stránku virtuální paměti, a proto musí být kontrolované přidělení předtím, než je ve skutečnosti přidělená. Zvláštní rutina volat z prologu a která nezničí některý z argumentů registrů se poskytuje pro tento účel.  
  
 Upřednostňovanou metodou pro ukládání stálé registry je přesuňte je do zásobníku před pevné přidělení zásobníku. Pokud pevné přidělení zásobníku byly provedeny před stálé registry byly uloženy, pak pravděpodobností 32bitový posun by bylo zapotřebí adresu uložené registraci oblasti (údajně posuny registrů jsou stejně tak rychlé jako přesune a by měla zůstat tak pro dohledné budoucnosti navzdory předpokládané závislosti mezi posuny). Stálé registry lze uložit v libovolném pořadí. První použití stálého registru v prologu musí však být ji uložit.  
  
 Kód pro typické prologu může být:  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 Tento prolog ukládá argument registru RCX v jeho domovském umístění, uloží stálé registry R13-R15, přidělí pevnou část rámce zásobníku a vytváří ukazatel na rámec, který odkazuje 128 bajtů do pevně přidělené oblasti. Použití posunutí umožňuje více pevně přidělených oblastí řešit pomocí odsazení bajtu jeden.  
  
 Pokud je pevně přidělená velikost je větší než nebo rovna jedné stránce paměti, pomocné funkce musí být voláno před změnou konfigurace. Tato pomocná funkce __chkstk je zodpovědná za zjišťování přidělený k zásobníku rozsahu, zajistit, že je správně rozšířená zásobníku. V takovém případě by místo toho se v předchozím příkladu prologu:  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
mov      RAX,  fixed-allocation-size  
call   __chkstk  
sub      RSP, RAX  
lea      R13, 128[RSP]  
...  
```  
  
 Funkce __chkstk nezmění žádné jiné registry než R10, R11 a kódy stavu. Konkrétně bude vrátí RAX beze změny a nechte všechny stálé registry a registry pro předávání argumentů ponechat beze změny.  
  
 Kód epilogu existuje na konci každé funkce. Zatímco je obvykle pouze jeden prolog, může být mnoho epilogu funkce. Kód epilogu zkrátí zásobník na jeho pevně přidělenou velikost (v případě potřeby), zruší přidělení pevné přidělení zásobníku, obnoví stálé registry tím odebere jejich uložené hodnoty v zásobníku a vrátí.  
  
 Kód epilogu musí dodržovaly striktní sadu pravidel pro unwind kód k spolehlivě unwind prostřednictvím výjimek a přerušení. Tím se snižuje množství potřebných unwind dat, protože je k popisu každého epilogu potřeba žádná další data. Unwind kód místo toho můžete určit, že epilog je spouštěna naskenováním předat prostřednictvím datového proudu kódu k identifikaci epilogu.  
  
 Pokud žádný ukazatel na rámec se používá v funkci a pak epilogu musí nejprve navrácení pevné části zásobníku, stálé registry jsou odebrány a ovládací prvek se vrátí k funkci volání. Například  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Pokud se ukazatel na rámec používá ve funkci, musí být v zásobníku oříznut na jeho pevně před spuštěním epilogu. Toto je technicky není součástí epilogu. Například následující epilog může vrátit zpět prologu použil:  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 V praxi Pokud je použita ukazatel na rámec, neexistuje žádný důvod upravit konfigurace ve dvou krocích, takže následující epilog by místo toho použít:  
  
```  
lea      RSP, fixed-allocation-size - 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Jedná se o platné formuláře pro epilog. Musí obsahovat buď `add RSP,constant` nebo `lea RSP,constant[FPReg]`, za nímž následují řadu nula nebo více 8-byte registrů a návrat nebo skok. (Jenom podmnožinu skok příkazy jsou povolené v epilogu. Toto jsou výhradně třídy jmps s ModRM paměti odkazy, kde ModRM mod hodnota pole 00. Použití jmps v epilogu s ModRM mod hodnota pole 01 nebo 10 je zakázáno. A-15 najdete v tabulce v programátora AMD x86-64 architektura ruční svazku 3: obecné účely a pokynů systému, další informace o Instructions.). Žádný další kód se může zobrazit. Konkrétně nic nemůže být naplánováno v rámci epilogu, včetně načítání návratovou hodnotu.  
  
 Všimněte si, že, když ukazatel na rámec se nepoužívá, musí používat epilogu `add RSP,constant` se zrušit přidělení pevné části zásobníku. Nesmíte používat `lea RSP,constant[RSP]` místo. Toto omezení existuje, takže unwind kód má méně vzorků k rozpoznání při hledání epilogu funkce.  
  
 Těchto pravidel umožňuje unwind kódu a určit, že epilog aktuálně vykonáván simulovat provádění zbytek epilogu, aby se povolilo kontext volání funkce.  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)