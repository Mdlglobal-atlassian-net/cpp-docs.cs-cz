---
title: x64 – prolog a epilog
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328434"
---
# <a name="x64-prolog-and-epilog"></a>x64 – prolog a epilog

Každá funkce, která přiděluje místo v zásobníku, volá jiné funkce, ukládá nestálé registry nebo používá zpracování výjimek, musí mít prolog, jehož omezení adresy jsou popsána v části unwind data přidružená k příslušné položce tabulky funkcí. Další informace naleznete v tématu [zpracování výjimek x64](../build/exception-handling-x64.md). Prolog ukládá Registry argumentů ve svých domácích adresách v případě potřeby, nahraje v zásobníku nestálé Registry, přidělí pevnou část zásobníku pro lokální hodnoty a dočasné objekty a volitelně vytvoří ukazatel na rámec. Přidružená unwind data musí popsat akci prologu a musí poskytovat informace potřebné k vrácení účinku kódu prologu.

Pokud je pevné přidělení v zásobníku více než jedna stránka (což je více než 4096 bajtů), je možné, že přidělení zásobníku může zahrnovat více než jednu stránku virtuální paměti a proto musí být přidělení zkontrolováno před přidělením. Speciální rutina, která je vyvolaná z prologu a která neničí žádné Registry argumentů, je k dispozici pro tento účel.

Upřednostňovanou metodou pro uložení nestálých registrů je přesunutí do zásobníku před pevným přidělením zásobníku. Je-li pevné přidělení zásobníku provedeno před uložením netěkavých registrů, je pravděpodobně pro řešení uložené oblasti registru požadováno navýšení 32 bitového posunu. (Sestavování a nabízených registrů je tak rychlé jako přesunutí a mělo by zůstat v předvídatelné budoucnosti i v případě předpokládané závislosti mezi vložením.) Nestálé Registry lze uložit v libovolném pořadí. První použití nestálého registru v prologu však musí být uloženy.

## <a name="prolog-code"></a>Kód prologu

Kód pro typický Prolog může být:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Tento Prolog ukládá argument registru RCX do svého domovského umístění, uloží nestálý registr R13-R15, přidělí pevnou část rámce zásobníku a vytvoří ukazatel na rámec, který ukazuje 128 bajtů do pevné oblasti přidělení. Použití posunu umožňuje adresovat více pevné oblasti přidělení s posuny s jedním bajtem.

Pokud je pevná velikost alokace větší než nebo rovna jedné stránce paměti, musí být před úpravou RSP volána pomocná funkce. Tato pomocná `__chkstk`rutina provede testem rozsahu zásobníku k zajištění správného rozšíření zásobníku. V takovém případě by předchozí příklad prologu místo toho byl:

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

`__chkstk` Pomocná rutina nebude upravovat žádné Registry jiné než R10, R11 a Code podmínky. Konkrétně vrátí RAX beze změny a ponechá všechny nestálé registry a Registry předávání argumentů beze změny.

## <a name="epilog-code"></a>Kód epilogu

Kód epilogu existuje při každém ukončení do funkce. Vzhledem k tomu, že existuje obvykle pouze jeden Prolog, může existovat mnoho epilogů. Kód epilogu ořízne zásobník na jeho pevnou velikost alokace (Pokud je to nutné), zruší přidělení pevného zásobníku, obnoví stálé registry vyodebráním uložených hodnot ze zásobníku a vrátí.

Kód epilogu musí následovat po striktní sadě pravidel pro unwind kód pro spolehlivou zpětnou likvidaci prostřednictvím výjimek a přerušení. Tato pravidla omezují množství nepotřebných dat, protože k popisu epilogu nejsou potřeba žádná další data. Místo toho může unwind kód určit, že je epilog proveden, pomocí kontroly vpřed prostřednictvím datového proudu kódu, který identifikuje epilog.

Pokud ve funkci není použit žádný ukazatel na rámec, pak musí epilog nejprve uvolnit pevně danou část zásobníku, stálé registry jsou odebrány a ovládací prvek je vrácen funkci volání. Například:

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Pokud je v funkci použit ukazatel na rámec, musí být zásobník oříznut na jeho pevné přidělení před provedením epilogu. Tato akce je technicky nesoučástí epilogu. Například následující epilog by mohl být použit k vrácení předchozího použitého prologu:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

V praxi se při použití ukazatele na rámec nedoporučuje upravit RSP ve dvou krocích, takže se místo toho použije následující epilog:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Tyto formuláře jsou jedinými zákonnými těmi pro epilog. `add RSP,constant` Musí obsahovat buď `lea RSP,constant[FPReg]`nebo, následované řadou nula nebo více 8 bajtů registru pop a `return` nebo. `jmp` (V epilogu je `jmp` povolená jenom podmnožina příkazů. Podmnožina je výhradně třídou `jmp` příkazů s odkazy na paměť ModRM, kde hodnota pole mod ModRM je 00. Použití `jmp` příkazů ve epilogu s hodnotou pole ModRM mod a hodnotou 01 nebo 10 je zakázáno. Další informace o povolených ModRMch odkazech najdete v tabulce A-15 v ručním svazku pro PROCESORy X86-64: Pro obecné účely a pokyny pro systém. Žádný jiný kód se nemůže zobrazit. Konkrétně není možné naplánovat nic v rámci epilogu, včetně načítání návratové hodnoty.

Pokud není použit ukazatel na rámec, epilog musí použít `add RSP,constant` pro zrušení přidělení pevně dané části zásobníku. Nemusí místo toho použít `lea RSP,constant[RSP]` . Toto omezení existuje, takže unwind kód má méně vzorů, které by bylo možné rozpoznat při hledání epilogů.

Pomocí těchto pravidel může unwind kód určit, že se epilog právě provádí, a simulovat provádění zbytku epilogu, aby bylo možné znovu vytvořit kontext volající funkce.

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](x64-software-conventions.md)
