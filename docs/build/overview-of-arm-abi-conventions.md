---
title: Přehled konvencí ARM ABI | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e5ee2ddc29c2a014aceb8ac6356cae9e42a916d
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027320"
---
# <a name="overview-of-arm32-abi-conventions"></a>Přehled konvencí ARM32 ABI

Binárním rozhraním aplikace (ABI) pro kód zkompilovaný pro Windows na procesorech ARM je založen na standardní EABI ARM. Tento článek popisuje hlavní rozdíly mezi Windows na ARM a standard. Tento dokument popisuje ARM32 ABI. Informace o ARM64 ABI najdete v tématu [ABI ARM64 přehled konvencí](arm64-windows-abi-conventions.md). Další informace o standardní EABI ARM naleznete v tématu [aplikace binární rozhraní ABI () pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externí odkaz).

## <a name="base-requirements"></a>Základní požadavky

Windows na ARM předpokládá, že je spuštěn na architekturu ARMv7 za všech okolností. Podpora plovoucí desetinné čárky ve formuláři VFPv3 D32 nebo novější musí být součástí hardwaru. VFP musí podporovat jednoduchou přesností a dvojité přesnosti s plovoucí desetinnou čárkou v hardwaru. Modul Windows runtime nepodporuje emulaci plovoucí desetinné čárky k povolení spuštění na jiných VFP hardwaru.

Přidává rozšířenou podporu rozšíření SIMD (NEON) – jedná se o celé číslo a operací s plovoucí desetinnou čárkou, musí být k dispozici také v hardwaru. Nenabízí žádnou podporu runtime pro emulaci.

Podpora dělení celého čísla (UDIV/SDIV) je důrazně doporučujeme, ale nevyžaduje. Platformy, které neobsahují podporu dělení celého čísla může mít za následek snížení výkonu vzhledem k tomu, že tyto operace musí být zachycena a případně opravit.

## <a name="endianness"></a>Ukládání významných bajtů

Windows na ARM se spustí v režimu little endian. Kompilátor Visual C++ a prostředí Windows runtime očekávat, že data ve formátu little endian za všech okolností. I když sadu instrukcí SETEND v ARM instrukce architektury (ISA) umožňuje změnit aktuální endianitou kódu i uživatelského režimu, tím proto se nedoporučují, protože je nebezpečné pro aplikaci. Pokud je výjimka vygenerované v režimu formát big-endian chování nepředvídatelné a může vést selhání aplikace v uživatelském režimu nebo kontroly chyb v režimu jádra.

## <a name="alignment"></a>Zarovnání

Zarovnání, které chyby stále mohou být generovány v některých situacích přistupuje transparentně, i když se povolí Windows ARM hardwarem pro zpracování chybně zarovnaných celé číslo. Postupujte podle těchto pravidel pro zarovnání:

- Poloviční slova velké (16 bitů) a načte slova velké celé číslo (32bitová verze) a úložiště nemusí být zarovnaný. Hardware zpracovává je efektivní a transparentně.

- Zarovnání zatížení s plovoucí desetinnou čárkou a úložiště. Jádro nezarovnaných zatížení zpracovává a ukládá transparentně, ale s významné režijní náklady.

- Načtení nebo uložení double (LDRD/STRD) a zarovnání více operací (LDM/STM). Jádro zpracovává většina z nich transparentně, ale s významné režijní náklady.

- Všechny přístupy do paměti bez vyrovnávací paměti musí být zarovnány i pro přístup k celé číslo. Nezarovnané přístupy způsobit chybu zarovnání.

## <a name="instruction-set"></a>Sada instrukcí

Instrukce pro Windows na ARM je výhradně omezená na Thumb-2. Veškerý kód proveden na této platformě se očekává spuštění a zůstanou v režimu Thumb po celou dobu. Pokus přepnout do starší verze ARM instrukční sada může být úspěšné, ale pokud ano, všechny výjimky nebo přerušení, ke kterým dochází může vést chybě aplikace v uživatelském režimu nebo kontroly chyb v režimu jádra.

