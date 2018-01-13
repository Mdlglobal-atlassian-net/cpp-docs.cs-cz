---
title: "Přehled konvencí ABI ARM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 073fe113c1915913d06a63c7feabcb7808896188
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-arm-abi-conventions"></a>Přehled konvencí ABI ARM
Binární rozhraní aplikace (ABI) pro kód zkompilovaném pro Windows na procesory ARM je založena na standardní EABI ARM. Tento článek popisuje klíčové rozdíly mezi Windows on ARM a standard. Další informace o standardní EABI ARM naleznete v tématu [aplikace binární rozhraní (ABI) pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html).  
  
## <a name="base-requirements"></a>Základní požadavky  
 Windows na ARM předpokládá, že je spuštěn na architekturu ARMv7 za všech okolností. Podpora plovoucí desetinné čárky ve tvaru VFPv3 D32 nebo novější musí být součástí hardwaru. VFP musí podporovat jednoduchou přesností a s plovoucí desetinnou čárkou v hardwaru s dvojitou přesností. Prostředí Windows runtime nepodporuje emulaci s plovoucí desetinnou čárkou povolit systémem bez VFP hardwaru.  
  
 Podpora SIMD Extensions (NEÓNOVÁ) rozšířené – to zahrnuje celé číslo a operace s plovoucí desetinnou čárkou – musí být k dispozici také v hardwaru. Žádná spuštění podpora pro emulaci je k dispozici.  
  
 Podpora dělení celé číslo (UDIV/SDIV) je důrazně doporučujeme, ale není potřeba. Platformy, které neobsahují podporu celočíselné dělení mohou být účtovány snížení výkonu, protože tyto operace musí být do pasti a případně opravit.  
  
## <a name="endianness"></a>Endianitou  
 Windows na ARM se spustí v režimu little endian. Kompilátor Visual C++ a prostředí Windows runtime očekávat little endian data za všech okolností. I když SETEND instrukce v ARM pokyn nastavit architektura (ISA) umožňuje kódu to i v uživatelském režimu, chcete-li změnit aktuální endianitou, to tak se nedoporučuje. protože je nebezpečné pro aplikaci. Pokud je výjimku generována v režimu big endian chování předpovědět a může vést selhání aplikace v uživatelském režimu, nebo kontrola chyb v režimu jádra.  
  
## <a name="alignment"></a>Zarovnání  
 Způsob zarovnání chyb objevovat i nadále, může v některých situacích přistupuje transparentně, i když Windows umožňuje ARM hardwarem pro zpracování chybně zarovnaných celé číslo. Postupujte podle těchto pravidel pro zarovnání:  
  
-   Velikost word půl (16 bitů) a načte word velikost celé číslo (32 bitů) a úložiště nemusí být zarovnána. Hardware zpracovává je efektivní a transparentně.  
  
-   By mělo být zarovnáno s plovoucí desetinnou čárkou zatížení a úložiště. Jádra zpracovává nezarovnané zatížení a ukládá transparentně, ale s významné režii.  
  
-   Zatížení nebo úložiště double (LDRD/STRD) a zarovnání více operací (LDM/STM). Jádra zpracovává většina z nich transparentně, ale s významné režii.  
  
-   Všechny přístupy bez vyrovnávací paměti paměti musí být zarovnána i pro přístup k celé číslo. Nezarovnané přístupů způsobit chybu zarovnání.  
  
## <a name="instruction-set"></a>Sada instrukcí  
 Instrukce nastavit pro Windows on ARM je výhradně omezená na 2 jezdce. Všechny kód provést na této platformě se očekává spuštění a zůstanou v režimu jezdec za všech okolností. Pokus přepnout do starší verze sada instrukcí ARM může být úspěšné, ale pokud ano, všechny výjimky nebo přerušení, ke kterým dochází může vést selhání aplikace v uživatelském režimu, nebo kontrola chyb v režimu jádra.  
  
 Vedlejším účinkem tento požadavek je, že všechny ukazatele kód musí mít nízkou bit nastavit. Toto je tak, aby při jejich načíst a vytvořit větve do prostřednictvím BLX nebo BX, procesor zůstanou v režimu Flash a není pokusí spustit cílový kód jako 32bitový ARM pokyny.  
  
