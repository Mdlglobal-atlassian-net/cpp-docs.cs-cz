---
title: Zpracování výjimek ARM64
ms.date: 07/11/2018
ms.openlocfilehash: 5189c399a4cbff071d2ec846008229ba76306882
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333586"
---
# <a name="arm64-exception-handling"></a>Zpracování výjimek ARM64

Windows pro ARM64 se používá stejné strukturovaného zpracování výjimek mechanismus pro asynchronní výjimky generované hardwaru a synchronní výjimky generované softwaru. Obslužné rutiny výjimek specifické pro jazyk jsou postavené na Windows zpracování s použitím jazyka pomocné funkce strukturovaných výjimek. Tento dokument popisuje zpracování výjimek v Windows na ARM64 a pomocné rutiny jazyka, používané kódu, který je generován assembler Microsoft ARM a kompilátor Visual C++.

## <a name="goals-and-motivation"></a>Cíle a motivace

Data konvence odvíjení výjimky a tento popis jsou určené pro:

1. Poskytuje dostatek popis umožňující odvíjení bez kódu, testování ve všech případech.

   - Analýza kódu se vyžaduje kód pro stránkování v. To zabraňuje odvíjení v některých případech, kdy je vhodné (trasování, vzorkování, ladění).

   - Analýza kódu je složitá. Kompilátor musíte být opatrní a generovat jenom pokyny, že je unwinder dokáže dekódování.

   - Pokud není možné plně popsány pomocí kódy unwind odvíjení, v některých případech ho musí přejít k dekódování instrukce. To zvyšuje celkovou složitost a v ideálním případě by se jim vyhnout.

1. Podpora odvíjení v polovině kódu prologu a epilogu uprostřed.

   - Uvolnění se používá ve Windows pro více než zpracování výjimek, takže je důležité, že budeme moct provádět přesný unwind i při uprostřed sekvence kódu prologu nebo epilogu.

1. Spotřebovávat minimální množství místa.

   - Významně zvyšuje velikost binárního nesmí agregovat kódy unwind.

   - Vzhledem k tomu, že kódy unwind můžou být uzamknuta v paměti, malé náklady zajišťuje minimální režie pro každý načtený binární soubor.

## <a name="assumptions"></a>Předpoklady

Následují předpoklady v popisu zpracování výjimek:

1. Pro zrcadlení obou jiné mají tendenci Prology a epilogu funkce. Podle a současně využívat toto společné vlastnosti lze velikost metadata potřebná k popisu odvíjení výrazně snížit. V těle funkce nezáleží, jestli jsou prologu operace vrátit zpět nebo epilogu operace se provádějí v dopředné způsobem. Jak by měl vytvářet identické výsledky.

1. Funkce jsou obvykle celkově poměrně malý. Několik optimalizací pro prostor spoléhat na to, abyste dosáhli co nejúčinnější balení data.

1. V epilogů není žádný podmíněný kód.

1. Vyhrazené registr ukazatelů rámce: Pokud sp je uložen v registru jiného (r29) v prologu, registru zůstane beze změny v rámci funkce, tak, aby původní sp může být kdykoli obnoven.

1. Pokud sp je uložen v registru jiné, všech manipulaci s ukazatel zásobníku dojde k výhradně v rámci kódu prologu a epilogu.

1. Rozložení rámce zásobníku je uspořádaný, jak je popsáno v další části.

## <a name="arm64-stack-frame-layout"></a>Rozložení rámce zásobníku ARM64

![rozložení rámce zásobníku](../build/media/arm64-exception-handling-stack-frame.png "rozložení rámce zásobníku")

Pro funkce rámce zřetězené lze uložit dvojice fp a lr v jakékoliv pozici v oblasti místní proměnné v závislosti na důležité informace o optimalizaci. Cílem je maximalizovat počet místních hodnot, které mohou být dosažitelný podle jedna jediná instrukce založené na ukazatel na rámec (r29) nebo ukazatel zásobníku (sp). Ale pro `alloca` funkce, musí být zřetězené a r29 musí odkazovat na konec zásobníku. Umožňující lepší pokrytí register pár – adresování – režim, zaregistrujte stálé aave, které oblasti jsou umístěny v horní části zásobníku místní síti. Tady jsou příklady, které ilustrují několik nejúčinnější sekvence prologu. Z důvodu přehlednosti a lepší umístění mezipaměti pořadí ukládání volaný – uložené registry ve všech canonical Prology je popořadě "rostoucí up". `#framesz` níže představuje velikost vším, co (s výjimkou oblasti alloca). `#localsz` a `#outsz` označení velikost místní síti (včetně uložení oblast pro \<r29, lr > pár) a odchozí velikost parametru v uvedeném pořadí.

1. Zřetězené #localsz \<= 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        stp    r29, lr, [sp, -#localsz]!    // save <r29,lr> at bottom of local area
        mov    r29,sp                   // r29 points to bottom of local
        sub    sp, #outsz               // (optional for #outsz != 0)
    ```

1. Zřetězené #localsz > 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        sub    sp,#localsz+#outsz       // allocate remaining frame
        stp    r29, lr, [sp, #outsz]    // save <r29,lr> at bottom of local area
        add    r29,sp, #outsz           // setup r29 points to bottom of local area
    ```

