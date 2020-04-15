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

Každá funkce, která přiděluje místo v zásobníku, volá další funkce, ukládá stálé registry nebo používá zpracování výjimek, musí mít prolog, jehož limity adres jsou popsány v datech unwind přidružených k příslušné položce tabulky funkcí. Další informace naleznete v tématu [zpracování výjimek x64](../build/exception-handling-x64.md). Prolog ukládá argument registry v jejich domovské adresy v případě potřeby, tlačí stálé registry v zásobníku, přiděluje pevnou část zásobníku pro místní a dočasné a volitelně vytvoří ukazatel rámce. Přidružená unwind data musí popisovat akci prologu a musí poskytnout informace potřebné k odčinit účinek kódu prologu.

Pokud je pevné přidělení v zásobníku více než jedna stránka (to znamená větší než 4096 bajtů), pak je možné, že přidělení zásobníku může span více než jednu stránku virtuální paměti, a proto přidělení musí být kontrolovány před přidělením. Pro tento účel je k dispozici speciální rutina, která je volatelná z prologu a která nezničí žádný z registrů argumentů.

Upřednostňovanou metodou pro ukládání stálých registrů je přesunout je do zásobníku před přidělením pevného zásobníku. Pokud je přidělení pevného zásobníku provedeno před uložením stálých registrů, je s největší pravděpodobností k adresování oblasti uloženého registru vyžadováno 32bitové posunutí. (Údajně, tlačí registrů jsou stejně rychlé jako pohyby a měly by zůstat tak v dohledné budoucnosti i přes implicitní závislost mezi tlačí.) Stálé registry lze uložit v libovolném pořadí. První použití stálého registru v prologu však musí být k jeho uložení.

## <a name="prolog-code"></a>Kód Prologu

Kód pro typický prolog může být:

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Tento prolog ukládá registr argumentů RCX do svého domovského umístění, ukládá stálé registry R13-R15, přiděluje pevnou část rámce zásobníku a vytvoří ukazatel rámce, který odkazuje na 128 bajtů do oblasti pevného přidělení. Použití posunu umožňuje více pevné přidělení oblasti, které mají být řešeny s jednobajtovým posunem.

Pokud je pevná velikost přidělení větší nebo rovna jedné stránce paměti, musí být před úpravou RSP volána pomocná funkce. Tento pomocník `__chkstk`, sondy k přidělení rozsah zásobníku k zajištění správné rozšíření zásobníku zásobníku. V takovém případě by předchozí příklad prologu byl:

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

Pomocník `__chkstk` nebude upravovat žádné jiné registry než R10, R11 a kódy podmínek. Zejména vrátí RAX beze změny a ponechat všechny stálé registry a argument-předávání registrů beze změny.

## <a name="epilog-code"></a>Kód Epilogu

Kód Epilogu existuje při každém ukončení funkce. Vzhledem k tomu, že obvykle existuje pouze jeden prolog, může existovat mnoho epilogů. Kód Epilogu ořízne zásobník na jeho pevnou velikost přidělení (v případě potřeby), zruší přidělení pevného zásobníku, obnoví stálé registry tím, že odprýskává jejich uložené hodnoty ze zásobníku a vrátí.

Kód epilogu musí dodržovat přísnou sadu pravidel pro unwind kód spolehlivě unwind prostřednictvím výjimek a přerušení. Tato pravidla snižují množství dat unwind, protože k popisu každého epilogu nejsou potřeba žádná další data. Místo toho unwind kód můžete určit, že epilog je spuštěn skenování vpřed prostřednictvím datového proudu kódu k identifikaci epilogu.

Pokud žádný ukazatel rámce se používá ve funkci, pak epilog musí nejprve navrátit pevnou část zásobníku, jsou odebrány stálé registry a ovládací prvek je vrácena do volající funkce. Například:

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Pokud je ve funkci použit ukazatel rámce, musí být zásobník před spuštěním epilogu oříznut na pevné přidělení. Tato akce technicky není součástí epilogu. Například následující epilog může být použit k odformátování dříve použitého prologu:

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

V praxi při použití ukazatele rámce neexistuje žádný dobrý důvod k úpravě RSP ve dvou krocích, takže místo toho by se použil následující epilog:

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Tyto formuláře jsou jediné legální pro epilog. Musí se skládat `add RSP,constant` `lea RSP,constant[FPReg]`buď z nebo , následuje řada nula nebo více `return` 8-bajtů registru pops a nebo nebo `jmp`. (V epilogu `jmp` je přípustná pouze podmnožina příkazů. Podmnožina je výhradně `jmp` třída příkazů s odkazy na paměť ModRM, kde hodnota pole mod mod Mod je 00. Použití `jmp` příkazů v epilogu s hodnotou pole ModRM mod 01 nebo 10 je zakázáno. Další informace o povolených referencích ModRM naleznete v tabulce A-15 v příručním svazku AMD x86-64 Architecture Programmer 3: Obecné účely a systémové pokyny.) Žádný jiný kód se nemůže zobrazit. Zejména nic nelze naplánovat v rámci epilogu, včetně načítání vrácené hodnoty.

Pokud se ukazatel rámce nepoužívá, epilog `add RSP,constant` musí použít k navrátit pevnou část zásobníku. Místo toho `lea RSP,constant[RSP]` se nesmí použít. Toto omezení existuje, takže unwind kód má méně vzorů rozpoznat při hledání epilogs.

Následující pravidla umožňuje unwind kód k určení, že epilog je právě spuštěna a simulovat provádění zbývající epilogu povolit opětovné vytvoření kontextu volající funkce.

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](x64-software-conventions.md)