### <a name="it-instructions"></a>IT pokyny  
 Použití IT pokyny v kódu jezdec-2 je zakázaná, s výjimkou těchto konkrétních případech:  
  
-   Instrukce IT slouží pouze k úpravě jeden cíl instrukcí.  
  
-   Cíl instrukcí musí být instrukce 16 bitů.  
  
-   Cíl instrukcí musí mít jednu z těchto:  
  
    |Operační 16bitové kódy|Třída|Omezení|  
    |---------------------|-----------|------------------|  
    |MOV, MVN|Přesunutí|RM! = počítače, VP! = počítače|  
    |LDR, LDR [S] B, H LDR [S]|Načtení z paměti|Ale není LDR literálu formulářů|  
    |STR STRB, STRH|Ukládání do paměti||  
    |PŘIDAT, ADC, RSB, SBC, SUB|Přidat nebo odebrat|Ale není přidat nebo dílčí SP, SP, imm7 formulářů<br /><br /> RM! = počítače, relativního rozlišujícího! = počítače, Rdm! = počítače|  
    |CMP, CMN|Porovnání|RM! = počítače, nout! = počítače|  
    |MUL|Násobení||  
    |AUTOMATICKÉ OBNOVENÍ SYSTÉMU, DOLNÍ LIMIT, LSR, ROR|Bitové posunutí||  
    |A BIC, EOR, ORR TST|Aritmetický bitový||  
    |BX|Větev k registraci|RM! = počítače|  
  
 I když aktuální ARMv7 procesorů nelze sestavu použití nepovoleném instrukce forms budoucí generace se očekává. Pokud jsou tyto formuláře, může být žádné program, který používá je ukončeno s výjimkou nedefinované instrukcí.  
  
### <a name="sdivudiv-instructions"></a>SDIV/UDIV pokyny  
 Použití celé číslo rozdělují pokyny SDIV a UDIV plnou podporu, i na platformách bez nativní hardware tak, aby mohli je zpracovat. Režijní náklady na SDIV nebo UDIV dělení mozkové A9 procesoru je přibližně 80 cykly, kromě celkovou dobu dělení cyklů 20 250, v závislosti na vstupy.  
  
## <a name="integer-registers"></a>Zaregistruje celé číslo  
 Procesor ARM podporuje 16 registrů celé číslo:  
  
|Registr|Volatile?|Role|  
|--------------|---------------|----------|  
|r0|Volatile|Parametr, výsledek pomocné registrace 1|  
|R1|Volatile|Parametr, výsledek pomocné registrace 2|  
|R2|Volatile|Parametr pomocné registrace 3|  
|R3|Volatile|Parametr pomocné registrace 4|  
|R4|Non-volatile||  
|R5|Non-volatile||  
|R6|Non-volatile||  
|R7|Non-volatile||  
|R8|Non-volatile||  
|R9|Non-volatile||  
|R10|Non-volatile||  
|R11|Non-volatile|Ukazatel na rámec|  
|r 12|Volatile|Volání procedur Intra pomocné registrace|  
|R13 (SP)|Non-volatile|Ukazatel zásobníku|  
|R14 (LR)|Non-volatile|Odkaz registrace|  
|R15 (počítače)|Non-volatile|Čítač programu|  
  
 Podrobnosti o tom, jak pomocí parametru a vrátit hodnotu registrů, najdete v části předání parametru v tomto článku.  
  
 Windows používá r11 fast proti rámce zásobníku. Další informace najdete v části procházení zásobníku. Kvůli tomuto požadavku musí r11 odkazovat na nejhornější odkaz v řetězu za všech okolností. Nepoužívejte r11 pro obecné účely – kódu nevygeneruje správné procházení zásobníku během analýzy.  
  
## <a name="vfp-registers"></a>Zaregistruje VFP  
 Windows podporuje jenom variant ARM, které mají VFPv3 D32 koprocesor podporovat. To znamená, že zaregistruje se s plovoucí desetinnou čárkou jsou vždy k dispozici a jsou spolehlivé pro předávání parametrů, a že kompletní sada 32 registry je k dispozici pro použití. Zaregistruje VFP a jejich využití jsou shrnuté v této tabulce:  
  