1. Funkce unchained, typu list (lr neuložené)

    ```asm
        stp    r19,r20,[sp, -72]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp, 16]
        str    r23 [sp,32]
        stp    d8,d9,[sp,40]            // save FP regs (optional)
        stp    d10,d11,[sp,56]
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Všechny místní hodnoty jsou přístupné podle SP. \<R29, lr > odkazuje na předchozí snímek. Pro velikost rámce \<= 512, "sub sp,..." lze vypuštěn když oblasti regs uložit se přesune do dolní části zásobníku. Nevýhodou, který je, že to není konzistentní s jiné rozložení výše a uložené regs trvat součástí rozsahu pro dvojice regs a provedení před instrumentací a po ní indexované režim odsazení adresování.

1. Funkce unchained, mimo úroveň listu (lr je uložen v oblasti Int uložit)

    ```asm
        stp    r19,r20,[sp,-80]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        stp    r23, lr,[sp, 32]         // save last Int reg and lr
        stp    d8,d9,[sp, 48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,64]          // ...
        sub    sp,#framesz-80           // allocate the remaining local area
    ```

   Nebo se sudým číslem uložené registry Int

    ```asm
        stp    r19,r20,[sp,-72]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        str    lr,[sp, 32]              // save lr
        stp    d8,d9,[sp, 40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,56]          // ...
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Pouze r19 uložit:

    ```asm
        sub    sp, sp, #16              // reg save area allocation*
        stp    r19,lr,[sp,0]            // save r19, lr
        sub    sp,#framesz-16           // allocate the remaining local area
    ```

   \* Reg uložit přidělení oblast není složeny do stp, protože předem indexované reg-lr stp nejde reprezentovat kódy unwind.

   Všechny místní hodnoty jsou přístupné podle SP. \<R29 > odkazuje na předchozí snímek.

1. Zřetězené #framesz \<= 512 #outsz = 0

    ```asm
        stp    r29, lr, [sp, -#framesz]!    // pre-indexed, save <r29,lr>
        mov    r29,sp                       // r29 points to bottom of stack
        stp    r19,r20,[sp, #framesz -32]   // save INT pair
        stp    d8,d9,[sp, #framesz -16]     // save FP pair
    ```

   Porovnejte prologu #1 výše, výhodou je, se všechny registrace uložit pokyny se spustí hned po pouze jeden zásobníku přidělením pokyn. Proto není proti závislost na sp, která zabrání instrukce úrovně paralelismu.

