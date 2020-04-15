---
title: Přehled konvencí ARM ABI
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 8737f7b1cbe0651b43eb3b9990a4035b60bd01b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320720"
---
# <a name="overview-of-arm32-abi-conventions"></a>Přehled úmluv ARM32 ABI

Binární rozhraní aplikace (ABI) pro kód kompilovaný pro Windows na procesorech ARM je založeno na standardníarm eabi. Tento článek upozorňuje na klíčové rozdíly mezi windows na ARM a standard. Tento dokument se vztahuje na ARM32 ABI. Informace o ARM64 ABI, viz [Přehled ARM64 ABI konvence](arm64-windows-abi-conventions.md). Další informace o standardní ARM EABI, naleznete [v tématu binární rozhraní aplikace (ABI) pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externí odkaz).

## <a name="base-requirements"></a>Základní požadavky

Systém Windows na ARM předpokládá, že je vždy spuštěn na architektuře ARMv7. Podpora s plovoucí desetinnou desetinnou tálicí ve formě VFPv3-D32 nebo novější musí být přítomna v hardwaru. VFP musí podporovat s jednou a dvojitou přesností plovoucí bod v hardwaru. Modul runtime systému Windows nepodporuje emulaci s plovoucí desetinnou tácekpou, která umožňuje spuštění na hardwaru, který není součástí vstřeba.

Pokročilá podpora rozšíření SIMD (NEON), která zahrnuje celočíselné i plovoucí bodové operace, musí být také přítomna v hardwaru. Není k dispozici žádná podpora emulace za běhu.

Podpora dělení celé číslo (UDIV/SDIV) se důrazně doporučuje, ale není vyžadována. Platformy, které postrádají podporu dělení celé číslo může vynakládat snížení výkonu, protože tyto operace musí být zachyceny a případně oprava.

## <a name="endianness"></a>Endianness

Systém Windows na ARM se spustí v režimu little-endian. Kompilátor MSVC a prostředí Runtime systému Windows očekávají vždy malá endianová data. Přestože setend instrukce v architektuře sady instrukcí ARM (ISA) umožňuje i kód uživatelského režimu změnit aktuální endianness, přitom se nedoporučuje, protože je to nebezpečné pro aplikaci. Pokud je výjimka generována v režimu big-endian, chování je nepředvídatelné a může vést k chybě aplikace v uživatelském režimu nebo kontrola chyb v režimu jádra.

## <a name="alignment"></a>Zarovnání

Přestože systém Windows umožňuje arm hardware pro zpracování nesprávně zarovnané celé číslo přístupy transparentně, zarovnání chyby stále mohou být generovány v některých situacích. Postupujte podle těchto pravidel pro zarovnání:

- Poloviční velikosti slova (16bitová) a word-velikosti (32bitové) celé zatížení a obchody nemusí být zarovnány. Hardware je zpracovává efektivně a transparentně.

- Zatížení a úložiště s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou Jádro zpracovává nezarovnaná zatížení a ukládá transparentně, ale s významnou režií.

- Načíst nebo uložit dvojité (LDRD/STRD) a více (LDM/STM) operace by měly být zarovnány. Jádro zpracovává většinu z nich transparentně, ale s významnou režií.

- Všechny přístupy k neuložené paměti musí být zarovnány, a to i pro celočíselné přístupy. Nezarovnané přístupy způsobují chybu zarovnání.

## <a name="instruction-set"></a>Sada instrukcí

Instrukční sada pro Windows na ARM je přísně omezena na Thumb-2. Očekává se, že veškerý kód spuštěný na této platformě se spustí a zůstane v režimu Thumb po celou dobu. Pokus o přepnutí do starší sady instrukcí ARM může být úspěšný, ale pokud ano, všechny výjimky nebo přerušení, ke kterým dojde, mohou vést k chybě aplikace v uživatelském režimu nebo ke kontrole chyb v režimu jádra.

