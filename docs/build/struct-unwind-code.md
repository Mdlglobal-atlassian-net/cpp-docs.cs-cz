---
title: struktura UNWIND_CODE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 40b47b2b04d73c30e6c876199dbd98483490f4f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="struct-unwindcode"></a>struct UNWIND_CODE
Unwind kódu se používá k zaznamenání posloupnost operací v prologu, které ovlivňují stálé registry a konfigurace. Každá položka kódu má následující formát:  
  
|||  
|-|-|  
|UBYTE|Posunutí v prologu|  
|UBYTE: 4|Unwind kód operace|  
|UBYTE: 4|Informace o operaci|  
  
 Toto pole je seřazen podle sestupném pořadí posun v prologu.  
  
 **Posunutí v prologu**  
 Posun od začátku prologu konce instrukce, který provádí tuto operaci, plus 1 (to znamená, posun začátku další instrukce).  
  
 **Unwind kód operace**  
 Poznámka: Určité operace kódy vyžadují nepodepsaný posun na hodnotu v rámci místní zásobníku. Tento posun je z počátku pevné přidělení zásobníku (nejnižší adresy). Pokud je pole registru rámce v UNWIND_INFO nula, je tento posun z konfigurace. Pokud je pole registru rámce nenulové, je to posun od kde nacházel konfigurace při FP reg bylo vytvořeno. To se rovná reg FP mínus posun reg FP (16 * posun registru rámce v UNWIND_INFO). Pokud se používá FP reg, pak všechny unwind kód trvá Posun musí použít pouze po navázání FP reg v prologu.  
  
 U všech operačních kódů s výjimkou UWOP_SAVE_XMM128 a UWOP_SAVE_XMM128_FAR posun bude vždy násobkem 8, protože všechny hodnoty zásobníků jsou uloženy v rozsahu 8 bajtů (zásobník samotný je vždy zarovnán na 16 bajtů). Pro operaci kódy, které berou krátký posun (méně než 512 kB) konečný USHORT v uzlech pro tento kód obsahuje posun dělený 8. Pro operaci kódy, které berou dlouhý posun (512 kB < = posun < 4GB), poslední dva uzly USHORT pro tento kód uložení posun (ve formátu little endian).  
  
 U operačních kódů UWOP_SAVE_XMM128 a UWOP_SAVE_XMM128_FAR posun bude vždy násobkem 16, vzhledem k tomu, že všechny operace XMM 128-bit musí proběhnout u paměti, zarovnané 16 bajtů. Měřítko 16 se tedy používá pro UWOP_SAVE_XMM128, jejímu posunutí menší než 1 milion.  
  
 Kód operace unwind je jedním z těchto:  
  
 UWOP_PUSH_NONVOL (0) 1 uzel  
  
 Push stálého registru integer, dekrementace konfigurace číslem 8. Informace o operaci je číslo registru. Všimněte si, že z důvodu omezení na epilogu funkce unwind kódy UWOP_PUSH_NONVOL musí být nejdříve uveden v prologu a odpovídajícím způsobem, poslední v unwind kódu. Relativní řazení se vztahuje na všechny ostatní kódy unwind s výjimkou UWOP_PUSH_MACHFRAME.  
  
 UWOP_ALLOC_LARGE (1) 2 nebo 3 uzly  
  
 Přidělte oblasti velké velikosti v zásobníku. Existují dva způsoby. Pokud se informace o operaci rovná 0, pak je velikost přidělení dělená 8 se zaznamenává v dalším slotu umožněním přidělení až 512 kB - 8. Pokud informace o operaci se rovná 1, pak bez měřítka velikost přidělení se zaznamená do následujících dvou sloty ve formátu little endian umožněním přidělení až 4GB - 8.  
  
 UWOP_ALLOC_SMALL (2) 1 uzel  
  
 Přidělení prostoru malé velikosti v zásobníku. Velikost přidělení je pole informace o operaci * 8 + 8, povolení přidělení od 8 do 128 bajtů.  
  
 Unwind kód pro přidělení zásobníku měli vždycky používat co nejkratší možné kódování:  
  