Vedlejším účinkem tento požadavek je, že všechny ukazatele kód musí mít s nízkou nastaven bit. Je to tak, aby při jsou načtena a rozvětvených prostřednictvím BLX nebo MX, procesor zůstanou v režimu Thumb a ne pokoušejí nepozorovaně spustit cílový kód jako 32bitový ARM pokyny.

### <a name="it-instructions"></a>Pokyny pro IT

Použití IT instrukcí v kód Thumb-2 je zakázáno, s výjimkou v takové situaci:

- Instrukce IT jde použít jenom k úpravě jeden cíl instrukcí.

- Instrukce cíl musí být instrukce 16 bitů.

- Instrukce cíl musí být jedna z následujících:

   |16bitové operační kódy|Třída|Omezení|
    |---------------------|-----------|------------------|
    |MOV MVN|Přesunutí|Správce prostředků! = počítače, VP! = PC|
    |OMEZENĚ DISTRIBUOVATELNÝCH OPRAV, OMEZENĚ DISTRIBUOVATELNÝCH OPRAV [S] B, H OMEZENĚ DISTRIBUOVATELNÝCH OPRAV [S]|Načtení z paměti|Ale ne literál formulářů omezeně distribuovatelných oprav|
    |STR STRB, STRH|Store do paměti.||
    |PŘIDAT, ADC, RSB, ZAŘÍZENÍMI, SUB|Můžete přidávat nebo odebírat|Ale ne ADD/SUB SP, SP, imm7 formulářů<br /><br /> Správce prostředků! = PC, relativní rozlišující! = PC, Rdm! = PC|
    |CMP CMN|Porovnat|Správce prostředků! = PC, Rn! = PC|
    |MUL|Násobení||
    |AZURE SITE RECOVERY, ZJEDNODUŠENÉHO NAČTENÍ ŘEŠENÍ, LSR, ZKOUŠENÉHO|Bitový posun||
    |A BIC EOR, ORR TST|Aritmetický bitový||
    |MX|Větev se má zaregistrovat|Správce prostředků! = PC|

I když aktuální ARMv7 procesorů nelze sestavy pomocí formulářů zakázaného instrukce budoucí generace se očekává. Pokud jsou zjištěny tyto formuláře, žádný program, který používá je může skončit s výjimkou nedefinované instrukce.

### <a name="sdivudiv-instructions"></a>SDIV/UDIV pokyny

Použití celé číslo rozdělit pokyny SDIV a UDIV je plně podporované. zahrnuje to i na platformách bez nativního hardwaru jejich zpracování. Režijní náklady za SDIV nebo UDIV dělení na mozkové A9 procesoru je přibližně 80 cykly, kromě celkový čas dělení 20 až 250 cyklů, v závislosti na vstupy.

## <a name="integer-registers"></a>Celočíselné registry

Procesor ARM podporuje 16 registrů pro celé číslo:

|Registr|Volatile?|Role|
|--------------|---------------|----------|
|r0|Volatile|Parametr, výsledek pomocné registrace 1|
|R1|Volatile|Parametr, výsledek pomocné registru 2|
|R2|Volatile|Parametr pomocné register 3|
|R3|Volatile|Parametr pomocné register 4|
|R4|Non-volatile||
|R5|Non-volatile||
|R6|Non-volatile||
|R7|Non-volatile||
|R8|Non-volatile||
|R9|Non-volatile||
|R10|Non-volatile||
|R11|Non-volatile|Ukazatel na rámec|
|r 12|Volatile|Volání procedury uvnitř pomocné registru|
|R13 (SP)|Non-volatile|Ukazatel zásobníku|
|R14 (LR)|Non-volatile|Registr odkaz|
|R15 (PC)|Non-volatile|Čítač programu|

Podrobnosti o tom, jak použít parametr a vrátí hodnotu registrů, najdete v části předávání parametru v tomto článku.

Windows používá r11 pro rychlé procházení zásobníku. Další informace najdete v části procházení zásobníku. Kvůli tomuto požadavku r11 musí odkazovat na nejvyšší článek v řetězci za všech okolností. Nepoužívejte r11 pro obecné účely – kódu nebude generovat správný procházení zásobníku během analýzy.

## <a name="vfp-registers"></a>Zaregistruje VFP