Vedlejším účinkem tohoto požadavku je, že všechny ukazatele kódu musí mít nastaven nízký bit. Je to tak, že když jsou načteny a rozvětvené na přes BLX nebo BX, procesor zůstane v režimu Thumb a nepokusí se spustit cílový kód jako 32bitové pokyny ARM.

### <a name="it-instructions"></a>Pokyny k IT

Použití pokynů it v kódu thumb-2 je zakázáno s výjimkou těchto konkrétních případů:

- Instrukce IT lze použít pouze k úpravě jedné instrukce cíle.

- Instrukce cíle musí být 16bitová instrukce.

- Instrukce cíle musí být jedna z těchto:

   |16bitové operační kódy|Třída|Omezení|
   |---------------------|-----------|------------------|
   |MOV, MVN|Přesunout|Rm != PC, Rd != PC|
   |LDR, LDR[S]B, LDR[S]H|Načtení z paměti|Ale ne LDR literálové formy|
   |STR, STRB, STRH|Uložit do paměti||
   |PŘIDAT, ADC, RSB, SBC, SUB|Sčítání nebo odčítání|Ale ne ADD / SUB SP, SP, imm7 formuláře<br /><br /> Rm != PC, Rdn != PC, Rdm != PC|
   |CMP, CMN|Porovnání|Rm != PC, Rn != PC|
   |MUL|Násobení||
   |ASR, LSL, LSR, ROR|Bitposun||
   |A, BIC, EOR, ORR, TST|Bitová aritmetika||
   |Bx|Pobočka k registraci|Rm != PC|

Přestože aktuální procesory ARMv7 nemohou hlásit použití nepovolených formulářů instrukcí, očekává se, že budoucí generace. Pokud jsou tyto formuláře zjištěny, může být jakýkoli program, který je používá, ukončen s nedefinovanou výjimkou instrukce.

### <a name="sdivudiv-instructions"></a>Pokyny pro SDIV/UDIV

Použití instrukcí pro dělení celého čísla SDIV a UDIV je plně podporováno, a to i na platformách bez nativního hardwaru, který je zvládne. Režie na SDIV nebo UDIV rozdělit na cortex-A9 procesor je přibližně 80 cyklů, kromě celkové doby dělení 20-250 cyklů, v závislosti na vstupech.

## <a name="integer-registers"></a>Evidenční registry

Procesor ARM podporuje 16 evidorových registrů:

|Zaregistrovat|Těkavých?|Role|
|--------------|---------------|----------|
|r0|Těkavých|Parametr, výsledek, registr škrábanců 1|
|r1|Těkavých|Parametr, výsledek, scratch register 2|
|R2|Těkavých|Parametr, scratch register 3|
|r3|Těkavých|Parametr, poškrábání registr 4|
|R4|Nevolatilní||
|r5|Nevolatilní||
|r6|Nevolatilní||
|r7|Nevolatilní||
|R8|Nevolatilní||
|r9|Nevolatilní||
|r10|Nevolatilní||
|r11|Nevolatilní|Ukazatel snímku|
|r12|Těkavých|Registr stíracích losů v rámci procedury|
|r13 (Šp.)|Nevolatilní|Ukazatel zásobníku|
|r14 (LR)|Nevolatilní|Registr odkazů|
|r15 (PC)|Nevolatilní|Čítač programů|

Podrobnosti o použití registrů parametrů a vrácených hodnot naleznete v části Předávání parametrů v tomto článku.

Systém Windows používá r11 pro rychlou chůzi rámce zásobníku. Další informace naleznete v části Procházení zásobníku. Z důvodu tohoto požadavku r11 musí vždy odkazovat na nejvyšší článek v řetězci. Nepoužívejte r11 pro obecné účely – váš kód nebude generovat správné procházení zásobníku během analýzy.

## <a name="vfp-registers"></a>Registry VFP

Systém Windows podporuje pouze varianty ARM, které podporují koprocesor VFPv3-D32. To znamená, že registry s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou tázání majevky jsou vždy k dispozici a lze se na ně spolehnout při předávání parametrů a že je k dispozici úplná sada 32 registrů. Registry VFP a jejich použití jsou shrnuty v této tabulce:

|Singly|Double – prvky|Čtyřkolky|Těkavých?|Role|
|-------------|-------------|-----------|---------------|----------|
|s0-s3|d0-d1|q0|Těkavých|Parametry, výsledek, registr škrábanců|
|s4-s7|d2-d3|Q1|Těkavých|Parametry, žlápnutí|
|s8-s11|d4-d5|q2|Těkavých|Parametry, žlápnutí|
|s12-s15|d6-d7|q3|Těkavých|Parametry, žlápnutí|
|s16-s19|d8-d9|q4|Nevolatilní||
|s20-s23|d10-d11|q5|Nevolatilní||
|s24-s27|d12-d13|q6|Nevolatilní||
|s28-s31|d14-d15|q7|Nevolatilní||
||d16-d31|q8-q15|Těkavých||

Následující tabulka znázorňuje bitová pole stavu a ovládacího registru s plovoucí desetinnou desetinnou a řídicí matnou (FPSCR):

|Bity|Význam|Těkavých?|Role|
|----------|-------------|---------------|----------|
|31-28|NZCV|Těkavých|Příznaky stavu|
|27|QC|Těkavých|Kumulativní nasycení|
|26|Ahp|Nevolatilní|Alternativní polopřesné řízení|
|25|Dn|Nevolatilní|Výchozí řízení režimu NaN|
|24|Fz|Nevolatilní|Řízení režimu flush-to-zero|
|23-22|Režim R|Nevolatilní|Ovládání režimu zaokrouhlení|
|21-20|Krok|Nevolatilní|Vektor krok, musí být vždy 0|
|18-16|Len|Nevolatilní|Vektordélka, musí být vždy 0|
|15, 12-8|IDE, IXE atd.|Nevolatilní|Soutisk výjimek povoluje bity, musí být vždy 0|
|7, 4-0|IDC, IXC atd.|Těkavých|Kumulativní příznaky výjimek|

## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou desetinnou tálicí

Většina arm hardware nepodporuje výjimky s plovoucí desetinnou desetinnou tácek. Na variantách procesoru, které mají výjimky s plovoucí desetinnou desetinnou tácekhardwary, jádro systému Windows tiše zachytí výjimky a implicitně je zakáže v registru FPSCR. Tím je zajištěno normalizované chování napříč variantami procesoru. Jinak kód vyvinutý na platformě, která nemá podporu výjimek může získat neočekávané výjimky při spuštění na platformě, která má podporu výjimek.

## <a name="parameter-passing"></a>Předávání parametrů

U nevariadických funkcí se systém Windows na ARM ABI řídí pravidly ARM pro předávání parametrů – to zahrnuje rozšíření VFP a Advanced SIMD. Tato pravidla se řídí [standardem volání procedur pro architekturu ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), konsolidovaným s rozšířeními VFP. Ve výchozím nastavení první čtyři celočíselné argumenty a až osm argumentů s plovoucí desetinnou nebo vektorovou jsou předány v registrech a další argumenty jsou předány v zásobníku. Argumenty jsou přiřazeny k registrům nebo zásobníku pomocí tohoto postupu:

### <a name="stage-a-initialization"></a>Fáze A: Inicializace

Inicializace se provádí přesně jednou, než začne zpracování argumentů:

1. Číslo dalšího registru jádra (NCRN) je nastaveno na r0.

1. Registry VFP jsou označeny jako nepřidělené.

1. Adresa dalšího skládaného argumentu (NSAA) je nastavena na aktuální sp.

1. Pokud je volána funkce, která vrací výsledek v paměti, je adresa pro výsledek umístěna v r0 a NCRN je nastavena na hodnotu r1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Fáze B: Předpisování a rozšíření argumentů

Pro každý argument v seznamu se použije první pravidlo párování z následujícího seznamu:

1. Pokud je argument složený typ, jehož velikost nemůže být staticky určena volajícím i volaného, argument je zkopírován do paměti a nahrazen ukazatelem na kopii.

