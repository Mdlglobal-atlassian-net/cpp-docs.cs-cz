---
title: Zpracování výjimek ARM64
description: Popisuje konvence zpracování výjimek a data používaná systémem Windows na ARM64.
ms.date: 11/19/2018
ms.openlocfilehash: 1ed147a27cfeb545e2a5fe265df8113a5befac73
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72276831"
---
# <a name="arm64-exception-handling"></a>Zpracování výjimek ARM64

Systém Windows v ARM64 používá stejný mechanismus strukturovaného zpracování výjimek pro asynchronní výjimky generované hardwarem a synchronní výjimky generované softwarem. Obslužné rutiny výjimek pro konkrétní jazyk jsou postaveny na základě strukturovaného zpracování výjimek ve Windows pomocí pomocných funkcí jazyka. Tento dokument popisuje zpracování výjimek ve Windows v ARM64 a jazyky, které používá kód generovaný kompilátorem Microsoft ARM assembler a MSVC.

## <a name="goals-and-motivation"></a>Cíle a motivace

Konvence unwind dat a tento popis jsou určeny pro:

1. Poskytněte dostatek popisů, aby bylo možné v každém případě odvíjení bez zjišťování kódu.

   - Analýza kódu vyžaduje, aby byl kód na stránce. V některých případech to brání v nevinutí, kde je to užitečné (trasování, vzorkování, ladění).

   - Analýza kódu je složitá; Kompilátor musí být pečlivý, aby vygeneroval pouze pokyny, které může unwinder dekódovat.

   - Pokud unwind nemůže být plně popsané pomocí unwind kódů, pak v některých případech musí přejít zpět k dekódování instrukcí. Tím se zvyšuje celková složitost a ideálně se jim vyhne.

1. Podpora unwindy v polovině prologu a polovině epilogu.

   - V systému Windows se používá odvíjení pro více než zpracování výjimek. Je velmi důležité, aby kód mohl být zpětně vytvořen i v případě, že je uprostřed sekvence kódu prologu nebo epilogu.

1. Vezměte v úvahu minimální množství místa.

   - Unwind kódy nesmí být agregovány, aby významně zvýšily binární velikost.

   - Vzhledem k tomu, že unwind kódy pravděpodobně budou uzamčeny v paměti, malé nároky zajistí minimální režii pro každý načtený binární soubor.

## <a name="assumptions"></a>Předpoklady

Tyto předpoklady jsou provedeny v popisu zpracování výjimek:

1. Protokoly a epilogy se obvykle zrcadlí jako jiné. Když využijete tento společný druh, může se výrazně snížit velikost metadat potřebných k popsání zrušení. V těle funkce bez ohledu na to, zda jsou operace prologu vráceny, nebo jsou operace epilogu dokončeny způsobem. Obě by měly mít stejné výsledky.

1. Funkce, které jsou celkově relativně malé. Několik optimalizací pro prostor spoléhají na tento fakt, aby bylo možné dosáhnout nejúčinnějšího balení dat.

1. V epilogech není žádný podmíněný kód.

1. Vyhrazený registr ukazatele na rámec: Pokud je aktualizace SP uložena v jiném registru (x29) v prologu, tento registr zůstane v rámci celé funkce. To znamená, že původní aktualizace SP může být kdykoli obnovená.

1. Pokud je aktualizace SP uložena v jiném registru, veškerá manipulace s ukazatelem zásobníku probíhá výhradně v rámci prologu a epilogu.

1. Rozložení rámce zásobníku je uspořádáno, jak je popsáno v následující části.

## <a name="arm64-stack-frame-layout"></a>Rozložení rámce zásobníku ARM64

(media/arm64-exception-handling-stack-frame.png "rozložení rámce zásobníku") ![rozložení rámce zásobníku]

V případě funkcí zřetězených podle rámců lze dvojici FP a LR uložit na libovolné místo v oblasti místní proměnné v závislosti na optimalizaci optimalizace. Cílem je maximalizovat počet lokálních hodnot, které mohou být dostupné jedinou instrukcí na základě ukazatele na rámec (x29) nebo ukazatel zásobníku (SP). U funkcí `alloca` však musí být zřetězené a x29 musí ukazovat na dolní část zásobníku. Aby bylo možné zajistit lepší pokrytí v rámci adresování, je možné nestálé oblasti uložení registru umístit v horní části zásobníku místní oblasti. Tady jsou příklady, které ilustrují několik nejúčinnějších sekvencí prologu. V zájmu přehlednosti a lepšího prostředí mezipaměti je pořadí ukládání volaných a uložených registrů ve všech kanonických protokolech v pořadí "rostoucího". `#framesz` níže představuje velikost celého zásobníku (kromě oblasti přidělení). `#localsz` a `#outsz` Poznamenejte velikost místní oblasti (včetně oblasti uložení \<x29, LR > dvojice) a velikosti odchozího parametru v uvedeném pořadí.

