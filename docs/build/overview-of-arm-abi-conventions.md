---
title: Přehled konvencí ABI pro ARM
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 176aaaa17af1ce358255ca94eaccc7d5217f2a87
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303194"
---
# <a name="overview-of-arm32-abi-conventions"></a>Přehled konvencí ARM32 ABI

Binární rozhraní aplikace (ABI) pro kód kompilovaný pro Windows na procesorech ARM je založené na standardu ARM EABI. Tento článek popisuje hlavní rozdíly mezi Windows na ARM a standardem. Tento dokument popisuje ARM32 ABI. Informace o ARM64 ABI najdete v tématu [Přehled ARM64ch konvencí ABI](arm64-windows-abi-conventions.md). Další informace o standardu ARM EABI naleznete v tématu [Application Binary Interface (ABI) pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externí odkaz).

## <a name="base-requirements"></a>Základní požadavky

Systém Windows na ARM předpokládá, že je neustále spuštěný v architektuře ARMv7. Podpora plovoucí desetinné čárky ve formátu VFPv3-D32 nebo vyšší musí být přítomna v hardwaru. VFP musí podporovat hardware s jednoduchou přesností a dvojitou přesností s plovoucí desetinnou čárkou. Prostředí Windows Runtime nepodporuje emulaci s plovoucí desetinnou čárkou, aby bylo možné spouštět na VFPm hardwaru.

Podpora rozšíření NEON (Advanced SIMD Extensions) – zahrnuje i operace s plovoucí desetinnou čárkou – musí být také přítomny v hardwaru. Není k dispozici žádná podpora pro emulaci za běhu.

Podpora dělení celočíselného čísla (UDIV/SDIV) se důrazně doporučuje, ale není potřeba. Na platformách, které chybí podpora celočíselného dělení, může dojít ke snížení výkonu, protože tyto operace musí být zachyceny a případně opraveny.

## <a name="endianness"></a>Endianitou

Systém Windows na ARM se spustí v režimu Little endian. Kompilátor MSVC i prostředí Windows Runtime očekávají data ve Little endian. I když SETEND instrukcí v architektuře ARM podporuje i kód v uživatelském režimu pro změnu aktuální služby endian, tak se to nedoporučuje, protože je pro aplikaci nebezpečné. Pokud je výjimka vygenerována v režimu big endian, chování je nepředvídatelné a může vést k chybě aplikace v uživatelském režimu nebo v režimu jádra kontroly chyb.

## <a name="alignment"></a>Zarovnání

I když systém Windows umožňuje, aby hardware ARM zpracovával nesprávně zarovnané celočíselné přístupy, chyby zarovnání se v některých situacích pořád generují. Pro zarovnání použijte tato pravidla:

- Celočíselné načítání a ukládání v polovičním formátu (16 bitů) a velikost slov (v 32) není nutné zarovnávat. Hardware je efektivně zpracovává a transparentně.

- Načítání a ukládání s plovoucí desetinnou čárkou se musí zarovnávat. Jádro zpracovává nezarovnané zatížení a úložiště transparentně, ale s významnou režií.

- Musí být zarovnaná operace Load nebo Store Double (LDRD/STRD) a vícenásobné operace (LDM/STM). Jádro zpracovává většinu těchto prostředků transparentně, ale s významnou režií.

- Všechna přístup k neuložené paměti musí být zarovnaná, i pro přístup typu Integer. Nezarovnaný přístup způsobí chybu zarovnání.

## <a name="instruction-set"></a>Sada instrukcí

Sada instrukcí pro Windows v ARM je výhradně omezená na palec – 2. Očekává se, že veškerý kód spuštěný na této platformě se spustí a zůstane v režimu povýšení. Pokus o přepnutí do starší sady instrukcí ARM může být úspěšný, ale v případě, že dojde k jakýmkoli výjimkám nebo přerušením, může dojít k selhání aplikace v uživatelském režimu nebo k chybám v režimu jádra.