1. Pokud je argument bajt nebo 16bitové půlslovo, pak je nula rozšířené nebo znaménko rozšířené na 32bitové celé slovo a považovány za 4bajtový argument.

1. Pokud je argument složený typ, jeho velikost se zaokrouhlí nahoru na nejbližší násobek 4.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Fáze C: Přiřazení argumentů k registrům a zásobníku

Pro každý argument v seznamu se znovu použijí následující pravidla, dokud není argument přidělen:

1. Pokud argument je typ VFP a existuje dostatek po sobě jdoucích nepřidělených registrů VFP příslušného typu, je argument přidělen nejnižší číslované posloupnosti těchto registrů.

1. Pokud je argument typu VFP, všechny zbývající nepřidělené registry jsou označeny jako nedostupné. NSAA je upravena směrem nahoru, dokud je správně zarovnán pro typ argumentu a argument je zkopírován do zásobníku na upravené NSAA. NSAA je pak zvýšil podle velikosti argumentu.

1. Pokud argument vyžaduje zarovnání o 8 bajtů, ncrn se zaokrouhlí nahoru na další sudé registrační číslo.

1. Pokud velikost argumentu v 32bitových slovech není větší než r4 mínus NCRN, argument je zkopírován do základních registrů počínaje NCRN, přičemž nejméně významné bity zabírají registry s nižšími čísly. NCRN se zintáží podle počtu použitých registrů.

1. Pokud NCRN je menší než r4 a NSAA se rovná SP, argument je rozdělen mezi základní registry a zásobníku. První část argumentu je zkopírována do základních registrů počínaje NCRN až po r3 včetně. Zbytek argumentu je zkopírován do zásobníku, počínaje NSAA. NCRN je nastavena na r4 a NSAA se zvětšuje podle velikosti argumentu minus částka předaná v registrech.

1. Pokud argument vyžaduje zarovnání o 8 bajtů, nsaa je zaokrouhlena nahoru na další adresu zarovnanou 8 bajtů.

1. Argument je zkopírován do paměti na NSAA. NSAA se zvětšuje podle velikosti argumentu.

Registry VFP se nepoužívají pro variadické funkce a pravidla fáze C 1 a 2 jsou ignorována. To znamená, že variadická funkce může začínat volitelnou push {r0-r3} pro předchlazení argumentů registru k dalším argumentům předaným volajícím a potom přistupovat k celému seznamu argumentů přímo ze zásobníku.

Hodnoty typu celé číslo jsou vráceny v r0, volitelně rozšířena na r1 pro 64bitové vrácené hodnoty. Hodnoty typu VFP/NEON s plovoucí desetinnou nebo SIMD jsou vráceny v s0, d0 nebo q0 podle potřeby.

## <a name="stack"></a>Zásobník

Zásobník musí zůstat vždy zarovnán o 4 bajty a musí být zarovnán o 8 bajtů na libovolné hranici funkce. To je nutné pro podporu častého používání propojených operací na 64bitové proměnné zásobníku. ARM EABI uvádí, že zásobník je 8 bajt zarovnán v libovolném veřejném rozhraní. Pro konzistenci systém Windows na ARM ABI považuje všechny hranice funkce za veřejné rozhraní.

Funkce, které mají použít ukazatel rámce – `alloca` například funkce, které volají nebo které dynamicky mění ukazatel zásobníku – musí nastavit ukazatel rámce v r11 v prologu funkce a ponechat jej beze změny až do epilogu. Funkce, které nevyžadují ukazatel rámce musí provádět všechny aktualizace zásobníku v prologu a ponechat ukazatel zásobníku beze změny, dokud epilogu.

Funkce, které přidělují 4 KB nebo více v zásobníku musí zajistit, že každá stránka před poslední stránku se dotkl v pořadí. Tím je zajištěno, že žádný kód může "přeskočit" stráž stránky, které systém Windows používá k rozšíření zásobníku. Obvykle se to provádí `__chkstk` pomocník, který je předán celkové přidělení zásobníku v bajtů děleno 4 v r4 a který vrátí konečné množství přidělení zásobníku v bajtů zpět v r4.

