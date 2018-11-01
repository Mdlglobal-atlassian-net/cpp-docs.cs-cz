---
title: struct UNWIND_CODE
ms.date: 11/04/2016
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
ms.openlocfilehash: 1ba3cc76c521e158ba448ac2e4e1beda9b3da35a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643232"
---
# <a name="struct-unwindcode"></a>struct UNWIND_CODE

Unwind kódu se používá k zaznamenání posloupnost operací v úvodní části, které by ovlivnily stálé registry a RSP. Každá položka kód má následující formát:

|||
|-|-|
|UBYTE|Posunutí v prologu|
|UBYTE: 4|Kód operace unwind|
|UBYTE: 4|Informace o operaci|

Pole je seřazeno sestupně posun v prologu.

## <a name="offset-in-prolog"></a>Posunutí v prologu

Posun od začátku této úvodní části koncem instrukce, který provádí tuto operaci, plus 1 (to znamená posun počáteční další instrukci).

## <a name="unwind-operation-code"></a>Kód operace unwind

Poznámka: Určité operační kódy vyžadovat posun bez znaménka na hodnotu v místní zásobníku. Tento posun je od samého začátku (nejnižší adresu) pevné přidělení zásobníku. Pokud pole registru rámce v UNWIND_INFO je nula, je tento posun z RSP. Pokud pole registru rámce je nenulová, jedná se posun od kdy nacházel RSP při FP reg bylo vytvořeno. Se rovná reg FP minus posun reg FP (16 \* registru rámce posun v UNWIND_INFO). Pokud použijete FP reg pak veškerý kód unwind trvá Posun musí použít pouze po navázání FP reg v prologu.

Pro všechny operační kódy s výjimkou `UWOP_SAVE_XMM128` a `UWOP_SAVE_XMM128_FAR`posun bude vždy jednat o násobek 8, protože všechny zásobníku na hranice 8 bajtů (samotného zásobník je vždy 16 bajtů zarovnána) se ukládají hodnoty, které vás zajímají. Pro operační kódy, které berou krátké posun (méně než 512 kB) obsahuje finální USHORT uzly pro tento kód posun dělený 8. Pro operační kódy, které trvat dlouho posun (512 kB < = posun < 4GB), poslední dva uzly USHORT pro tento kód volí posun (ve formátu little endian).

Pro operační kódy `UWOP_SAVE_XMM128` a `UWOP_SAVE_XMM128_FAR`, posun bude vždy násobkem 16, protože všechny operace XMM 128 bitů se musí vyskytovat na paměti, zarovnané 16 bajtů. Proto se používá měřítko 16 pro `UWOP_SAVE_XMM128`, jejímu posuny menší než 1 milion.

Kód operace unwind je jedním z následujících akcí:

`UWOP_PUSH_NONVOL` (0) 1 uzel

Nabízená oznámení registru stálé celých čísel, snížením RSP o 8. Informace o operaci se číslo do registru. Všimněte si, že se z důvodu omezení na epilogů, `UWOP_PUSH_NONVOL` kódy unwind musí být nejdříve uveden v prologu a odpovídajícím způsobem, poslední v kódu unwind. Relativní řazení se vztahuje na všechny ostatní kódy unwind s výjimkou `UWOP_PUSH_MACHFRAME`.

`UWOP_ALLOC_LARGE` (1) 2 a 3 uzly

Přidělte oblasti velké velikosti v zásobníku. Existují dva typy. Pokud se o operaci rovná 0, pak je velikost přidělení dělený 8 je zaznamenán v dalším slotem umožňuje přidělení až 512 kB – 8. Pokud operace informace, které se rovná 1, pak bez měřítka velikosti alokace je zaznamenán v následujících dvou sloty ve formátu little endian, což přidělení až 4GB - 8.

`UWOP_ALLOC_SMALL` (2) 1 uzel

Přidělení prostoru malé velikosti v zásobníku. Pole informace o operaci se velikost přidělení \* 8 + 8, povolení přidělení od 8 do 128 bajtů.

Přidělení zásobníku unwind kód by měl vždy používat co nejkratší možné kódování:

|**Velikost alokační**|**Uvolnění kódu**|
|-|-|
|8 až 128 bajtů|`UWOP_ALLOC_SMALL`|
|136 na 512 kB – 8 bajtů|`UWOP_ALLOC_LARGE`, informace o operaci = 0|
|512 kB až 4G - 8 bajtů|`UWOP_ALLOC_LARGE`, informace o operaci = 1|

`UWOP_SET_FPREG` (3) 1 uzel

Vytvořte registr ukazatele na rámec nastavením registru na některé posun aktuální RSP. Posun je rovna hodnotě registru rámce (škálován) pole posunu v UNWIND_INFO \* 16, což umožňuje posun od 0 do 240. Použití Posun umožňuje zřízení ukazatel na rámec, který odkazuje na střední pevné přidělení zásobníku, pomáhá hustota kód tím, že další přístupy k použití krátkých instrukce formulářů. Všimněte si, že pole informace o operaci je vyhrazen a neměl by se používat.

`UWOP_SAVE_NONVOL` (4) 2 uzly

Uložení stálé celé číslo registru do zásobníku MOV místo PUSH. To se používá především pro shrink-wrapping, kde je uložen stálé registru do zásobníku v pozici, která byla dříve přidělena. Informace o operaci se číslo do registru. Posun škálovat podle 8 zásobníku je zaznamenán v příštích unwind operační kód datovou oblast, jak je popsáno v poznámce výše.

`UWOP_SAVE_NONVOL_FAR` (5) 3 uzly

Uložení stálé celé číslo registru do zásobníku s dlouhým posunem MOV místo PUSH. To se používá především pro shrink-wrapping, kde je uložen stálé registru do zásobníku v pozici, která byla dříve přidělena. Informace o operaci se číslo do registru. Posun bez měřítka zásobníku je zaznamenán v následujících dvou unwind operační kód sloty, jak je popsáno v poznámce výše.

`UWOP_SAVE_XMM128` (8) 2 uzly

Uložte všechny 128 bitů stálý XMM registr v zásobníku. Informace o operaci se číslo do registru. Posun škálovat podle 16 zásobníku je zaznamenán v dalším slotu.

`UWOP_SAVE_XMM128_FAR` (9) 3 uzly

Uložte všechny 128 bitů stálý XMM registr v zásobníku s dlouhým posunem. Informace o operaci se číslo do registru. Posun bez měřítka zásobníku je zaznamenán v následujících dvou sloty.

`UWOP_PUSH_MACHFRAME` (10) 1 uzel

Vložit blok počítače.  To se používá k zaznamenání účinek přerušení hardwaru nebo výjimky. Existují dva typy. Pokud se o operaci rovná 0, následující bylo vloženo do zásobníku:

|||
|-|-|
|RSP + 32|SS|
|RSP + 24|Starý RSP|
|RSP + 16|EFLAGS|
|RSP + 8|CS|
|RSP|KOPÍROVÁNÍ|

Pokud se o operaci rovná 1, pak toto místo toho bylo vloženo:

|||
|-|-|
|RSP + 40|SS|
|RSP + 32|Starý RSP|
|RSP + 24|EFLAGS|
|RSP + 16|CS|
|RSP + 8|KOPÍROVÁNÍ|
|RSP|Kód chyby:|

Tento kód unwind vždy zobrazí ve fiktivní prologu, který je ve skutečnosti nikdy proveden, ale místo toho se zobrazí před skutečné vstupní bod rutiny přerušení a existuje jenom k poskytování místo, kde můžete simulovat nasdílení změn počítače rámce. `UWOP_PUSH_MACHFRAME` zaznamenává tuto simulaci, která indikuje, že počítač má koncepčně provedli následující:

1. Vyvolat přes POP RIP návratovou hodnotu z horní části zásobníku do *Temp*

1. Push SS

1. Starý RSP nabízených oznámení

1. Push EFLAGS

1. CS nabízených oznámení

1. Push *Temp*

1. Vložit kód chyby (Pokud se informace op rovná 1)

Simulované `UWOP_PUSH_MACHFRAME` operace sníží RSP podle 40 (informace o op se rovná 0) nebo 48 (informace o op se rovná 1).

## <a name="operation-info"></a>Informace o operaci

Význam těchto 4 bitů, závisí na kódu operace. Ke kódování registru pro obecné účely (integer), se používá následující mapování:

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 až 15|R8 k R15|

## <a name="see-also"></a>Viz také

[Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)