Vedlejším účinkem tohoto požadavku je, že všechny ukazatele kódu musí mít nízkou bitovou sadu. To znamená, že když jsou načteny a větvení přes BLX nebo BX, procesor zůstane v režimu povýšení a nepokusí se spustit cílový kód jako instrukce pro procesory ARM 32-bit.

### <a name="it-instructions"></a>Pokyny pro IT

Použití instrukcí v oddělení IT v kódu pro palec – 2 není povoleno s výjimkou těchto specifických případů:

- Instrukce IT se dá použít jenom k úpravě jedné cílové instrukce.

- Instrukce target musí být 16bitová instrukce.

- Instrukce target musí být jedna z následujících:

   |16bitové operační kódy|Třída|Omezení|
   |---------------------|-----------|------------------|
   |MOV, MVN|Přesunutí|RM! = počítač, RD! = počítač|
   |LDR, LDR[S]B, LDR[S]H|Načíst z paměti|Ale nejedná se o literálové formuláře LDR.|
   |STR, PARAMETRU STRB, STRH|Ukládat do paměti||
   |ADD, ADC, RSB, MEZIPAMĚŤ SOFTWAROVÉ SBĚRNICE, SUB|Přidat nebo odečíst|Ale ne doplňky/SUB SP, SP, imm7 Forms<br /><br /> RM! = PC, RDN! = PC, RDM! = PC|
   |CMP, CMN|Porovnán|RM! = PC, RN! = počítač|
   |MUL|Hodnotou||
   |ASR, LSL, LSR, ROR|Bitový posun||
   |A, BIC, EOR, ORR, TST|Bitové aritmetické operace||
   |BX|Větev k registraci|RM! = počítač|

I když aktuální procesory ARMv7 nemůžou hlásit použití nepovolených formulářů instrukcí, očekává se budoucí generace. Pokud jsou tyto formuláře zjištěny, mohou být všechny programy, které je používají, ukončeny nedefinovanou výjimkou instrukcí.

### <a name="sdivudiv-instructions"></a>Pokyny pro SDIV/UDIV

Použití instrukcí celočíselného dělení SDIV a UDIV je plně podporované, i na platformách bez nativního hardwaru pro jejich zpracování. Režie na SDIV nebo UDIV rozdělení na procesor Cortex je přibližně 80 cyklů, a to v závislosti na tom, 20-250 Jaké jsou vstupy.

## <a name="integer-registers"></a>Celočíselné registry

Procesor ARM podporuje 16 celých celočíselných registrů:

|Registr|Permanentní?|Role|
|--------------|---------------|----------|
|r0|Permanentní|Parametr, Result, Scrat registr 1|
|r1|Permanentní|Parametr, Result, Scrat zápis 2|
|r2|Permanentní|Parametr, Scrat registr 3|
|r3|Permanentní|Parametr, Scrat registr 4|
|R4|Bez volatile||
|r5|Bez volatile||
|r6|Bez volatile||
|r7|Bez volatile||
|R8|Bez volatile||
|r9|Bez volatile||
|r10|Bez volatile||
|r11|Bez volatile|Ukazatel na rámec|
|r12|Permanentní|V rámci procedur – vytočit nový zápis|
|r13 (SP)|Bez volatile|Ukazatel zásobníku|
|r14 (LR)|Bez volatile|Registrovat odkaz|
|r15 (PC)|Bez volatile|Čítač programu|

Podrobnosti o tom, jak používat parametr a návratové hodnoty, naleznete v části předávání parametrů v tomto článku.

Systém Windows používá R11 pro rychlé procházení rámce zásobníku. Další informace najdete v části procházení zásobníku. Z důvodu tohoto požadavku musí R11 ukazovat na nejvyšší odkaz v řetězu. Nepoužívejte R11 pro obecné účely – váš kód při analýze negeneruje správné procházení zásobníku.

## <a name="vfp-registers"></a>Registry VFP

Windows podporuje jenom varianty ARM, které mají podporu koprocesorů VFPv3-D32. To znamená, že registry s plovoucí desetinnou čárkou jsou vždy přítomny a lze je použít pro předávání parametrů a že je k dispozici úplná sada 32 registrů pro použití. Registry VFP a jejich využití jsou shrnuté v této tabulce:

|Jednoduchou|Double – prvky|Quad|Permanentní?|Role|
|-------------|-------------|-----------|---------------|----------|
|s0-s3|d0-d1|q0|Permanentní|Parametry, výsledek, Scrat zápis|
|s4-s7|d2-d3|q1|Permanentní|Parametry, nový registrační registr|
|s8-s11|d4-d5|q2|Permanentní|Parametry, nový registrační registr|
|s12-s15|d6-d7|q3|Permanentní|Parametry, nový registrační registr|
|s16-s19|d8-d9|q4|Bez volatile||
|s20-s23|d10-d11|q5|Bez volatile||
|s24-s27|d12-d13|q6|Bez volatile||
|s28-s31|d14-d15|q7|Bez volatile||
||d16-d31|q8-q15|Permanentní||

Další tabulka ilustruje stav a kontrolní registr s plovoucí desetinnou čárkou (FPSCR) bitová pole:

|Bity|Význam|Permanentní?|Role|
|----------|-------------|---------------|----------|
|31-28|NZCV|Permanentní|Příznaky stavu|
|27|QC|Permanentní|Kumulativní sytost|
|26|AHP|Bez volatile|Alternativní ovládací prvek s poloviční přesností|
|25|ROZLIŠUJÍCÍ NÁZEV|Bez volatile|Výchozí ovládací prvek režimu NaN|
|24|FZ|Bez volatile|Řízení režimu vyprázdnění na nulu|
|23-22|RMode|Bez volatile|Ovládací prvek režimu zaokrouhlování|
|21-20|Mezer|Bez volatile|Vektorová rozteč, musí vždy být 0.|
|18-16|Funkce|Bez volatile|Délka vektoru, musí být vždy 0.|
|15, 12-8|IDE, IXE atd.|Bez volatile|Depeše výjimky povolit bity, musí být vždy 0|
|7, 4-0|IDC, IXC atd.|Permanentní|Příznaky kumulativní výjimky|

## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou čárkou

Většina hardwaru ARM nepodporuje výjimky s plovoucí desetinnou čárkou standardu IEEE. V případě variant procesoru, které mají hardwarové výjimky s plovoucí desetinnou čárkou, jádro systému Windows tiše tyto výjimky zachytí a implicitně je zakáže v registru FPSCR. Tím se zajistí normalizované chování napříč variantami procesoru. V opačném případě kód vyvinutý na platformě, která nemá podporu výjimek, může obdržet neočekávané výjimky, když běží na platformě, která má podporu výjimek.

## <a name="parameter-passing"></a>Předávání parametrů

Pro funkce, které nejsou variadické, Windows na ARM provede pravidla ARM pro předávání parametrů – to zahrnuje VFP a rozšířená rozšíření SIMD. Tato pravidla dodržují [Standard volání procedur pro architekturu ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), konsolidovaná s rozšířeními VFP. Ve výchozím nastavení jsou v registrech předány první čtyři celočíselné argumenty a až osm argumentů s plovoucí desetinnou čárkou nebo vektory a další argumenty jsou předány do zásobníku. Argumenty jsou přiřazeny k registrům nebo zásobníku pomocí tohoto postupu:

### <a name="stage-a-initialization"></a>Fáze A: inicializace

Inicializace je provedena právě jednou, před zahájením zpracování argumentu:

1. Další základní číslo registru (NCRN) je nastavené na R0.

1. Registry VFP jsou označeny jako nepřidělené.

1. Následující adresa skládaného argumentu (NSAA) je nastavená na aktuální SP.

1. Pokud je zavolána funkce, která vrátí výsledek v paměti, pak je adresa pro výsledek umístěna v r0 a NCRN je nastaven na R1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Fáze B: předběžné odsazení a rozšíření argumentů

Pro každý argument v seznamu se použije první pravidlo pro porovnání z následujícího seznamu:

1. Pokud je argumentem složený typ, jehož velikost nemůže být staticky určena volajícím i volaným, je argument zkopírován do paměti a nahrazen ukazatelem na kopii.

