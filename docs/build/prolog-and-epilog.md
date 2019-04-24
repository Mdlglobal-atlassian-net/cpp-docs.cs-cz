---
title: x64 kódu prologu a epilogu
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: a225786853fcc2eb7b6a21de29f1ccf4901e4377
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295230"
---
# <a name="x64-prolog-and-epilog"></a>x64 kódu prologu a epilogu

Každá funkce, která přiděluje místo v zásobníku, volání dalších funkcí, uloží stálé registry nebo používá zpracování výjimek, musí mít prologu, jejíž adresa omezení jsou popsány v unwind data přidružená k položce tabulky příslušné funkce. Další informace najdete v tématu [x64 zpracování výjimek](../build/exception-handling-x64.md). Prologu uloží argument registry v jejich domovské adresy v případě potřeby nabízených oznámení stálé registrech do zásobníku, přidělí pevnou součástí zásobníku pro místní hodnoty a dočasné objekty a volitelně vytvoří ukazatel na rámec. Přidružená data unwind musí popisovat akce prologu a poskytne informace potřebné k účinek kód prologu vrátit zpět.

Pokud pevně přidělených v zásobníku je více než jednu stránku (to znamená větší než 4096 bajtů), je možné, že přidělení zásobníku může zahrnovat více než jedné stránky virtuální paměti, a proto přidělení musí být zaškrtnuto, než je přidělená. Speciální rutině, která lze volat z prologu a která nebude zničit některý z argumentů registrů je k dispozici pro tento účel.

Přesunout do zásobníku před pevné přidělení zásobníku je upřednostňovanou metodou pro ukládání stálé registry. Pokud pevné přidělení zásobníku se provádí před uložením stálé registry, potom pravděpodobností 32bitovým posunem je potřeba vyřešit oblasti uložené registrace. (Údajně nabízených oznámení v ceně registrů jsou stejně rychlé jako přesune a tak by mělo zůstat v dohledné budoucnosti budou Přestože předpokládaná závislost mezi nabízených oznámení.) Stálé registry je ukládat v libovolném pořadí. Však musí být prvním použití stálé registru v prologu ji uložit.

## <a name="prolog-code"></a>Kód prologu

Kód pro typické prologu může být:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Tato sekvence prologu obchodů s aplikacemi argument registru RCX v jeho umístění, uloží stálé zaregistruje R13 R15 přidělí pevnou součástí rámce zásobníku a naváže ukazatel na rámec, který odkazuje 128 bajtů do oblasti pevně přidělených. Použití Posun umožňuje více pevně přidělených oblastí řešit pomocí jeden bajtové posunů.

Pokud je pevně přidělených velikost větší než nebo rovna hodnotě jednu stránku paměti, pomocná funkce musí být volána před změnou RSP. Tato pomocná `__chkstk`, sondy zásobníku přidělený k rozsahu zajistit, že je správně rozšířená zásobníku. V takovém případě by místo toho byl v předchozím příkladu kódu prologu:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

`__chkstk` Pomocné rutiny nezmění žádné registry kromě R10 R11 a kódy stavu. Konkrétně se vrátí RAX beze změny a všechny stálé registry a předání argumentu registrů bez jakýchkoli úprav.

## <a name="epilog-code"></a>Kód epilogu

Kód epilogu existuje na konci každé funkci. Zatímco je obvykle pouze jeden prolog, může být mnoho epilogu funkce. Kód epilogu ořízne zásobníku pevně přidělených velikost (v případě potřeby), zruší přidělení pevné přidělení zásobníku, obnoví stálé registry pomocí automaticky otevíraného jejich uložené hodnoty ze zásobníku a vrátí.

Kód epilogu musí postupovat při striktní sadu pravidel pro kód unwind spolehlivě unwind výjimek a přerušení. Tato pravidla snížení množství potřebných unwind dat, protože je potřeba žádná další data k popisu jednotlivých epilogu. Unwind kódu místo toho můžete určit, že se tím, že kontroluje vpřed prostřednictvím datového proudu kódu k identifikaci epilogu zpracovává epilogu.

Pokud není ukazatel na rámec se používá v funkci a pak epilogu musí nejprve zrušte přidělení pevnou součástí zásobníku, stálé registry jsou odebrány a ovládací prvek je vrácena volající funkci. Například

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Pokud ukazatel na rámec se používá ve funkci, musí k jeho pevně přidělených před provedením epilogu oříznut zásobníku. Tato akce je technicky vzato není součástí epilogu. Například následující epilog může vrátit zpět prologu používali dříve:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

V praxi při použití ukazatel na rámec, neexistuje žádný dobrý důvod k úpravě RSP ve dvou krocích, takže následující epilogu by místo toho použít:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Tyto formy jsou pouze ty, které pro epilogu. Musí obsahovat buď `add RSP,constant` nebo `lea RSP,constant[FPReg]`následovaný posloupnost nula nebo více bodů POP 8bajtový registru a `return` nebo `jmp`. (Pouze podmnožinu `jmp` příkazy nejsou povolené v epilogu. Dílčí je výhradně třída `jmp` příkazů s odkazy na paměť ModRM kde ModRM mod pole hodnota je 00. Použití `jmp` příkazy v epilogu pomocí ModRM mod pole Hodnota 01 nebo 10 je zakázána. Zobrazit tabulku A-15 ruční hromadně AMD x86 – x 64 architektura programátora ve 3: Obecné účely a pokyny k systému, další informace o Instructions.) Žádný další kód se nemůže objevit. Konkrétně se nic nemůže být naplánováno v rámci epilogu, včetně načítání návratovou hodnotu.

Když se nepoužívá ukazatel na rámec, musíte použít epilogu `add RSP,constant` se uvolnit pevnou součástí do zásobníku. Nesmíte používat `lea RSP,constant[RSP]` místo. Toto omezení existuje, a proto unwind kód má menší počet vzorků k rozpoznání při hledání epilogu funkce.

Těchto pravidel umožňuje unwind kódu k určení, že se aktuálně zpracovává epilog a simulují provádění zbytek epilogu, aby se povolilo kontext volání funkce.

## <a name="see-also"></a>Viz také:

[x64 – softwarové konvence](x64-software-conventions.md)