1. Zřetězené, velikost rámce > 512 (volitelné pro funkce bez alloca)

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        sub    sp,#framesz-80               // allocate the remaining local area
    ```

   Za účelem optimalizace r29 můžete umístit na libovolné pozici v místní síti a poskytuje lepší pokrytí pro "reg dvojice" a předprodukční/po-indexed posun režim adresování. Místní hodnoty níže ukazatele na rámce je přístupný podle SP.

1. Zřetězené, velikost rámce > 4 kB, s nebo bez něj alloca(),

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        mov    r8, #framesz/16
        bl     chkstk
        sub    sp, r8*16                    // allocate remaining frame
                                            // end of prolog
        ...
        sp = alloca                         // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,r29                       // sp points to top of local area
        ldp    d10,d11, [sp,64],
        ...
        ldp    r29, lr, [sp], -80           // post-indexed, reload <r29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informace o zpracování výjimky ARM64

### <a name="pdata-records"></a>záznamy .pdata

Záznamy .pdata jsou uspořádaného pole položek pevné délky, které popisují každý manipulace s zásobníku funkce v binárním souboru PE. Pozorně si frázi "zásobníku-manipulace s": listů funkcí, které nevyžadují žádné místní úložiště a kterého není potřeba uložit/obnovit bez registry nevyžadují, aby záznam .pdata; Tyto by měl být explicitně vynechat pro úsporu místa. Unwind z jednoho z těchto funkcí mohou jednoduše získat zpáteční adresu z LR vypracovat tak, aby volající.

Každý záznam .pdata pro ARM64 se délku 8 bajtů. Obecný formát jednotlivých záznamů míst RVA 32-bit funkce spustit v první slovo, a druhý s, který obsahuje ukazatel na .xdata proměnné délky bloku nebo sbalené aplikace word popisující odvíjení pořadí kanonické funkce.

![rozložení záznamu .pdata](../build/media/arm64-exception-handling-pdata-record.png ".pdata záznam rozložení")

Pole jsou následující:

- **Funkce spuštění RVA** je adresa RVA 32-bit zahájení funkce.

- **Příznak** je 2 bitové pole, která určuje, jak interpretovat zbývajících 30 bitů druhý .pdata slova. Pokud **příznak** je 0, pak zbývající bity formulář **RVA informace o výjimce** (s nízkou dva bity implicitně 0). Pokud **příznak** je nenulová, zbývající bity formuláře **zabaleny Unwind Data** struktury.

- **Informace o výjimce adresu RVA** je adresa struktury výjimky proměnné délky informace uložené v části .xdata. Tato data musí být zarovnaná na 4 bajty.

- **Provedené zabalené Unwind Data** je komprimovaný popis operace nutné k provedení operace unwind z funkce, za předpokladu, že kanonickém tvaru. V tomto případě žádný záznam .xdata je povinný.

### <a name="xdata-records"></a>.xdata záznamů

Když sbalené unwind formátu není dostatečná k popisu odvíjení funkce, je nutné vytvořit záznam proměnné délky .xdata. Adresa tento záznam je uložen v druhé slovo .pdata záznamu. Formát .xdata je sbalené proměnné délky množinu slov:

![rozložení záznamu .xdata](../build/media/arm64-exception-handling-xdata-record.png ".xdata záznam rozložení")

Tato data rozdělená do čtyř oddílů:

1. 1 nebo 2 slov záhlaví popisující celkovou velikost struktury a poskytuje klíčové funkce data. Druhý slovo je k dispozici, pokud mají oba pouze **epilogu počet** a **slova kódu** pole jsou nastavena na hodnotu 0. Toto jsou bitových polí v záhlaví:

   a. **Funkce délka** je 18 bitové pole určující celková délka funkce bajtovou hodnotou 4. Pokud je větší než 1 milion funkce, musí k popisu funkce používá více záznamů pdata a xdata. Zobrazit [rozsáhlé funkce](#large-functions) části Další podrobnosti.

   b. **Ver** je 2 bitového pole s popisem verzi zbývající xdata. V době psaní tohoto textu je definována pouze verze 0 a proto nejsou povoleny hodnoty 1-3.

   c. **X** je 1bitového pole určující (1) přítomnosti nebo absenci (0) data výjimky.

   d. **Elektronické** je pole jeden bit označuje, že informace popisující jeden epilogu je zabalena do záhlaví (1) namísto toho, aby další obor slova novější (0).

   e. **Počet epilogu** je 5 bitové pole, která má dvě význam, v závislosti na stavu **E** bit:

      1. Pokud **E** je nastavena na hodnotu 0: Určuje počet celkový počet výjimek obory, které je popsáno v části 2. Pokud existuje více než 31 oborů ve funkci, pak bude **slova kódu** pole musí být nastaveno na hodnotu 0 označující, že je vyžadována word rozšíření.

      2. Pokud **E** je nastavená na 1, pak toto pole určuje index první unwind kód, který popisuje jeden a pouze epilogu.

   f. **Kód slova** je 5 bitové pole, která určuje počet slov 32-bit potřeby tak, aby obsahovala všechny kódy unwind sekce 4. Pokud potřebujete více než 31 slov (tj, více než 124 unwind bajtů kódu), pak toto pole musí být nastaveno na hodnotu 0 označující, že je vyžadována word rozšíření.

   g. **Rozšířené epilogu počet** a **rozšířené slova kódu** jsou pole 16 bitů a 8 bitů, respektive, které poskytují více místa pro kódování neobvykle velký počet epilogů nebo neobvykle velký počet unwind slova kódu. Word rozšíření obsahující tato pole se nachází pouze pokud **epilogu počet** a **slova kódu** pole v první slovo záhlaví jsou nastavena na hodnotu 0.

1. Po data výjimky Pokud **epilogu počet** není nula, je seznam informací o oborech epilogu zabaleny z nich se má u slov velká a uloženy v pořadí podle zvýšení počáteční posun. Každý obor obsahuje následující bits:

   a. **Posun Start epilogu** je 18 bitové pole s popisem posun v bajtech, dělený 4 epilogu vzhledem ke spuštění funkce

   b. **Res** je pole 4-bit vyhrazené pro budoucí rozšíření. Hodnotou musí být 0.

   c. **Start Index epilogu** je 10-bit (2 většího počtu bitů než **rozšířené slova kódu**) označující bajtový index prvního pole unwind kód, který popisuje toto epilogu.

1. Po vstupu do seznamu oborů epilogu pole bajtů, které obsahují kódy unwind podrobně popsány v další části. Toto pole je, aby bylo vytvořeno po uplynutí na nejbližší hranici úplné slovo. Bajty jsou uloženy v pořadí little endian, takže může být přímo načíst v režimu little endian.

1. Nakonec po unwind kód bajtů (a pokud **X** bitu v hlavičce byla nastavena na 1) obsahuje informace o výjimce obslužné rutiny. Tento postup se skládá z jednoho **RVA obslužné rutiny výjimek** poskytuje adresu obslužná rutina výjimky, okamžitě následován proměnné délky množství dat nutnému obslužnou rutinou výjimky.

Výše uvedené .xdata záznamu je navržená tak, že je možné načíst první 8 bajtů a z té compute na plnou velikost záznamu (minus délka data výjimky proměnlivé velikosti, který následuje). Následující fragment kódu vypočítá velikost záznamu:

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

Je třeba poznamenat, že i když prologu a epilogu každý má své vlastní se budou indexovat kódy unwind, v tabulce se sdílí mezi nimi a je šíři (a ne úplně neobvyklé), můžete všechny sdílejí stejné kódy (viz příklad 2 v dodatku A níže). Autorům by měla optimalizovat pro tento případ, zejména protože nejvyšší index, který se dá nastavit je 255, tím omezíte celkový počet kódy unwind pro určité funkce.

### <a name="unwind-codes"></a>Parsovat kódy unwind

Pole kódy unwind je fond sekvence, které popisují, jak přesně vrátit zpět účinky prologu v pořadí, ve kterém potřebujete nevratná operace. Kódy unwind můžete představit jako mini instrukční sadu, kódovaný jako řetězec bajtů. Po dokončení provádění zpětná adresa pro volání funkce je v registru lr a obnoví všechny stálé registrů se jejich hodnoty v době, kdy byla volána funkce.

Pokud výjimky byla zaručeno, že vždy jen ke kterým dochází v těle funkce (a nikdy se prologu nebo epilogu žádné), pak bude nezbytné pouze jednoho pořadí. Odvíjení model Windows ale vyžaduje, že budeme moct vrátit zpět z v rámci částečně provedeného kódu prologu nebo epilogu. Aby mohla pojmout tento požadavek, kódy unwind byly pečlivě navrženy tak, aby se jednoznačně mapování 1:1 na každý relevantní operační kód prologu a epilogu. To má vliv na několik:

1. Podle počtu kódy unwind, je možné vypočítat délku kódu prologu a epilogu.

1. Podle počtu pokynů po spuštění epilogu oboru, je možné přeskočit ekvivalentní počet kódy unwind a provést zbývající části sekvence dokončit částečně spouštěné unwind fungování epilogu.

1. Podle počtu pokynů před koncem prologu, je možné přeskočit ekvivalentní počet kódy unwind a provést zbývající části sekvence vrátit pouze ty části úvodní části, které se dokončí.

Podle následující tabulky jsou kódovány kódy unwind. Všechny kódy unwind jsou jedním/double byte, kromě toho, který přiděluje obrovské zásobníku. Existují zcela 21 unwind kód. Každý unwind kód mapy přesně jeden instrukce v kódu prologu/epilogu aby bylo možné povolit pro uvolnění částečně prováděnou Prology a epilogu funkce.

|Uvolnění kódu|Služba BITS a interpretace|
|-|-|
|`alloc_s`|000xxxxx: přidělovat malé zásobníku s velikostí \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz: Uložit \<r19 r20 > pár [Z sp-# * 8]!, posun předem indexované > =-248 |
|`save_fplr`|        01zzzzzz: Uložit \<r29, lr > spárovat na [sp + #Z * 8], posun \<= 504. |
|`save_fplr_x`|        10zzzzzz: Uložit \<r29, lr > spárovat na [sp-(#Z + 1) * 8]!, posun předem indexované > = – 512 |
|`alloc_m`|        11000xxx "xxxxxxxx: přidělit velké zásobníku s velikostí \< 16 kB (2 ^ 11 * 16). |
|`save_regp`|        110010xx "xxzzzzzz: uložit dvojice r(19+#X) na [sp + #Z * 8], posun \<= 504 |
|`save_regp_x`|        110011xx "xxzzzzzz: uložit dvojice r(19+#X) na [sp-(#Z + 1) * 8]!, posun předem indexované > = – 512 |
|`save_reg`|        110100xx "xxzzzzzz: uložit reg r(19+#X) na [sp + #Z * 8], posun \<= 504 |
|`save_reg_x`|        1101010 x'xxxzzzzz: uložit reg r(19+#X) na [sp-(#Z + 1) * 8]!, posun předem indexované > =-256 |
|`save_lrpair`|         1101011 x'xxzzzzzz: uložit dvojice \<r19 + 2 *#X, lr > na [sp + #Z*8], posun \<= 504 |
|`save_fregp`|        1101100 x'xxzzzzzz: uložit dvojice d(8+#X) na [sp + #Z * 8], posun \<= 504 |
|`save_fregp_x`|        1101101 x'xxzzzzzz: uložit dvojice d(8+#X) na [sp-(#Z + 1) * 8]!, posun předem indexované > = – 512 |
|`save_freg`|        1101110 x'xxzzzzzz: uložit reg d(8+#X) na [sp + #Z * 8], posun \<= 504 |
|`save_freg_x`|        11011110' xxxzzzzz: uložit reg d(8+#X) na [sp-(#Z + 1) * 8]!, posun předem indexované > =-256 |
|`alloc_l`|         'xxxxxxxx"xxxxxxxx xxxxxxxx 11100000': přidělit velké zásobníku s velikostí \< 256 M (2 ^ 24 * 16) |
|`set_fp`|        11100001: nastavení r29: s: mov r29 sp |
|`add_fp`|        11100010' xxxxxxxx: nastavení r29 s: Přidat r29, sp, #x * 8 |
|`nop`|            11100011: žádné unwind operace je povinný. |
|`end`|            11100100: konec unwind kód. Zahrnuje ret v epilogu. |
|`end_c`|        11100101: konec unwind kódu v aktuálním oboru zřetězených. |
|`save_next`|        11100110: uložit další stálé Int nebo registr FP pár. |
|`arithmetic(add)`|    11100111' 000zxxxx: přidání souboru cookie reg(z) lr (0 = x28, 1 = sp); Přidat lr, lr, reg(z) |
|`arithmetic(sub)`|    11100111' 001zxxxx: sub reg(z) soubor cookie z lr (0 = x28, 1 = sp); Sub lr, lr, reg(z) |
|`arithmetic(eor)`|    11100111' 010zxxxx: eor lr pomocí souboru cookie reg(z) (0 = x28, 1 = sp); eor lr, lr, reg(z) |
|`arithmetic(rol)`|    11100111' 0110xxxx: simulované rol lr pomocí souboru cookie reg (x28); xip0 = neg x28; zkoušeného lr, xip0 |
|`arithmetic(ror)`|    11100111' 100zxxxx: zkoušeného lr pomocí souboru cookie reg(z) (0 = x28, 1 = sp); zkoušeného lr, lr, reg(z) |
| |            11100111: xxxz---:---vyhrazené |
| |              11101xxx: vyhrazené pro níže uvedené případy vlastní zásobníku, generují jenom pro asm rutiny |
| |              11101001: vlastní zásobníku pro MSFT_OP_TRAP_FRAME |
| |              11101010: vlastní zásobníku pro MSFT_OP_MACHINE_FRAME |
| |              11101011: vlastní zásobníku pro MSFT_OP_CONTEXT |
| |              1111xxxx: vyhrazené |

Nejvýznamnější bity pokyny s velkými hodnotami, které pokrývají více bajtů, jsou uloženy nejprve. Kódy unwind výše jsou navržené tak, aby jednoduše vyhledá první bajt kód, je možné vědět, celková velikost v bajtech kódu unwind. Vzhledem k tomu, že jednotlivé kódy unwind přesně je namapována na instrukce v kódu prologu/epilogu, Vypočítat velikost kódu prologu nebo epilogu, vše, co je potřeba udělat je pro vás od samého začátku pořadí za účelem použití vyhledávací tabulky nebo podobné zařízení k určení, jak dlouho se oprava odpovídá operační kód je.

Všimněte si, že po indexované posunu adresování nejsou povolené v prologu. Všechny rozsahy posunutí (#Z) odpovídat kódování, s výjimkou adresování STP/STR `save_r19r20_x` ve které 248 je dostatečná pro všechny oblasti (10 registrů Int + 8 registrů FP + 8 vstupní Registry) uložte.

`save_next` musí dodržujte uložení pro Int nebo FP volatile zaregistrovat pár: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x`, nebo jiné `save_next`. "Rostoucí" pořadí uloží další registrovaném páru na další slotu 16 bajtů. `save-next` Následující `save_next` , který označuje, že posledních pár registr Int odkazuje na první pár registr FP.