1. Pokud je argumentem bajt nebo 16bitové poloviční slovo, pak se jedná o nulové rozšíření nebo znaménko na 32 celé slovo, které se považuje za argument o velikosti 4 bajty.

1. Pokud je argumentem složený typ, jeho velikost se zaokrouhluje na nejbližší násobek 4.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Fáze C: přiřazení argumentů k registrům a zásobníku

U každého argumentu v seznamu jsou následující pravidla aplikována postupně, dokud není přidělen argument:

1. Pokud je argumentem typ VFP a existuje dostatek po sobě jdoucích VFP registrů příslušného typu, pak je argument přidělen na nejnižší počet sekvencí takových registrů.

1. Pokud je argumentem typ VFP, všechny zbývající nepřidělené Registry jsou označeny jako nedostupné. NSAA se upraví nahoru, dokud není správně zarovnán pro typ argumentu a argument je zkopírován do zásobníku v upraveném NSAA. NSAA se pak zvýší o velikost argumentu.

1. Pokud argument vyžaduje zarovnání 8 bajtů, NCRN se zaokrouhlí až na další číslo, které je sudé.

1. Pokud velikost argumentu v 32ových slovech není více než R4 minus NCRN, je argument zkopírován do základních registrů, počínaje NCRN, přičemž nejméně významné bity vybírají Registry s nižším číslem. NCRN se zvyšuje podle počtu využitých registrů.

1. Pokud je NCRN menší než R4 a NSAA je rovno SP, je argument rozdělen mezi základní registry a zásobník. První část argumentu je zkopírována do základních registrů, počínaje NCRN, až do a včetně R3. Zbývající část argumentu je zkopírována do zásobníku počínaje NSAA. NCRN je nastavená na R4 a NSAA se zvyšuje o velikost argumentu minus počet předaných v registrech.

1. Pokud argument vyžaduje zarovnání 8 bajtů, NSAA se zaokrouhlí na další adresu zarovnaná na 8 bajtech.

1. Argument je zkopírován do paměti v NSAA. NSAA se zvyšuje o velikost argumentu.

Registry VFP se nepoužívají pro funkce variadické a pravidla 1 fáze C a 2 jsou ignorována. To znamená, že funkce variadické může začínat nepovinným nabízeným vložením {r0-R3}, aby se argumenty registru předaly dalším argumentům předaným volajícím a pak měli přístup k celému seznamu argumentů přímo ze zásobníku.

Hodnoty celočíselného typu jsou vraceny v r0, volitelně rozšířené na R1 pro hodnoty 64 vracené zpět. Hodnoty VFP/NEON typu s plovoucí desetinnou čárkou nebo SIMD jsou v případě potřeby vráceny v S0, d0 nebo Q0.

## <a name="stack"></a>Rámec

Zásobník musí zůstat zarovnaný na 4 bajtech a musí být zarovnán na 8 bajtů na hranici funkce. Tato akce je nutná k podpoře častého použití propojených operací s 64 bitovými proměnnými zásobníku. EABI ARM uvádí, že zásobník je 8 bajtů zarovnaný na jakémkoli veřejném rozhraní. V případě konzistence se systém Windows na ARM vytvoří jako veřejné rozhraní a považuje se za hranice funkce.

Funkce, které musí používat ukazatel na rámec, například funkce, které volají `alloca` nebo které dynamicky mění ukazatel zásobníku – musí nastavit ukazatel na rámec v r11 ve funkci prologu a ponechat ho beze změny až do epilogu. Funkce, které nevyžadují ukazatel na rámec, musí provést všechny aktualizace zásobníku v prologu a nechat ukazatel zásobníku beze změny do epilogu.

Funkce, které přidělují 4 KB nebo více v zásobníku, musí zajistit, aby se všechny stránky před poslední stránkou dotkly v daném pořadí. Tím se zajistí, že žádný kód nemůže "přesměrovat" na stránku Guard, kterou systém Windows používá k rozšíření zásobníku. Obvykle je to prováděno pomocí pomocné rutiny `__chkstk`, která se předá celkovým přidělením zásobníku v bajtech dělený 4 v R4 a která vrací konečnou velikost přidělení zásobníku v bajtech zpátky v R4.