|Singly|Double – prvky|Quads|Volatile?|Role|  
|-------------|-------------|-----------|---------------|----------|  
|S0 s3|D0 d1|q0|Volatile|Pomocné parametry, výsledek, registrace|  
|S4 s7|d2 d3|OTÁZKA Č. 1|Volatile|Parametry, pomocné registrace|  
|s8 s.11|D4 d5|DOTAZ Č. 2|Volatile|Parametry, pomocné registrace|  
|S12 s.15|D6 d7|3. ČTVRTLETÍ|Volatile|Parametry, pomocné registrace|  
|s19 s 16|D8 d9|OTÁZKA Č. 4|Non-volatile||  
|S20 s23|D10 d11|Dotaz č. 5|Non-volatile||  
|s24 s27|D12 d13|6|Non-volatile||  
|s28 s31|D14 d15|Dotaz č. 7|Non-volatile||  
||D16 d31|Otázka č. 8-Otázka č. 15|Volatile||  
  
 V další tabulce ukazuje stav s plovoucí desetinnou čárkou a řízení zaregistrovat bitová pole (FPSCR):  
  
|Bity|Význam|Volatile?|Role|  
|----------|-------------|---------------|----------|  
|31-28|NZCV|Volatile|Příznaky stavu|  
|27|QC|Volatile|Kumulativní sytost|  
|26|AHP|Non-volatile|Alternativní půl přesnost ovládací prvek|  
|25|ROZLIŠUJÍCÍ NÁZEV|Non-volatile|Výchozí NaN režimu ovládací prvek|  
|24|FZ|Non-volatile|Vyprázdnění nula režimu ovládací prvek|  
|23-22|RMode|Non-volatile|Zaokrouhlení režimu ovládací prvek|  
|21-20|STRIDE|Non-volatile|Vector Stride, musí být vždy 0.|  
|18-16|Len|Non-volatile|Vector délka, musí být vždy 0.|  
|15, 12-8|IDE, IXE, atd.|Non-volatile|Výjimka depeše povolit bits, musí být vždy 0.|  
|7, 4-0|IDC, IXC, atd.|Volatile|Příznaky kumulativní výjimky|  
  
## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou čárkou  
 Většina ARM hardware nepodporuje výjimek plovoucí desetinné čárky IEEE. Jádro systému Windows na variant procesoru, které mají s plovoucí desetinnou čárkou výjimky hardwaru, bezobslužně zachytí výjimky a je implicitně zakáže v registru FPSCR. Tím se zajistí normalizovaný chování napříč variant procesoru. Jinak hodnota kódu vyvinuté na platformě, která nemá výjimky, které podporují neočekávané výjimky při obdržet je spuštěn na platformu, která se má výjimka podporovat.  
  
## <a name="parameter-passing"></a>Předávání parametrů  
 Pro jiné variadická funkce Windows on ARM ABI následuje ARM pravidla pro předávání parametrů – to zahrnuje rozšíření VFP a rozšířené SIMD. Postupujte podle těchto pravidel [postup volání standardní pro architekturu ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), konsolidované s rozšíření VFP. Pomocí výchozí první čtyři celočíselné argumenty a až osm s plovoucí desetinnou čárkou nebo vector argumenty jsou předány v registrech a další argumenty se předávají v zásobníku. Argumenty jsou přiřazeni k registry nebo zásobníku tímto postupem:  
  
### <a name="stage-ainitialization"></a>Příprava A – inicializace  
 Inicializace se provádí právě jednou před zahájením zpracování argument:  
  
1.  Na další základní zaregistrovat číslo (NCRN) je nastavena na r0.  
  
2.  Zaregistruje VFP jsou označeny jako volné.  
  
3.  Na další skládaný Argument adresu (NSAA) je nastavena na aktuální SP.  
  
4.  Pokud je volána funkce, která vrací výsledek v paměti, adresu pro výsledek je umístěn v r0 a NCRN je nastaven na r1.  
  
### <a name="stage-bpre-padding-and-extension-of-arguments"></a>Fáze B – Pre odsazení a rozšíření argumentů  
 Pro každý argument v seznamu se použije první odpovídající pravidlo z následujícího seznamu:  
  
1.  Pokud je argumentem složeného typu, jejíž aktuální velikost nelze určit staticky volající i volaného, argument se zkopíruje do paměti a nahrazuje ukazatel na kopie.  
  