Protože velikost běžného vraťte a přeskočit pokyny jsou stejné, není nutné z oddělenými `end` kódu uvolnění pro volání funkce tail scénáře.

`end_c` je určen ke zpracování fragmenty nesouvislé funkce za účelem optimalizace. A `end_c` což označuje konec kódy unwind v aktuálním oboru musí být následován znakem další řady unwind kódu bylo dokončeno s reálné `end`. Kódy unwind mezi `end_c` a `end` představují prologu operace v nadřazená oblast ("fiktivní" prologu).  Další podrobnosti a příklady jsou popsány v následující části.

### <a name="packed-unwind-data"></a>Provedené zabalené unwind dat

Pro funkce, jejíž Prology a epilogu funkce použijte kanonický tvar je popsáno níže, balení unwind data je možné použít, musely zcela záznam .xdata a výrazně snižuje náklady na poskytnutí unwind data. Kanonické Prology a epilogu funkce jsou určeny ke splnění běžných požadavků jednoduchou funkci, která nevyžaduje, aby obslužná rutina výjimky a které provádí operace jeho nastavení a jejich vyřazování z provozu v standardní pořadí.

Formát záznamu .pdata se komprimovat komprimovaný objekt unwind dat vypadá nějak takto:

![unwind data .pdata záznam se komprimovat komprimovaný objekt](../build/media/arm64-exception-handling-packed-unwind-data.png ".pdata záznam se komprimovat komprimovaný objekt unwind dat")