Windows podporuje jenom varianty ARM, které mají VFPv3 D32 koprocesoru podporují. To znamená, že registrů plovoucí desetinné čárky jsou vždy k dispozici a lze dovolávat pro předávání parametrů a kompletní sada 32 registrů je k dispozici pro použití. Zaregistruje VFP a jejich využití jsou shrnuté v této tabulce:

|Určené|Double – prvky|Quads|Volatile?|Role|
|-------------|-------------|-----------|---------------|----------|
|S0 s3|D0 d1|q0|Volatile|Pomocné parametry, výsledek, registr|
|S4 s7|d2 d3|1.|Volatile|Pomocné parametry registrace|
|s8 s.11|D4 d5|2. čtvrtletí|Volatile|Pomocné parametry registrace|
|s.15 S12 na úrovni Standard|D6 d7|3. čtvrtletí|Volatile|Pomocné parametry registrace|
|s 16 s19|D8 d9|4.|Non-volatile||
|S20 s23|D10 d11|5|Non-volatile||
|s24 s27|D12 d13|6|Non-volatile||
|s28 s31|D14 d15|Dotaz č. 7|Non-volatile||
||D16 d31|Dotaz 8-Otázka č. 15|Volatile||

Následující tabulka ukazuje stav s plovoucí desetinnou čárkou a bitová pole (FPSCR) se řídicí registr:

|Bity|Význam|Volatile?|Role|
|----------|-------------|---------------|----------|
|31-28|NZCV|Volatile|Příznaky stavu|
|27|QC|Volatile|Kumulativní sytost|
|26|AHP|Non-volatile|Alternativní ovládací prvek poloviční přesností|
|25|ROZLIŠUJÍCÍ NÁZEV|Non-volatile|Výchozí NaN režimu ovládací prvek|
|24|FZ|Non-volatile|Vyprázdnění nula režim ovládacího prvku|
|23-22|RMode|Non-volatile|Ovládací prvek režimu zaokrouhlení|
|21-20|STRIDE|Non-volatile|Vector – Stride, musí být vždy 0.|
|18-16|Délka|Non-volatile|Vector – délku, musí být vždy 0.|
|15, 12-8|Integrované vývojové prostředí, IXE, atd.|Non-volatile|Výjimku zachytit povolit bits, musí být vždy 0.|
|7, 4-0|Dokument společnosti IDC, IXC, atd.|Volatile|Příznaky kumulativní výjimky|

## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou čárkou

Většina ARM hardware nepodporuje výjimky s plovoucí desetinnou čárkou IEEE. Na procesoru varianty, které mají hardwarové výjimky s plovoucí desetinnou čárkou jádra Windows tiše zachytí výjimky a implicitně zakazuje je do registru FPSCR. Tím se zajistí normalizované chování napříč varianty procesoru. Kód vyvinutý na platformě, která nemá podporu výjimky v opačném případě mohli dostávat neočekávané výjimky, při spuštění na platformě, která se má výjimka podporují.

## <a name="parameter-passing"></a>Předávání parametrů

Pro jiné variadické funkce Windows na ARM ABI následuje ARM pravidla pro předávání parametrů – to zahrnuje rozšíření VFP a Advanced SIMD. Postupujte podle těchto pravidel [postup volání Standard pro architekturu ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf)sloučeného pomocí rozšíření VFP. Ve výchozí, první čtyři celočíselné argumenty a až osm s plovoucí desetinnou čárkou nebo vektorové argumenty jsou předány v registrech a další argumenty jsou předány v zásobníku. Argumenty jsou přiřazeny k registry nebo zásobníku pomocí tohoto postupu:

### <a name="stage-a-initialization"></a>Fáze inicializace A:

Inicializace probíhá pouze jednou, před zahájením zpracování argumentů:

1. Na další základní registrace číslo (NCRN) je nastavena na r0.

2. VFP registry jsou označeny jako volné.

3. Na další skládaný Argument adresu (NSAA) je nastavena na aktuální SP.

4. Pokud je volána funkce, která vrátí výsledek v paměti, adresu pro výsledek se umístí do r0 a je nastavena NCRN R1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Fáze B: předběžné odsazení a rozšíření argumentů

Pro každý argument v seznamu je použito první vyhovující pravidlo z následujícího seznamu:

1. Pokud argument je složený typ, jehož velikost nelze určit staticky tak, že volající a volaného, tento argument je zkopírována do paměti a nahrazuje ukazatel na kopii.

2. Pokud je argumentem bajtů nebo částečně slova 16 bitů, je nulou nebo rozšířena znaménkem na 32bitové úplné slovo a považován za argument na 4 bajty.

3. Pokud argument je složený typ, jeho velikost se zaokrouhluje na nejbližší násobek čísla 4.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Fáze C: přiřazení argumentů, které mají registry a zásobníku

Pro každý argument v seznamu následující pravidla se použijí pak dokud byl přidělen argument:

1. Pokud je argument typu VFP a dostatek po sobě jdoucích nepřidělené registrů VFP příslušného typu, argument je přidělen nejnižší číslované pořadí těchto registrů.

2. Pokud je argumentem Typ VFP, všechny zbývající volné registry jsou označeny jako nedostupné. NSAA se upraví nahoru, dokud je správně zarovnán pro typ argumentu a argument je zkopírován do zásobníku volání na upravené NSAA. NSAA je poté zvýšen o velikost argumentu.

3. Pokud argument vyžaduje 8bajtový zarovnání, NCRN se zaokrouhluje nahoru na nejbližší číslo sudé registru.

4. Pokud není více než r4 minus NCRN velikost argumentu ve slovech 32-bit, argument zkopírována do registrů core, počínaje NCRN, s nejméně významných bitů zabírá registrů nižší sudým číslem. NCRN se zvýší počet registrů použít.

5. Pokud NCRN je menší než r4 a NSAA rovná SP, argument je rozdělená mezi základní registry a zásobníku. První část argumentu je zkopírována do registrů core, počínaje NCRN, až a včetně r3. Zbývající část argumentu je zkopírován do zásobníku, počínaje NSAA. NCRN je nastavena na r4 a NSAA je zvýšen o velikost argumentu minus částka předány v registrech.

6. Pokud argument vyžaduje 8bajtový zarovnání, NSAA se zaokrouhluje další zarovnané adrese 8 bajtů.

7. Argument je zkopírována do paměti NSAA. NSAA je zvýšen o velikost argumentu.

VFP registrech nejsou použity pro variadické funkce a pravidel C fáze 1 a 2 jsou ignorovány. To znamená, že variadické funkce může začínat volitelné nabízených {r0 – r3} pro předřazení argumentů registru do jakýchkoli dalších argumentů předaná volající funkcí a přejděte k seznamu argumentů celý přímo ze zásobníku.

Hodnoty typu Integer se vrátí v r0, případně rozšířit na r1 pro vrácené hodnoty 64-bit. VFP/NEON s plovoucí desetinnou čárkou nebo SIMD typu hodnoty jsou vráceny v s0, d0 nebo q0 podle potřeby.

## <a name="stack"></a>Rámec

Zásobník musí zůstat 4bajtové zarovnána po celou dobu a musí být 8 bajtů zarovnána na hranici žádné funkce. To je potřeba k podpoře časté použití propojené operace pro proměnné zásobníku 64-bit. ARM EABI hlásí, že zásobník je 8 bajtů zarovnána na libovolné veřejné rozhraní. Pro zajištění konzistence Windows na ARM ABI bere v úvahu všechny funkce předěl, který má být veřejné rozhraní.

Funkce, které mají používat ukazatel na rámec – například toto volání funkce `alloca` nebo který ukazatel zásobníku změnit dynamicky – musíte nastavit ukazatel na rámec v r11 v prologu funkce a nechte beze změny až epilogu. Funkce, které nevyžadují ukazatel na rámec musí v prologu provede všechny aktualizace zásobníku a ukazatel zásobníku, dokud epilogu beze změny.

Funkce, které přidělují 4 KB nebo Další informace o zásobníku musíte zajistit, že je v pořadí dotčená každou stránku před poslední stránky. Tím se zajistí, že žádný kód můžete "leap přes" ochranné stránky, které Windows používá rozšíření zásobníku. Obvykle to se provádí `__chkstk` pomocné rutiny, které se předává celkové přidělení zásobníku v bajtech dělený 4 v r4 a která vrací poslední zásobníku přidělení velikost v bajtech zpět v r4.