2.  Pokud je argumentem bajtů nebo 16bitové půl word, je rozšířené nula nebo rozšířeny do 32-bit úplné word a považován za 4bajtový argument.  
  
3.  Pokud je argumentem složeného typu, je jeho velikost zaokrouhlený nahoru na nejbližší násobek 4.  
  
### <a name="stage-cassignment-of-arguments-to-registers-and-stack"></a>Fáze C – přiřazení argumentů registry a zásobníku  
 Pro každý argument v seznamu následující pravidla platí zase dokud přiděleno argument:  
  
1.  Pokud argument je typu VFP a nejsou k dispozici dostatečný počet po sobě jdoucích nepřidělené registry VFP příslušného typu, je přidělen argument pořadí nejnižší číslované takové registrů.  
  
2.  Pokud argument je typu VFP, všechny ostatní nepřidělené registry jsou označeny jako nedostupné. NSAA se upraví směrem nahoru, dokud je správně zarovnán pro typ argumentu a argument se zkopíruje do zásobníku v upravenou NSAA. NSAA se pak zvýší velikost argumentu.  
  
3.  Pokud argument vyžaduje 8bajtový zarovnání, je NCRN zaokrouhlený nahoru na nejbližší číslo i registrace.  
  
4.  Pokud velikost argument ve 32bitové slova není víc než r4 minus NCRN, argument zkopírována do základní registrů, počínaje NCRN, s nejméně významný bity v registry číslované nižší. NCRN se zvýší podle počtu zaregistruje se používá.  
  
5.  Pokud NCRN je menší než r4 a NSAA rovná SP, argument je rozdělená mezi základní registry a zásobníku. První část argument zkopírována do registry jádra, až od NCRN a včetně r3. Zbývající část argument zkopírován do zásobníku, začínající NSAA. NCRN nastavena na r4 a NSAA se zvýší velikost argument minus částka předány v registrech.  
  
6.  Pokud argument vyžaduje 8bajtový zarovnání, NSAA zaokrouhlit na adresu zarovnaný další 8 bajtů.  
  
7.  Argument se zkopíruje na NSAA v paměti. NSAA se zvýší velikost argumentu.  
  
 Zaregistruje VFP nepoužívají se pro funkce variadická a pravidla C fáze 1 a 2 jsou ignorovány. To znamená, že funkce variadická může začínat volitelné nabízené {r0-r3} pro předřazení registrace argumenty, které mají libovolné další argumenty předaná volající funkcí a poté přístup k seznamu celý argument přímo z zásobníku.  
  
 Hodnoty typu integer, jsou vráceny v r0, případně rozšířit na r1 pro 64bitové vrácené hodnoty. VFP nebo NEÓNOVÁ s plovoucí desetinnou čárkou nebo SIMD typ hodnoty jsou vráceny v s0, d0 nebo q0 podle potřeby.  
  
## <a name="stack"></a>Rámec  
 V zásobníku musí zůstat 4bajtový zarovnán za všech okolností a musí být 8bajtový zarovnán na všechny funkce hranic. To je potřeba pro podporu často používají interlocked operací na 64-bit zásobníku proměnné. ARM EABI uvádí, že v zásobníku je 8bajtový zarovnán v libovolné veřejné rozhraní. Konzistence Windows on ARM ABI zvažuje všechny funkce předěl, který má být veřejné rozhraní.  
  
 Funkce, které mají používat ukazatel na rámec – například funkce tohoto volání `alloca` nebo který má ukazatel zásobníku se dynamicky mění – musí nastavit ukazatel rámce v r11 v prologu funkce a nechte ho beze změny až epilogu. Funkce, které nevyžadují ukazatel na rámec musíte provádět všechny aktualizace zásobníku v prologu a nechte beze změny, dokud epilogu ukazatel zásobníku.  
  
 Funkce, které přidělují 4 KB nebo více v zásobníku musíte zajistit, že je v pořadí dotýkal každé stránce před poslední stránce. Tím se zajistí, že žádný kód můžete "leap přes" ochrana stránek, které Windows používá rozšíření zásobníku. Obvykle k tomu je potřeba `__chkstk` pomocné rutiny, který je v bajtech dělený 4 v r4 předat přidělení celkový zásobníku a které vrátí velikost přidělení zásobníku konečné v bajtech zpět v r4.  
  