Pole jsou následující:

- **Funkce spuštění RVA** je adresa RVA 32-bit zahájení funkce.
- **Příznak** je 2 bitové pole, jak je popsáno výše, s následující význam:
  - 00 = sbalené unwind dat nepoužívá; zbývající bity přejděte na záznam .xdata níže
  - 01 = sbalené unwind dat použít, jak je popsáno níže pomocí jednoho kódu prologu a epilogu na začátek a konec rozsahu
  - 10 = sbalené unwind dat použít, jak je popsáno níže pro kód bez jakékoli kódu prologu a epilogu; To je užitečné pro popis segmentů oddělených funkce.
  - 11 = vyhrazené;
- **Funkce délka** je pole 11bitový poskytuje délka celou funkci bajtovou hodnotou 4. Pokud funkce je větší než 8 kB, záznam úplné .xdata musí použít.
- **Velikost rámce** je pole 9bitové označující počet bajtů zásobníku, který je přidělen pro tuto funkci dělený 16. Funkce, které přidělují větší (8 kb – 16) bajtů zásobníku musí používat úplnou .xdata záznam. To zahrnuje proměnné místní, odchozí oblasti parametrů, volaný – uložené Int a FP oblasti a oblasti domovské parametrů, s výjimkou oblasti dynamického přidělení.
- **Znak CR** je 2bitový příznak označující, zda funkce zahrnuje další pokyny k nastavení rámce řetězec a vrácení odkazu:
  - 00 = unchained funkce \<r29, lr > pár není uložená v zásobníku.
  - 01 = unchained funkce \<lr > je uloženo v zásobníku
  - 10 = vyhrazené;
  - 11 = zřetězené funkce instrukce pár úložiště/zatížení se používá v kódu prologu/epilogu \<r29, lr >