### <a name="red-zone"></a>Červená zóna

Oblast 8 bajtů bezprostředně pod aktuálním ukazatelem zásobníku je vyhrazena pro analýzu a dynamické opravy. To umožňuje pečlivě generovaný kód, který ukládá 2 registry na [sp, #-8] a dočasně je používá pro libovolné účely. Jádro systému Windows zaručuje, že těchto 8 bajtů nebude přepsáno, pokud dojde k výjimce nebo přerušení v uživatelském režimu i v režimu jádra.

### <a name="kernel-stack"></a>Zásobník jádra

Výchozí zásobník režimu jádra v systému Windows je tři stránky (12 kB). Dávejte pozor, abyste nevytvářeli funkce, které mají v režimu jádra vyrovnávací paměti s velkým zásobníkem. Přerušení může přijít s velmi malou stack headroom a způsobit kontrolu paniky zásobníku.

## <a name="cc-specifics"></a>Specifika c/c++

Výčty jsou 32bitové celočíselné typy, pokud alespoň jedna hodnota ve výčtu nevyžaduje úložiště s 64bitovými dvojitými slovy. V takovém případě je výčet povýšen na 64bitový celočíselný typ.

`wchar_t`je definována jako `unsigned short`rovnocenná , aby byla zachována kompatibilita s jinými platformami.

## <a name="stack-walking"></a>Procházení zásobníku

Kód systému Windows je kompilován s povolenými ukazateli rámce ([/Oy (Frame-Pointer Omission)](reference/oy-frame-pointer-omission.md)) pro umožnění rychlé hodování zásobníku. Obecně platí, že registr r11 odkazuje na další odkaz v řetězci, což je dvojice {r11, lr}, která určuje ukazatel na předchozí snímek v zásobníku a zpáteční adresu. Doporučujeme, aby váš kód také povolit ukazatele rámce pro lepší profilování a trasování.

## <a name="exception-unwinding"></a>Odvíjení výjimek

Odvíjení zásobníku během zpracování výjimek je povoleno použitím unwind kódů. Unwind kódy jsou posloupnost bajtů uložených v části .xdata spustitelnébit image. Popisují operaci prologu funkce a epilogu kódu abstraktním způsobem, takže účinky prologu funkce lze vrátit zpět v rámci přípravy na odvíjení do rámce zásobníku volajícího.

ARM EABI určuje model odvíjení výjimek, který používá unwind kódy. Tato specifikace však není dostatečná pro unwinding v systému Windows, který musí zpracovávat případy, kdy je procesor uprostřed prologu nebo epilogu funkce. Další informace o windows na data výjimky ARM a unwinding, naleznete v [tématu ARM Zpracování výjimek](arm-exception-handling.md).

Doporučujeme, aby dynamicky generovaný kód byl popsán pomocí `RtlAddFunctionTable` tabulek dynamických funkcí určených ve voláních a přidružených funkcích, aby se generovaný kód mohl účastnit zpracování výjimek.

## <a name="cycle-counter"></a>Čítač cyklů

Arm procesory se systémem Windows jsou nutné pro podporu čítače cyklu, ale pomocí čítače přímo může způsobit problémy. Chcete-li se těmto problémům vyhnout, systém Windows na ARM používá nedefinovaný operační kód k vyžádání normalizované hodnoty 64bitového cyklového čítače. Z Jazyka C nebo C++ použijte `__rdpmccntr64` vnitřní k vyzařují příslušný operační kód; z montáže, `__rdpmccntr64` použijte návod. Čtení čítače cyklu trvá přibližně 60 cyklů na Cortex-A9.

Čítač je skutečný cyklus čítač, nikoli hodiny; proto se frekvence počítání mění s frekvencí procesoru. Chcete-li měřit uplynulý čas hodin, použijte . `QueryPerformanceCounter`

## <a name="see-also"></a>Viz také

[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Zpracování výjimek ARM](arm-exception-handling.md)