### <a name="red-zone"></a>Red zóny  
 Oblasti 8bajtový bezprostředně pod aktuální ukazatel zásobníku je vyhrazena pro analýzu a dynamické opravy. To umožňuje má být vložen, pečlivě generovaného kódu, která ukládá 2 registruje v [sp,-8.] a použije je dočasně pro libovolný účely. Jádro systému Windows zaručuje, že tyto 8 bajtů nedojde k přepsání případě výjimku nebo přerušení v uživatelském režimu i režimu jádra.  
  
### <a name="kernel-stack"></a>Zásobník jádra  
 Výchozím režimu jádra zásobníku v systému Windows je tři stránky (12 KB). Dejte pozor, abyste vytvořit funkce, které mají velký zásobníku vyrovnávací paměti v režimu jádra. Přerušení může pocházet pomocí velmi malé rezervou zásobníku a způsobit zásobníku tísňový kontroly chyb.  
  
## <a name="cc-specifics"></a>Specifika C/C++  
 Výčty jsou typy 32bitové celé číslo, pokud alespoň jednu hodnotu ve výčtu vyžaduje 64-bit dvojitou word úložiště. V takovém případě výčtu je propagována do typu 64bitové celé číslo.  
  
 `wchar_t`je definován jako ekvivalentní `unsigned short`, zachování kompatibility s jinými platformami.  
  
## <a name="stack-walking"></a>Procházení zásobníku  
 Kompilace kódu Windows s rámečkem ukazatele povolené ([/Oy (vynechání ukazatele)](../build/reference/oy-frame-pointer-omission.md)) Chcete-li povolit procházení rychlé zásobníku. Obecně platí, r11 zaregistrovat v řetězci, který je {r11, lr} odkazuje na odkaz na další pár, který určuje má ukazatel na předchozí snímek v zásobníku a zpáteční adresu. Doporučujeme kódu také povolit ukazatele na rámce pro vylepšené profilace a trasování.  
  
## <a name="exception-unwinding"></a>Výjimka Unwinding  
 Při zpracovávání výjimek v jazyce unwinding zásobníku je povolit pomocí služby unwind kódy. Unwind kódy jsou sekvenci bajtů, které jsou uložené v části .xdata spustitelné bitové kopie. Popisují operaci kódu prologu a epilogu funkce abstraktní způsobem, aby důsledky prologu funkce může být v rámci přípravy na rámec zásobníku volajícího unwinding vrátit zpět.  
  
 ARM EABI určuje unwinding modelu výjimky, který používá unwind kódy. Tato specifikace však není dostatečná pro unwinding v systému Windows, který musí zpracovávat případech, kdy procesor uprostřed prologu nebo epilogu funkce. Další informace o systému Windows na ARM data výjimky a unwinding najdete v tématu [zpracování výjimek ARM](../build/arm-exception-handling.md).  
  
 Doporučujeme, aby dynamicky generovaném kódu popsat pomocí dynamické funkce tabulky zadané ve volání `RtlAddFunctionTable` a související funkce, tak, aby generovaný kód mohl účastnit výjimek.  
  
## <a name="cycle-counter"></a>Čítač cyklu  
 Procesory ARM systémem Windows jsou potřebné k podpoře čítač cyklus, ale přímo pomocí čítače může způsobit problémy. Abyste se těmto problémům, používá Windows on ARM nedefinované opcode k vyžádání normalizovanou hodnotu čítače cyklu 64-bit. Z jazyka C nebo C++, použijte `__rdpmccntr64` vnitřní k emitování odpovídající opcode; ze sestavení, použijte `__rdpmccntr64` instrukcí. Čtení čítač cyklu trvá přibližně 60 cykly na mozkové-A9.  
  
 Čítač je čítač true cyklus, není hodiny; proto počítání frekvence se liší podle frekvence procesoru. Pokud chcete k měření času uplynulá hodin, použijte `QueryPerformanceCounter`.  
  
## <a name="see-also"></a>Viz také  
 [Běžné problémy s migrací ARM Visual C++](../build/common-visual-cpp-arm-migration-issues.md)   
 [Zpracování výjimek ARM](../build/arm-exception-handling.md)