- **H** ukládání na začátku funkce je 1bitový příznak označující, zda funkce homes parametr celočíselné registry (r0 – r7). (0 = není domácí registrů, 1 = domovů Registry).
- **RegI** je 4 bitového pole určující počet stálé INT registrů (r19 r28) uloží do umístění zásobníku canonical.
- **RegF** je 3bitová pole určující počet FP stálé registrů (d8 d15) uloží do umístění zásobníku canonical. (0 = žádný FP registr uložen, m > 0: m + 1 FP registrů se uloží). Pro funkci uložit jenom jeden registr FP zabaleny unwind dat nelze použít.

Canonical Prology, které spadají do kategorie 1, 2 (bez odchozí oblasti parametrů), 3 a 4 výše v části může být reprezentována sbalené unwind formátu.  Epilogů kanonické funkce podle velmi podobné formuláře, s výjimkou **H** nemá žádný vliv `set_fp` instrukce je vynechán, a jsou v epilogu obrácený pořadí kroků, jakož i pokyny v každém kroku. Algoritmus pro komprimovaný xdata následující postup podrobně popsané v následující tabulce:

Krok 0: Proveďte předběžné výpočet velikosti každé oblasti.

Krok 1: Uložení Int volaný – uložené registry.

Krok 2: Tento krok je specifické pro typ 4 v dřívější části. LR je uložen na konci Int oblasti.

Krok 3: Uložení FP volaný – uložené registry.

Krok 4: Uložení vstupní argumenty v oblasti domovské parametrů.

Krok 5: Přidělit zbývající problematiku, včetně místních, \<r29, lr > párování a odchozí oblasti parametrů. 5a odpovídá typu kanonickém 1. 5b a 5c jsou určené pro kanonický typu 2. 5d a 5e jsou pro oba typy 3 a 4 zadejte.