1. Zřetězené #localsz \< = 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. Zřetězené #localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. Nezřetězené funkce listu (neuložené LR)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Všechna místní prostředí jsou k dispozici na základě SP. \<x29, LR > odkazuje na předchozí snímek. Pro velikost rámečku \< = 512, "sub SP,..." může být optimalizována, pokud je regs uložená oblast přesunuta do dolní části zásobníku. Nevýhodou je, že se neshoduje s ostatními rozloženími a uložená Regs se přijímají do rozsahu pro režim párování regs a předzálohovacího adresování.

1. Nezřetězené funkce, které nejsou na list (LR se ukládají do uložené oblasti int)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Nebo s sudým počtem uložených registrů int,

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Pouze uložené x19:

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* přidělení oblasti pro uložení v registru není přeloženo do STP, protože předem indexovaný reg-LR STP nemůže být reprezentovaná pomocí unwind kódů.

   Všechna místní prostředí jsou k dispozici na základě SP. \<x29 > odkazuje na předchozí snímek.

1. Zřetězené #framesz \< = 512, #outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   V porovnání s prvním předchozím příkladem prologu je zde výhoda, že všechny pokyny pro uložení registru jsou připravené ke spuštění po pouze jedné instrukci pro přidělení zásobníku. To znamená, že není k dispozici žádná závislost na SP, která zabraňuje paralelismuům na úrovni instrukcí.

1. Zřetězené, velikost rámečku > 512 (volitelné pro funkce bez přidělení)

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   Pro účely optimalizace je možné x29 umístit na libovolné místo v místní oblasti, aby se zajistilo lepší pokrytí pro "registrační pár" a režim adresování před/post-Indexed. K místním hodnotám, které jsou k ukazatelům snímků, lze přistupovat na základě SP.

1. Zřetězené, velikost rámečku > 4K, s nebo bez alokačního a (),

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informace o zpracování výjimek ARM64

### <a name="pdata-records"></a>záznamy. pdata

Záznamy. pdata jsou seřazené pole položek s pevnou délkou, které popisují všechny funkce manipulace s zásobníky v binárním souboru PE. Fráze "manipulace s zásobníkem" je významná: funkce listu, které nevyžadují žádné místní úložiště a nepotřebují ukládat/obnovovat netěkavé Registry, nevyžadují záznam. pdata. Tyto záznamy by se měly explicitně vynechat, aby se ušetřilo místo. Unwind z jedné z těchto funkcí může získat návratovou adresu přímo z LR a přejít tak k volajícímu.

Každý záznam. pdata pro ARM64 má délku 8 bajtů. Obecný formát každého záznamu umístí 32-bitovou adresu RVA funkce, kterou začíná v prvním slově následovaný druhým slovem, které obsahuje buď ukazatel na proměnnou length. xdata blok, nebo zabalený text, který popisuje kanonickou sekvenci unwind funkce.

![PDATA rozložení záznamu].(media/arm64-exception-handling-pdata-record.png "PDATA rozložení záznamu")

Pole jsou následující:

- **Počáteční adresa RVA funkce** je 32-BITOVÁ adresa RVA začátku funkce.

- **Příznak** je 2 bitové pole, které určuje, jak interpretovat zbývající 30 bitů druhého. pdata slovo. Pokud je **příznak** 0, zbývající bity vychází z **informací o výjimce RVA** (se dvěma nejnižšími bitymi implicitně 0). Pokud **příznak** není nula, zbývající bity budou mít **sbalenou strukturu unwind dat** .

- **Informace o výjimce RVA** je adresa struktury informací o výjimce s proměnnou délkou, která je uložená v oddílu. xdata. Tato data musí být zarovnané na 4 bajty.

- **Zabalená unwind data** jsou komprimovaným popisem operací, které jsou potřeba k unwindu z funkce za předpokladu kanonického tvaru. V tomto případě není vyžadován žádný záznam XData.

### <a name="xdata-records"></a>záznamy. xdata

Pokud je zabalený unwind formát nedostatečný pro popis odvíjení funkce, je nutné vytvořit záznam s proměnnou délkou. xdata. Adresa tohoto záznamu je uložena ve druhém slově záznamu. pdata. Formát. xdata je zabalená sada slov s proměnlivou délkou:

![XData rozložení záznamu].(media/arm64-exception-handling-xdata-record.png "XData rozložení záznamu")

Tato data jsou rozdělená do čtyř oddílů:

1. Záhlaví 1 nebo 2 slova popisující celkovou velikost struktury a poskytování klíčových dat funkcí. Druhé slovo je přítomno pouze v případě, že jsou pole **počet epilogu** a **slova kódu** nastavená na hodnotu 0. Záhlaví obsahuje tato bitová pole:

   a. **Délka funkce** je 18 bitové pole. Označuje celkovou délku funkce v bajtech dělenou 4. Je-li funkce větší než 1 milion, je nutné pro popis funkce použít více záznamů. pdata a. xdata. Další informace najdete v části [velké funkce](#large-functions) .

   b. **Průřez** je 2 bitové pole. Popisuje verzi zbývajícího. xdata. V současné době je definována pouze verze 0, takže hodnoty 1-3 nejsou povoleny.

   c. **X** je 1 bitové pole. Označuje přítomnost dat výjimky (1) nebo absence (0).

   d. **E** je 1 bitové pole. Označuje, že informace popisující jeden epilog se zabalí do hlavičky (1) místo toho, aby později vyžadovala další slovo rozsahu (0).

   e. **Počet epilog** je 5 bitové pole, které má dva významy v závislosti na stavu **E** -bitu:

      1. Pokud je hodnota **E** 0, určuje celkový počet rozsahů epilogu popsaných v části 2. Pokud ve funkci existuje více než 31 oborů, pole **kód** se musí nastavit na hodnotu 0, aby označovala, že je nutné zadat rozšiřující slovo.

      2. Pokud je **E** 1, pak toto pole určuje index prvního unwind kódu, který popisuje pouze jeden a epilog.

   f. **Slova kódu** jsou 5 bitové pole, které určuje počet 32-bitových slov potřebných k tomu, aby obsahoval všechny unwind kódy v oddílu 3. Pokud je vyžadováno více než 31 slov (tj. Pokud existuje více než 124 unwind bajtů), musí být toto pole 0, aby označovalo, že je nutné zadat rozšiřující slovo.

   g. **Rozšířené počty epilogů** a **Rozšířená kódová slova** jsou 16bitová a 8bitové pole v uvedeném pořadí. Poskytují více místa pro kódování neobvykle velkého počtu epilogů nebo neobvykle velký počet slov unwind kódu. Toto slovo rozšíření, které obsahuje tato pole, je přítomno pouze v případě, že pole **počet epilogu** a **slova kódu** v prvním záhlaví jsou 0.

1. Pokud **počet epilogů** není nula, zobrazí se seznam informací o oborech epilogu zabalené do slova, které se nachází po záhlaví a volitelné rozšířené hlavičce. Ukládají se v pořadí od zvýšení počátečního posunu. Každý obor obsahuje následující bity:

   a. **Počáteční posun epilogu** je 18 bitové pole, které má posun v bajtech dělený 4, z epilogu vzhledem k začátku funkce.

   b. **Res** je 4 bitové pole rezervované pro budoucí rozšíření. Jeho hodnota musí být 0.

   c. **Počáteční index epilogu** je 10 bitové pole (2 více bitů než **slova rozšířená kódu**). Označuje index bajtů prvního unwind kódu, který popisuje tento epilog.

1. Po seznamu oborů epilogu dojde k poli bajtů, které obsahují unwind kódy, podrobněji popsané v další části. Toto pole je doplněno na konci k nejbližší celé hranici slova. Do tohoto pole se zapisují unwind kódy. Začínají s nejblíže k hlavní části funkce a přesun směrem k okrajům funkce. Bajty pro každý kód unwind jsou uloženy v pořadí big-endian, aby bylo možné je načíst přímo, počínaje nejvýznamnějším bajtem, který identifikuje operaci a délkou zbytku kódu.

1. Nakonec, po uplynutí bajtů unwind kódu, pokud byl bit **X** v hlavičce nastaven na hodnotu 1, obsahuje informace o obslužné rutině výjimky. Obsahuje jednu adresu **RVA obslužné rutiny výjimky** , která poskytuje adresu samotné obslužné rutiny výjimky. Následuje bezprostředně za proměnnou délkou dat, kterou vyžaduje obslužná rutina výjimky.

Záznam. xdata je navržený tak, aby bylo možné načíst prvních 8 bajtů a použít je k výpočtu plné velikosti záznamu, mínus délku dat výjimky proměnné velikosti, které následují. Následující fragment kódu vypočítá velikost záznamu:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

I když prolog a každý epilog má svůj vlastní index do unwind kódů, je mezi nimi sdílena tabulka. Je to zcela možné (a není zcela běžné), že můžou všechny sdílet stejné kódy. (Příklad naleznete v části Příklad 2 v oddílu [Příklady](#examples) .) Moduly pro zápis kompilátoru by měly pro tento případ optimalizovat, zejména proto, že největší index, který lze zadat, je 255, což omezuje celkový počet unwind kódů pro konkrétní funkci.

### <a name="unwind-codes"></a>Unwind kódy

Pole unwind kódů je fond sekvencí, který přesně popisuje, jak vrátit zpět účinky prologu, uložený ve stejném pořadí, že operace musí být vráceny zpět. Unwind kódy lze představit jako malou sadu instrukcí, která je zakódována jako řetězec bajtů. Po dokončení spuštění je zpáteční adresa volající funkce v registru LR. A všechny netěkavé Registry jsou obnoveny do jejich hodnot v době volání funkce.

Pokud by výjimky byly zaručeny jenom v těle funkce a nikdy v rámci prologu nebo žádného epilogu, bude nutné jenom jednu sekvenci. Model unwind pro systém Windows ale vyžaduje, aby byl kód v částečně spuštěném prologu nebo epilogu. Aby bylo možné tento požadavek splnit, jsou unwind kódy pečlivě navržené, takže jednoznačně mapují 1:1 na každý relevantní operační kód v prologu a epilogu. Tento návrh má několik dopadů:

1. Napočítáním počtu unwind kódů je možné vypočítat délku prologu a epilogu.

1. Napočítáním počtu instrukcí za začátek rozsahu epilogu je možné přeskočit ekvivalentní počet unwind kódů. Potom můžeme spustit zbytek sekvence a dokončit částečně provedené unwind provedené pomocí epilogu.

1. Napočítáním počtu instrukcí před koncem prologu je možné přeskočit ekvivalentní počet unwind kódů. Potom můžeme spustit zbytek sekvence a vrátit zpět pouze ty části prologu, jejichž provedení bylo dokončeno.

Unwind kódy jsou zakódovány podle následující tabulky. Všechny unwind kódy jsou jedním nebo dvojitým bajtem, s výjimkou toho, který přiděluje obrovský zásobník. Úplně existuje 21 unwind kód. Každý unwind kód mapuje přesně jednu instrukci v prologu/epilog, aby bylo umožněno odvinutí částečně spuštěných protokolů a epilogů.

|Unwind kód|Bity a interpretace|
|-|-|
|`alloc_s`|000xxxxx: přidělte velikost malého zásobníku \< 512 (2 ^ 5 × 16).|
|`save_r19r20_x`|    001zzzzz: Save \<x19, x20 > páry na `[sp-#Z*8]!`, předem indexovaný posun > =-248 |
|`save_fplr`|        01zzzzzz: Save \<x29, LR > dvojici v `[sp+#Z*8]`, posun \< = 504. |
|`save_fplr_x`|        10zzzzzz: Save \<x29, LR > páry na `[sp-(#Z+1)*8]!`, předem indexovaný posun > =-512 |
|`alloc_m`|        11000xxx'xxxxxxxx: přidělte velkou velikost zásobníku s velikostí \< 16% (2 ^ 11 * 16). |
|`save_regp`|        110010xx'xxzzzzzz: Uložit dvojici x (19 + #X) na `[sp+#Z*8]`, posun \< = 504 |
|`save_regp_x`|        110011xx'xxzzzzzz: Uložit dvojici x (19 + #X) na `[sp-(#Z+1)*8]!`, předem indexovaný posun > =-512 |
|`save_reg`|        110100xx'xxzzzzzz: Save x (19 + #X) na `[sp+#Z*8]`, offset \< = 504 |
|`save_reg_x`|        1101010x'xxxzzzzz: Save x (19 + #X) on `[sp-(#Z+1)*8]!`, index s předdefinovaným posunem > =-256 |
|`save_lrpair`|         1101011x'xxzzzzzz: Uložit dvojici @no__t – 0x (19 + 2 * #X), LR > na `[sp+#Z*8]`, posun \< = 504 |
|`save_fregp`|        1101100x'xxzzzzzz: Uložit pár d (8 + #X) na `[sp+#Z*8]`, posun \< = 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz: Uložit pár d (8 + #X), na `[sp-(#Z+1)*8]!`, předindexované posunutí > =-512 |
|`save_freg`|        1101110x'xxzzzzzz: uložte reg d (8 + #X) na `[sp+#Z*8]`, offset \< = 504 |
|`save_freg_x`|        11011110 ' xxxzzzzz: Save reg d (8 + #X) na `[sp-(#Z+1)*8]!`, předindexované posun > =-256 |
|`alloc_l`|         11100000 ' xxxxxxxx'xxxxxxxx'xxxxxxxx: přidělit velký zásobník s velikostí \< 256M (2 ^ 24 * 16) |
|`set_fp`|        11100001: nastavte x29: with: `mov x29,sp` |
|`add_fp`|        11100010 ' xxxxxxxx: nastavte x29 na: `add x29,sp,#x*8` |
|`nop`|            11100011: není požadována žádná operace unwind. |
|`end`|            11100100: konec unwind kódu. Implikuje ret v epilogu. |
|`end_c`|        11100101: konec unwind kódu v aktuálním zřetězeném oboru. |
|`save_next`|        11100110: uložte následující pár nestálých registrů int nebo FP. |
|`arithmetic(add)`|    11100111 ' 000zxxxx: Přidat soubor cookie reg (z) do LR (0 = x28, 1 = SP); `add lr, lr, reg(z)` |
|`arithmetic(sub)`|    11100111 ' 001zxxxx: sub cookie reg (z) from LR (0 = x28; 1 = SP); `sub lr, lr, reg(z)` |
|`arithmetic(eor)`|    11100111 ' 010zxxxx: EOR LR with cookie reg (z) (0 = x28, 1 = SP); `eor lr, lr, reg(z)` |
|`arithmetic(rol)`|    11100111 ' 0110xxxx: simulovaná ROL LR se souborem cookie reg (x28); xip0 = záporné x28; `ror lr, xip0` |
|`arithmetic(ror)`|    11100111 ' 100zxxxx: ROR LR with cookie reg (z) (0 = x28, 1 = SP); `ror lr, lr, reg(z)` |
| |            11100111: xxxz----:----vyhrazena |
| |              11101xxx: vyhrazeno pro vlastní případy zásobníku níže, které jsou vygenerovány pouze pro rutiny ASM |
| |              11101000: vlastní zásobník pro MSFT_OP_TRAP_FRAME |
| |              11101001: vlastní zásobník pro MSFT_OP_MACHINE_FRAME |
| |              11101010: vlastní zásobník pro MSFT_OP_CONTEXT |
| |              11101100: vlastní zásobník pro MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx: rezervováno |

V pokynech týkajících se velkých hodnot, které pokrývají více bajtů, jsou nejprve uloženy nejvýznamnější bity. Tento návrh umožňuje najít celkovou velikost unwind kódu v bajtech hledáním pouze prvního bajtu kódu. Vzhledem k tomu, že každý unwind kód je přesně namapován na instrukci v prologu nebo epilogu, lze vypočítat velikost prologu nebo epilogu. Můžete procházet od začátku sekvence po konec a pomocí vyhledávací tabulky nebo podobného zařízení určit, jak dlouho je odpovídající operační kód.

Adresování odsazení po indexovaném indexu není v prologu povolené. Všechny rozsahy posunu (#Z) odpovídají kódování adres STP/STR s výjimkou `save_r19r20_x`, ve kterých je 248 dostačující pro všechny oblasti ukládání (10 int Registry + 8 FP Registry + 8 vstupních registrů).

`save_next` musí následovat po nestálém páru registru pro int nebo FP: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x` nebo jiný `save_next`. Uloží další dvojici registru v dalších 16 bajtových slotech v "rostoucím" pořadí. @No__t-0 odkazuje na první pár registru FP, pokud následuje `save-next`, která označuje pár registrů posledního int.

Vzhledem k tomu, že velikost běžných návratových instrukcí a pokynů pro skoky jsou stejné, není nutné oddělený @no__t 0 unwind kód pro scénáře s koncovým voláním.

`end_c` je navržena pro zpracování nesouvislých fragmentů funkcí pro účely optimalizace. @No__t-0, který označuje konec unwind kódů v aktuálním oboru, musí následovat jiná série unwind kódu skončila skutečným `end`. Unwind kódy mezi `end_c` a `end` reprezentují operace prologu v nadřazené oblasti ("fiktivní" Prolog).  Další podrobnosti a příklady jsou popsány v následující části.

### <a name="packed-unwind-data"></a>Zabalená unwind data

Pro funkce, jejichž protokoly a epilogy následují podle kanonického tvaru popsaného níže, lze použít zabalená data unwind. Eliminuje nutnost záznamu. xdata zcela a významně snižuje náklady na poskytování nevětrných dat. Kanonické protokoly a epilogy jsou navržené tak, aby splňovaly společné požadavky jednoduché funkce: jeden, který nevyžaduje obslužnou rutinu výjimky a který provádí operace nastavení a rozboru ve standardním pořadí.

Formát záznamu. pdata se zabalenými unwind daty vypadá takto:

![záznam. pdata s zabalenými unwind daty](media/arm64-exception-handling-packed-unwind-data.png ". pdata záznam se sbalenými newindými daty")

Pole jsou následující:

- **Počáteční adresa RVA funkce** je 32-BITOVÁ adresa RVA začátku funkce.
- **Příznak** je 2 bitové pole, jak je popsáno výše, s následujícími významy:
  - 00 = zabalené unwind data se nepoužívají; zbývající bity nasměrují na záznam. xdata
  - 01 = zabalená unwind data používaná s jedním prologem a epilogem na začátku a na konci oboru
  - 10 = zabalená unwind data použitá pro kód bez jakéhokoli prologu a epilogu. Užitečné pro popis segmentů oddělených funkcí
  - 11 = rezervováno.
- **Délka funkce** je 8bitové pole, které poskytuje délku celé funkce v bajtech dělenou 4. Pokud je funkce větší než 8k, je nutné místo toho použít úplný záznam. xdata.
- **Velikost rámečku** je 8bitové pole udávající počet bajtů zásobníku, který je přidělený této funkci, dělený 16. Funkce, které přidělují více než (8k-16) bajtů zásobníku, musí používat plný záznam. xdata. Obsahuje oblast místní proměnné, oblast odchozího parametru, volaný – uložený typ int a FP a domovskou oblast, ale vyloučí oblast dynamického přidělení.
- **CR** je 2 bitový příznak označující, jestli funkce zahrnuje další pokyny pro nastavení řetězu snímků a návratového odkazu:
  - 00 = nezřetězená funkce, \<x29, LR dvojice > není v zásobníku uložena.
  - 01 = nezřetězená funkce, \<lr > je uložena v zásobníku
  - 10 = rezervováno;
  - 11 = zřetězená funkce: v prologu/epilogu se používá instrukce Store/Load \<x29, LR >
- **H** je 32bitový příznak označující, zda je funkce celočíselný parametr registrován (x0-120) tak, že je uloží na začátek funkce. (0 = nejedná se o domovské Registry, 1 = domácí Registry).
- **Blast** je 4 bitové pole označující počet nestálých registrů int (x19-x28) uložených v kanonickém umístění zásobníku.
- **RegF** je 3 bitové pole označující počet nestálých registrů FP (D8-D15) uložených v kanonickém umístění zásobníku. (RegF = 0: není uložen žádný registr FP; RegF > 0: Registry RegF + 1 FP jsou uloženy). Zabalená unwind data nelze použít pro funkci, která ukládá pouze jeden registr FP.

Kanonické protokoly, které spadají do kategorií 1, 2 (bez odchozí oblasti parametrů), 3 a 4 v oddílu výše, mohou být reprezentovány zabaleným formátem unwind.  Epilogy pro kanonické funkce následují podobně, s výjimkou **H** nemá žádný vliv, instrukce `set_fp` se vynechá a pořadí kroků a instrukcí v jednotlivých krocích se v epilogu zruší. Algoritmus pro zabalený. xdata se řídí těmito kroky, které jsou popsané v následující tabulce:

Krok 0: předběžná výpočet velikosti každé oblasti.

Krok 1: uložení typu int volaný – uložené registry.

Krok 2: Tento krok je specifický pro typ 4 v dřívějších částech. LR je uložen na konci celé oblasti.

Krok 3: uložení volaných a uložených registrů FP

Krok 4: uložte vstupní argumenty v oblasti domovského parametru.

Krok 5: přidělení zbývajícího zásobníku, včetně místní oblasti, \<x29, LR > párování a odchozí oblasti parametrů. 5a odpovídá kanonickému typu 1. 5b a 5c jsou pro kanonický typ 2. hodnoty 5D a 5e jsou pro typ 3 i typ 4.

Krok #|Hodnoty příznaků|počet instrukcí|Operačních|Unwind kód
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1\. místo|0 < **blast** < = 10|Blast/2 + **Blast** %2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**= = 01 *|1\. místo|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1)/2 +<br/>(RegF + 1) %2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
vkládá|**CR** = = 11 & & #locsz<br/> < = 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** = = 11 & &<br/>512 < #locsz < = 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5C|**CR** = = 11 & & #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5D|(**CR** = = 00 \| @ no__t-2 **CR**= = 01) & &<br/>#locsz < = 4080|1\. místo|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** = = 00 \| @ no__t-2 **CR**= = 01) & &<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Pokud je **CR** = = 01 a **Blast** liché číslo, krok 2 a poslední save_rep v kroku 1 jsou sloučeny do jednoho save_regp.

\* @ no__t-1 Pokud **blast** == **CR** = = 0 a **RegF** ! = 0, první STP pro plovoucí desetinnou čárku bude odečtena.

\* @ no__t-1 @ no__t-2 v epilogu není k dispozici žádná instrukce odpovídající `mov x29,sp`. Zabalená unwind data se nedají použít, pokud funkce vyžaduje obnovení SP z x29.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Odvíjení částečných protokolů a epilogů

Nejběžnější situací, kdy by došlo k výjimce nebo volání v těle funkce, je mimo prolog a všechny epilogy. V této situaci je nevinutí jednoduché: unwinda jednoduše zahájí spouštění kódů v unwind poli počínaje indexem 0 a pokračuje, dokud není detekován konec operačního kódu.

V případě, že dojde k výjimce nebo přerušení při provádění prologu nebo epilogu, je to obtížnější. V těchto situacích je rámec zásobníku vytvořen pouze částečně. Problémem je určení přesně toho, co bylo provedeno, aby bylo možné ho správně vrátit.

Například proveďte tento prolog a sekvenci epilogu:

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

Vedle každého operačního kódu je odpovídající unwind kód popisující tuto operaci. Můžete vidět, jak je řada unwind kódů pro Prolog přesný zrcadlový obraz kódů pro epilog (nepočítá se konečné instrukce epilogu). Jedná se o běžnou situaci a je to proto, že vždycky předpokládáme, že unwind kódy pro Prolog jsou uloženy v opačném pořadí od pořadí provádění prologu.

Pro prolog i epilog ale jsme opustili společnou sadu unwind kódů:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Případ epilogu je jednoduchý, protože je v normálním pořadí. Počínaje posunem 0 v rámci epilogu (který začíná na posunu 0x100 ve funkci) očekáváme, že se spustí úplná unwind sekvence, protože se ještě neudělalo žádné vyčištění. Pokud jsme našli dodržovali jednu instrukci (na posunu 2 v epilogu), můžeme úspěšně vrátit zpět vynecháním prvního kódu unwind. Tuto situaci můžeme zobecnit a předpokládat mapování 1:1 mezi opcodemi a unwind kódy. Potom pro zahájení odvíjení z instrukcí *n* ve epilogu doporučujeme přeskočit prvních *n* unwind kódů a začít z něj.

Zapíná, že podobná logika funguje pro Prolog, s výjimkou opačného. Pokud začínáte s posunem 0 v prologu, chceme nespouštět nic. Pokud provádíme zpět od posunu 2, což je jedna instrukce v, pak chceme začít spouštět unwind sekvencování jednoho unwind kódu od konce. (Nezapomeňte, že kódy jsou uloženy v opačném pořadí.) A je to také můžeme zobecnit: pokud začneme v prologu vrátit zpět z instrukce n, měli byste začít spouštět n unwind kódy na konci seznamu kódů.

Nejedná se vždy o případ, že se kód prologu a epilogu přesně shodují. To je důvod, proč může být nutné, aby pole unwind mohlo obsahovat několik sekvencí kódu. K určení posunu místa, kde začít zpracovávat kódy, použijte následující logiku:

1. Pokud se odvíjí od těla funkce, zahajte spouštění unwind kódu na indexu 0 a pokračujte, dokud se nespustí opcode "end".

1. Pokud se v rámci epilogu odvíjí, použijte jako výchozí bod počáteční index specifický pro epilog, který je k dispozici s oborem epilogu. Vypočítá počet bajtů, které počítač splňuje, od začátku epilogu. Pak se přeskočí zpětných kódů unwind a přeskočí unwind kódy, dokud nebudou k disloze všechny již spouštěné instrukce. Pak spusťte od tohoto okamžiku.

1. Pokud se v prologu odvíjí, jako výchozí bod použijte index 0. Vypočítá délku kódu prologu z sekvence a pak vypočítá počet bajtů, které počítač splňuje, od konce prologu. Pak se přesměrujte zpět pomocí unwind kódů a přeskočí unwind kódy, dokud nebudou všechny Nespuštěné pokyny k disloze. Pak spusťte od tohoto okamžiku.

Tato pravidla znamenají, že unwind kódy pro Prolog musí být vždy první v poli. A jsou také kódy, které se používají k odvíjení v obecném případě odvíjení v těle. Všechny sekvence kódu specifické pro epilog by měly následovat hned po.

### <a name="function-fragments"></a>Fragmenty funkcí

Pro účely optimalizace kódu a jiných důvodů může být vhodnější rozdělit funkci na oddělené fragmenty (označované také jako oblasti). Při rozdělení každý výsledný fragment funkce vyžaduje svůj vlastní samostatný záznam. pdata (a případně. xdata).

U každého odděleného sekundárního fragmentu, který má svůj vlastní Prolog, je očekáváno, že není provedena žádná úprava zásobníku v jeho prologu. Všechny prostory zásobníku požadované sekundární oblastí musí být předem přiděleny v nadřazené oblasti (nebo označované jako hostitelská oblast). Tím se zachovává striktní manipulace s ukazatelem zásobníku v původním prologu funkce.

Typický případ fragmentů funkcí je "oddělení kódu" s tímto kompilátorem může přesunout oblast kódu z funkce hostitele. Existují tři neobvyklé případy, které by mohly být způsobeny oddělením kódu.

#### <a name="example"></a>Příklad:

- (oblast 1: začátek)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (oblast 1: konec)

- (oblast 3: začátek)

    ```asm
        ...
    ```

- (oblast 3: konec)

- (oblast 2: začátek)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (oblast 2: konec)

1. Pouze prolog (oblast 1: všechny epilogy jsou v oddělených oblastech):

   Je třeba popsat pouze Prolog. Tato reprezentace nemůže být reprezentovaná ve formátu Compact. pdata. V plném rozsahu. xdata může být reprezentována nastavením počet epilogu = 0. Viz oblast 1 v předchozím příkladu.

   Unwind kódy: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Pouze epilogy (oblast 2: Prolog je v oblasti hostitele)

   Předpokládá se, že v čase řízení přechod do této oblasti byly provedeny všechny kódy prologu. K částečnému unwindu může dojít v epilogech stejným způsobem jako v normální funkci. Tento typ oblasti nemůže být reprezentovaný pomocí Compact. pdata. V úplném záznamu. xdata může být kódovaný pomocí "fiktivního" prologu, v závorkách, oddělený dvojicí `end_c` a `end` unwind kódu.  Úvodní `end_c` značí, že velikost prologu je nula. Epilog – počáteční index jednotlivých bodů epilogu do `set_fp`

   Unwind kód pro oblast 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Žádné protokoly ani epilogy (oblast 3: proprotokoly a všechny epilogy jsou v dalších fragmentech):

   Formát Compact. pdata lze použít prostřednictvím příznaku nastavení = 10. S úplným záznamem. xdata, počet epilogu = 1. Unwind kód je stejný jako kód pro oblast 2 výše, ale u počátečního indexu epilogu směřuje také `end_c`. V této oblasti kódu nebude nikdy provedena částečná operace unwind.

Další složitější případy fragmentů funkcí jsou "zmenšení zalamování". Kompilátor se může rozhodnout pro zpoždění uložení některých volaných uložených registrů, dokud neleží mimo prolog vstupu funkce.

- (oblast 1: začátek)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (oblast 2: začátek)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (oblast 2: konec)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (oblast 1: konec)

V prologu oblasti 1 je prostor zásobníku předem přidělený. Uvidíte, že oblast 2 bude mít stejný unwind kód, i když se přesune mimo svoji hostitelskou funkci.

Oblast 1: `set_fp`, `save_regp 0,240` `save_fplr_x_256` `end` s epilogem počátečního indexu body `set_fp` jako obvykle.

Oblast 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240` `save_fplr_x_256`, `end`. Epilog počáteční index ukazuje na první unwind kód `save_regp 2, 224`.

### <a name="large-functions"></a>Velké funkce

Fragmenty lze použít k popisu funkcí větších, než je limit 1 milion, který je určen bitovými poli v hlavičce. xdata. Chcete-li popsat velmi velkou funkci, je nutné ji rozdělit na fragmenty menší než 1M. Jednotlivé fragmenty by měly být upraveny tak, aby nedošlo ke rozdělení epilogu do více kusů.

Pouze první fragment funkce bude obsahovat Prolog; všechny ostatní fragmenty jsou označeny jako bez prologu. V závislosti na počtu nalezených epilogů může každý fragment obsahovat nula nebo více epilogů. Mějte na paměti, že každý rozsah epilogu v fragmentu Určuje počáteční posun vzhledem k začátku fragmentu, ne na začátku funkce.

Pokud fragment neobsahuje žádný prolog a žádný epilog, bude stále vyžadovat vlastní záznam. pdata (a případně. xdata), který popisuje, jak se vrátit zpět v těle funkce.

## <a name="examples"></a>Příklady

### <a name="example-1-frame-chained-compact-form"></a>Příklad 1: zřetězení s rámečkem, kompaktní tvar

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Příklad 2: orámování zřetězení, úplný tvar s zrcadlením prologu & epilog

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

Epilog začátek indexu [0] odkazuje na stejné pořadí unwind kódu prologu.

### <a name="example-3-variadic-unchained-function"></a>Příklad 3: nezřetězená funkce variadické

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

Epilog začátek indexu [4] odkazuje na střed unwind kódu prologu (částečné opakované použití unwind pole).

## <a name="see-also"></a>Další informace najdete v tématech

[Přehled konvencí ARM64 ABI](arm64-windows-abi-conventions.md)<br/>
[Zpracování výjimek ARM](arm-exception-handling.md)