### <a name="red-zone"></a>Červená zóna

Oblast s 8 bajty hned pod aktuálním ukazatelem zásobníku je vyhrazena pro analýzu a dynamické opravy. To umožňuje, aby byl kód vložen pečlivě, což ukládá 2 Registry na [SP, #-8] a dočasně je používá pro libovolný účel. Jádro systému Windows zaručuje, že tyto 8 bajty nebudou přepsány, pokud dojde k výjimce nebo přerušení v uživatelském režimu i v režimu jádra.

### <a name="kernel-stack"></a>Zásobník jádra

Výchozí zásobník režimu jádra ve Windows je tři stránky (12 KB). Dejte pozor, abyste nevytvářeli funkce s velkými vyrovnávacími paměťmi zásobníku v režimu jádra. K přerušení může docházet s velmi malou rezervou zásobníku a způsobit nenouzové selhání zásobníku.

## <a name="cc-specifics"></a>C/C++ specifické

Výčty jsou 32 celočíselných typů, pokud alespoň jedna hodnota ve výčtu nevyžaduje 64 úložiště dvakrát-Word. V takovém případě je výčet povýšen na celočíselný typ, který je 64.

`wchar_t` je nastavené tak, aby byly rovnocenné `unsigned short`, aby se zachovala kompatibilita s jinými platformami.

## <a name="stack-walking"></a>Procházení zásobníku

Kód Windows je kompilován s povolenými ukazateli snímků ([/Oy (vynechání ukazatele na rámec)](reference/oy-frame-pointer-omission.md)) a umožňuje rychlé procházení zásobníku. Obecně platí, že registr R11 odkazuje na další odkaz v řetězci, což je dvojice {R11, LR}, která určuje ukazatel na předchozí snímek v zásobníku a návratovou adresu. Doporučujeme, aby váš kód také povolil ukazatele rámce pro lepší profilování a trasování.

## <a name="exception-unwinding"></a>Vrácení výjimky zpět

Odvinutí zásobníku během zpracování výjimky je povoleno pomocí unwind kódů. Unwind kódy jsou posloupnosti bajtů uložených v oddílu. xdata spustitelného obrázku. Popisují operaci prologu a kódu epilogu abstraktním způsobem tak, aby se účinky prologu funkce mohly vrátit zpět v přípravě pro vrácení zpět do rámce zásobníku volajícího.

EABI ARM určuje model unwind pro výjimku, který používá unwind kódy. Tato specifikace však není dostačující pro odvíjení v systému Windows, která musí zpracovávat případy, kde procesor je uprostřed prologu nebo epilogu funkce. Další informace o systému Windows na základě dat výjimky ARM a o tom, jak se odvíjí, najdete v tématu [zpracování výjimek v ARM](arm-exception-handling.md).

Doporučujeme, aby se dynamicky generovaný kód popsal pomocí tabulek dynamických funkcí zadaných v voláních do `RtlAddFunctionTable` a přidružených funkcí, aby se generovaný kód mohl zúčastnit zpracování výjimek.

## <a name="cycle-counter"></a>Čítač cyklů

Procesory ARM s Windows jsou potřebné k podpoře počítadla cyklu, ale použití čítače přímo může způsobovat problémy. Aby se tyto problémy předešly, Windows v ARM používá nedefinovaný operační kód pro vyžádání normalizované hodnoty počítadla 64 bitů. Z C nebo C++použijte vnitřní `__rdpmccntr64` k vygenerování příslušného operačního kódu; ze sestavení použijte instrukci `__rdpmccntr64`. Čtení počítadla cyklu trvá přibližně 60 cyklů v Cortex.

Čítač je skutečným počítadlem, nikoli hodinami. Proto se frekvence počítání liší od frekvence procesoru. Pokud chcete změřit uplynulý čas, použijte `QueryPerformanceCounter`.

## <a name="see-also"></a>Viz také:

[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Zpracování výjimek ARM](arm-exception-handling.md)