Krok #|Nastavení příznaku|# instrukcí|Operační kód|Uvolnění kódu
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **regI** < = 10|RegI / 2 + **RegI** % 2|`stp r19,r20,[sp,#savsz]!`<br/>`stp r21,r22,[sp,16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**ZNAK CR**== 01 *|1|`str lr,[sp, #intsz-8]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1) / 2 +<br/>(RegF + 1) % 2).|`stp d8,d9,[sp, #intsz]`\*\*<br/>`stp d10,d11,[sp, #intsz+16]`<br/>`...`<br/>`str d(8+RegF),[sp, #intsz+#fpsz-8]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp r0,r1,[sp, #intsz+#fpsz]`<br/>`stp r2,r3,[sp, #intsz+#fpsz+16]`<br/>`stp r4,r5,[sp, #intsz+#fpsz+32]`<br/>`stp r6,r7,[sp, #intsz+#fpsz+48]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**Znak CR** == 11 & & #locsz<br/> < = 512|2|`stp r29,lr,[sp,-#locsz]!`<br/>`mov r29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**ZNAK CR** == 11 &AMP; &AMP;<br/>512 < #locsz < =. 4088|3|`sub sp,sp, #locsz`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**Znak CR** == 11 & &. #locsz > 4088|4|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \| \| **CR**== 01) &AMP; &AMP;<br/>#locsz < =. 4088|1|`sub sp,sp, #locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \| \| **CR**== 01) &AMP; &AMP;<br/>#locsz >. 4088|2|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Pokud **CR** == 01 a **RegI** je číslo liché, krok 2 a poslední save_rep v kroku 1 jsou sloučeny do jednoho save_regp.

\*\* Pokud **RegI** == **CR** == 0, a **RegF** ! = 0, první stp pro plovoucí desetinné čárky snížením.

\*\*\* Žádné instrukce odpovídající `mov r29, sp` je k dispozici v epilogu. Provedené zabalené funkce vyžaduje obnovení sp z r29, využijeme nelze-li vrátit se zpět data.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Odvíjení částečné Prology a epilogu funkce

Nejběžnější odvíjení situace patří, kde výjimky nebo volání došlo k chybě v těle funkce od prologu a epilogu všechny funkce. V takovém případě odvíjení je jednoduchý: unwinder jednoduše začne spouštět kód v unwind začínající na indexu 0 a budete pokračovat, dokud se zjistí operační kód ukončení.

Je obtížné správně vrátit se zpět v případě, kdy k výjimce nebo přerušení dochází při provádění kódu prologu nebo epilogu. V těchto situacích je pouze částečně vytvořen rámec zásobníku a zdvih je určit přesně co bylo provedeno aby bylo možné správně vrátit zpět.

Jako příklad může postupujte této sekvence prologu a epilogu:

```asm
0000:    stp    r29, lr, [sp, -256]!        // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,224]              // save_fregp 0, 224
0008:    stp    r19,r20,[sp,240]            // save_regp 0, 240
000c:    mov    r29,sp                      // set_fp
         ...
0100:    mov    sp,r29                      // set_fp
0104:    ldp    r19,r20,[sp,240]            // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    r29, lr, [sp, -256]!        // save_fplr_x  256 (post-indexed load)
0110:    ret     lr                         // end
```

Vedle každé operační kód je vhodné unwind kód, který popisuje tuto operaci. První věc, kterou si je, že se série kódy unwind pro prologu přesné zrcadlový obraz unwind kódy epilog (nepočítají poslední instrukce epilogu). To je běžné situace a z tohoto důvodu unwind kódy pro prologu jsou vždy předpokládá, že mají být uloženy v obráceném pořadí z pořadí zpracování prologu.

Proto pro sekvence prologu a epilogu, jsme se připojíme společnou sadu kódy unwind:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Počínaje případ epilogu (více jednoznačné, jak vypadá v normální pořadí), na posunu 0 v rámci epilogu (která začíná na posunu 0x100 ve funkci), by Očekáváme, že k provedení úplné unwind pořadí, jak se ještě neprovedlo žádné čištění. Pokud se nám najít vyzkoušíme jedné instrukce v (na pozici 2 v epilogu), budeme úspěšně unwind přeskočením první kód unwind. Zobecňuje se této situaci, za předpokladu, že mapování 1:1 mezi operačních kódů a kódy unwind jsme může stát, že pokud jsme odvíjení n instrukce v epilogu jsme měli přeskočit první kódy n unwind a spusťte skript z něj.

Ukázalo se, že podobnou logiku funguje pro sekvence prologu, s výjimkou v opačném pořadí. Pokud jsme se návrat zpět z posunu 0 v úvodní části, chceme by provést žádnou akci. Pokud jsme zachytila počínaje posunutím 2, což je jedna instrukce v a pak by chceme spustit provádění kódu jeden unwind unwind pořadí od konce (Nezapomeňte, že kódy jsou uložené v obráceném pořadí). A tady příliš jsme můžete zobecnit, pokud jsme odvíjení n instrukce v prologu by měl začneme provádění kódy n unwind od konce seznamu kódů.

Nyní není vždy případě, že kód prologu a epilogu přesně shodovat. Z tohoto důvodu může musejí obsahovat několik pořadí kódy unwind pole. K určení posunu kde začít, zpracovávání kódech, pomocí následujícího postupu:

1. Pokud návrat zpět z v rámci těla funkce, jednoduše spusťte skript kódy unwind na pozici 0 a pokračovat až do dosažení operační kód "end".

1. Pokud návrat zpět z v rámci epilogu, použijte konkrétní epilogu počáteční index s rozsahem epilogu jako výchozí bod k dispozici. Kolik bajtů dotyčný počítač je od samého začátku epilogu služby COMPUTE. Pak přejděte vpřed prostřednictvím kódy unwind kódy unwind přeskakuje, dokud všechny už provedli pokyny jsou zahrnuté. Pak proveďte spuštění v tomto okamžiku.

1. Pokud návrat zpět z v rámci prologu, použijte jako výchozí bod index 0. Výpočetní délky kódu prologu z pořadí a pak výpočetní kolik bajtů dotyčný počítač se od konce prologu. Pak přejděte vpřed prostřednictvím kódy unwind kódy unwind přeskakuje, dokud všechny nebyl dosud proveden pokyny jsou zahrnuté. Pak proveďte spuštění v tomto okamžiku.

V důsledku těchto pravidel kódy unwind prologu musí být vždy první pole a jsou také kódy používané k provedení operace unwind v obecné případ návrat zpět z v rámci těla. Ihned po postupujte podle jakékoli sekvencí kódu epilogu specifické.

### <a name="function-fragments"></a>Fragmenty – funkce

Pro účely optimalizace kódu a z jiných důvodů může být vhodné rozdělit funkce do oddělených fragmenty (také nazývané oblasti). Když to uděláte, každý výsledný fragment funkce vyžaduje vlastní samostatný .pdata (a případně .xdata) záznam.

Pro oddělené sekundární fragment, který má svou vlastní sekvence prologu očekává se, že žádný zásobník úpravy se provádí v jeho prologu. Všechny požadované sekundárním místo zásobníku oblasti musí být předem přiděleny podle její nadřazená oblast (nebo názvem hostitele oblasti). Manipulace s ukazatel zásobníku takto zachová výhradně v původní prologu funkce.

Je obvyklý případ z funkce fragmenty "code oddělení" s, kterou kompilátor může přesunout oblasti kódu mimo svou funkci hostitele. Existují tři neobvyklé případů, které může být výsledkem je podle oddělení kódu.

#### <a name="example"></a>Příklad:

- (oblast 1: začněte)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (oblast 1: ukončení)
- (oblast 3: začněte)

    ```asm
        ...
    ```

- (oblast 3: ukončení)
- (2 oblasti: začněte)

    ```asm
    ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (2 oblasti: ukončení)

1. Pouze prolog (oblast 1: epilogu všechny funkce jsou v oddělených oblastech):

   Pouze prologu musí být popsány. To nemůže být reprezentována compact .pdata formátu. V případě úplné .xdata to může být reprezentován nastavování počet epilogu = 0. Zobrazit oblast 1 v předchozím příkladu.

   Parsovat kódy unwind: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Pouze epilogů (oblast 2: prologu je v oblasti hostitele)

   Předpokládá se, že ovládací prvek čas přechod do této oblasti, všechny kódy prologu spustily. Částečné unwind může dojít v epilogů stejném principu jako normální funkce. Tento typ oblasti nemůže být reprezentována compact .pdata. V záznamu o úplné xdata, může být zakódován pomocí "fiktivní" prologu, uváděn v závorkách `end_c` a `end` unwind pár kódu.  Úvodního `end_c` označuje velikost kódu prologu je nula. Index v jedné epilogu bodů, do počátečního epilogu `set_fp`.

   Kódu uvolnění pro oblast 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Žádné Prology nebo který (oblast 3: Prology a epilogu všechny funkce jsou v jiné fragmenty):

   Kompaktní .pdata formátu lze použít prostřednictvím nastavení příznaku = 10. S plnou .xdata záznamem, počet epilogu = 1. Unwind – kód je stejný jako v případě oblast 2 výše, ale epilogu Start Index také odkazuje na `end_c`. Částečné unwind nikdy dojde v této oblasti kódu.

Další možnost je složitější funkce fragmentů, ve kterých je "zmenšují zabalení", kterou kompilátor můžete odložit ukládání některé volaný – uložené registry dokud mimo položky prologu funkce.

- (oblast 1: začněte)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (2 oblasti: začněte)

    ```asm
        stp     r21,r22,[sp,224]        // save_regp 2, 224
        ...
        ldp     r21,r22,[sp,224]        // save_regp 2, 224
    ```

- (2 oblasti: ukončení)

    ```asm
        ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (oblast 1: ukončení)

Místo v zásobníku je v prologu oblast 1 předběžně přidělit. Mějte na paměti, že tuto oblast 2 budou mít stejné unwind kód, který ještě je přesunut mimo jeho funkce hostitele.

Oblast 1: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` s epilogu Start Index odkazuje na `set_fp` jako obvykle.

Oblast 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`. Epilogu Start Index odkazuje na první kódu uvolnění `save_regp 2, 224`.

### <a name="large-functions"></a>Rozsáhlé funkce

Fragmenty můžete využít k popisu funkce, které jsou větší než omezení milionu stanovené bitových polí v záhlaví .xdata. K popisu velmi velké funkce tímto způsobem, jednoduše musí být rozdělená do fragmenty menší než 1 milion. Každý fragment je třeba upravit tak, aby rozdělí epilogu není na více místech.

Pouze první fragment funkce bude obsahovat sekvence prologu; Další fragmenty jsou označené jako bez kódu prologu. V závislosti na počtu epilogu funkce, které jsou k dispozici každý fragment může obsahovat nula nebo více epilogu funkce. Uvědomte si, že každý obor epilogu v fragment Určuje počáteční posun vzhledem k začátku fragment, nikoli začátku funkci.

Pokud je fragment bez kódu prologu a epilogu žádné, nadále vyžaduje svou vlastní .pdata (a případně .xdata) záznam, který popisuje, jak vrátit zpět z v rámci těla funkce.

## <a name="examples"></a>Příklady

### <a name="example-1-frame-chained-compact-form"></a>Příklad 1: Zřetězená rámce compact tvaru

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Příklad 2: Zřetězená rámce úplném tvaru s zrcadlení kódu prologu a epilogu

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

Všimněte si, že EpilogStart Index [0] odkazuje na stejnou sekvenci kódu prologu unwind.

### <a name="example-3-variadic-unchained-function"></a>Příklad 3: Unchained Variadické funkce

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

Poznámka: EpilogStart Index [4] odkazuje na uprostřed unwind kód prologu (částečně opakované použití unwind pole).

## <a name="see-also"></a>Viz také:

[Přehled konvencí ARM64 ABI](arm64-windows-abi-conventions.md)<br/>
[Zpracování výjimek ARM](../build/arm-exception-handling.md)