### <a name="red-zone"></a>Červené zóny

8bajtový oblast bezprostředně pod aktuální ukazatel zásobníku je vyhrazený pro analýzu a dynamické opravy. To umožňuje pečlivě generovaného kódu má být vložen, který uchovává 2 registrů na [sp, #-8] a používá je dočasně libovolného důvodů. Jádra Windows zaručuje, že tyto 8 bajtů nedojde k přepsání dojde-li k výjimce nebo přerušení v uživatelském režimu i režimu jádra.

### <a name="kernel-stack"></a>Jádra zásobníku

Výchozím režimu jádra zásobníku ve Windows je tři stránky (12 KB). Dejte pozor, abyste vytvořit funkce, které mají velké zásobníku vyrovnávací paměti v režimu jádra. Přerušení může pocházet pomocí velmi málo rezervou zásobníku a způsobit, že zásobník tísňový kontroly chyb.

## <a name="cc-specifics"></a>Specifikace jazyka C/C++

Výčty jsou typy 32bitové celé číslo, pokud alespoň jednu hodnotu ve výčtu vyžaduje 64-bit double word úložiště. V takovém případě výčtu je povýšen na typ 64bitové celé číslo.

`wchar_t` je definován jako ekvivalentní `unsigned short`, chcete-li zachovat kompatibilitu s jinými platformami.

## <a name="stack-walking"></a>Procházení zásobníku

Windows kód je zkompilován pomocí ukazatele na rámce povolené ([/Oy (vynechání ukazatele na rámec)](../build/reference/oy-frame-pointer-omission.md)) k povolení procházení zásobníku rychlé. Obecně platí, r11 zaregistrovat odkazuje na odkaz na další v řetězci, který je {r11, lr} pár, který určuje ukazatel na předchozí snímek zásobníku a zpáteční adresu. Doporučujeme, aby váš kód také povolit ukazatele na rámce lepší profilace a trasování.

## <a name="exception-unwinding"></a>Uvolňování výjimek

Během zpracování výjimek uvolnění zásobníku je povoleno pomocí kódy unwind. Kódy unwind je posloupnost bajtů, které jsou uložené v části .xdata spustitelné bitové kopie. Popisují operace kód prologu a epilogu funkce abstraktní způsobem tak, aby efekty prologu funkce může být v rámci přípravy odvíjení rámce zásobníku volajícího vrátit zpět.

ARM EABI určuje odvíjení model výjimek, který používá parsovat kódy unwind. Tato specifikace však není dostatečná pro uvolnění ve Windows, které musí zpracovat případy, ve kterém procesoru je uprostřed prologu nebo epilogu funkce. Další informace o Windows na ARM data výjimky a uvolnění, naleznete v tématu [zpracování výjimek ARM](../build/arm-exception-handling.md).

Doporučujeme, aby dynamicky generovaném kódu najdete pomocí dynamické funkce tabulky zadané ve volání do `RtlAddFunctionTable` a související funkce, tak, aby vygenerovaného kódu mohl podílet na zpracování výjimek.

## <a name="cycle-counter"></a>Čítač cyklu

Procesory ARM se systémem Windows jsou potřebné k podpoře cyklu čítač, ale pomocí čítače přímo může způsobit problémy. K těmto potížím vyhnout, Windows na ARM používá nedefinovaný operační kód k vyžádání normalizovanou hodnotu čítače cyklu 64-bit. V jazyce C nebo C++, použijte `__rdpmccntr64` přirozené pro generování odpovídající operační kód; ze sestavení, použijte `__rdpmccntr64` instrukce. Čtení čítačů cyklu trvá přibližně 60 cykly na mozkové a A9.

Čítač je čítač true cyklu, nikoli hodin; proto počítání frekvence se liší podle frekvence procesoru. Pokud chcete k měření uplynulý čas, použijte `QueryPerformanceCounter`.

## <a name="see-also"></a>Viz také:

[Běžné problémy s migrací ARM v prostředí Visual C++](../build/common-visual-cpp-arm-migration-issues.md)  
[Zpracování výjimek ARM](../build/arm-exception-handling.md)  