|||  
|-|-|  
|**Velikost alokační**|**Unwind kódu**|  
|8 až 128 bajtů|UWOP_ALLOC_SMALL|  
|136 až 512K – 8 bajtů|UWOP_ALLOC_LARGE, informace o operaci = 0|  
|512 kB až 4G – 8 bajtů|UWOP_ALLOC_LARGE, informace o operaci = 1|  
  
 UWOP_SET_FPREG (3) 1 uzel  
  
 Vytvořte registr ukazatele na rámec nastavením registru na některé posun aktuální konfigurace. Posun je rovna hodnotě registru rámce posunutí (škálovat) pole v UNWIND_INFO * 16, což umožňuje posun od 0 do 240. Použití Posun umožňuje vytvoření ukazatel na rámec, který odkazuje na středu pevné přidělení zásobníku, pomáhá kód hustotu tím, že další přístupů k použití krátké instrukce formulářů. Všimněte si, že pole informace o operaci je vyhrazen a neměl by se používat.  
  
 UWOP_SAVE_NONVOL (4) 2 uzly  
  
 Uložte stálého registru integer v zásobníku pomocí MOV namísto PUSH. Především slouží k zmenšujícímu obalení, uložení stálého registru do zásobníku na pozici, který se předtím použil. Informace o operaci je číslo registru. Posun zásobníku škálovat podle 8 je zaznamenán v dalším slotu kódu unwind operace, jak je popsáno v poznámce výše.  
  
 UWOP_SAVE_NONVOL_FAR (5) 3 uzly  
  
 Uložení stálé celé číslo registru do zásobníku s dlouhým posunem pomocí MOV namísto PUSH. Především slouží k zmenšujícímu obalení, uložení stálého registru do zásobníku na pozici, který se předtím použil. Informace o operaci je číslo registru. Posun zásobníku bez měřítka se zaznamenává v příštích dvou unwind kód operace slotů, jak je popsáno v poznámce výše.  
  
 UWOP_SAVE_XMM128 (8) 2 uzly  
  
 Uložení všech 128 bitů stálého registru XMM do zásobníku. Informace o operaci je číslo registru. Posun zásobníku škálovat podle 16 je zaznamenán v dalším slotu.  
  
 UWOP_SAVE_XMM128_FAR (9) 3 uzly  
  
 Uložení všech 128 bitů stálého registru XMM do zásobníku s dlouhým posunem. Informace o operaci je číslo registru. Posun zásobníku bez měřítka se zaznamená do následujících dvou sloty.  
  
 UWOP_PUSH_MACHFRAME (10) 1 uzel  
  
 Posun zásobníku počítače.  To se používá k zaznamenání účinku přerušení hardwaru nebo výjimky. Existují dva způsoby. Pokud se informace o operaci rovná 0, následující bylo posunuto v zásobníku:  
  
|||  
|-|-|  
|KONFIGURACE + 32|SS|  
|KONFIGURACE + 24|Původní konfigurace|  
|KONFIGURACE + 16|EFLAGS|  
|KONFIGURACE + 8|CS|  
|KONFIGURACE|RIP|  
  
 Pokud se informace o operaci rovná 1, pak toto místo toho se nabídne:  
  
|||  
|-|-|  
|KONFIGURACE + 40|SS|  
|KONFIGURACE + 32|Původní konfigurace|  
|KONFIGURACE + 24|EFLAGS|  
|KONFIGURACE + 16|CS|  
|KONFIGURACE + 8|RIP|  
|KONFIGURACE|Kód chyby|  
  
 Tento kód unwind vždy zobrazí ve fiktivní prologu, který se spustí ve skutečnosti, ale místo toho se zobrazuje před skutečným vstupním bodem rutiny přerušení a existuje pouze k dispozici místo pro simulaci vložení rámce počítače. UWOP_PUSH_MACHFRAME zaznamenává tuto simulaci, která označuje, že je počítač koncepčně provedl následující:  
  
 POP – návratovou hodnotu RIP z horní části zásobníku do *Temp*  
  
 Push SS  
  
 Push původní konfigurace  
  
 Push EFLAGS  
  
 Push CS  
  
 Push *Temp*  
  
 Push kód chyby (Pokud op info rovná 1)  
  
 Simulovaná operace UWOP_PUSH_MACHFRAME snižuje konfigurace podle 40 (op info rovná 0) nebo 48 (op info rovná 1).  
  
 **Informace o operaci**  
 Význam těchto 4 bitů závisí na kódu operace. Ke kódování registru pro obecné účely (integer), se používá následující mapování:  
  
|||  
|-|-|  
|0|RAX|  
|1|RCX|  
|2|RDX –|  
|3|RBX|  
|4|KONFIGURACE|  
|5|RBP|  
|6|RSI|  
|7|RDI|  
|8 až 15|R8 k R15|  
  
## <a name="see-also"></a>Viz také  
 [Unwind Data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)