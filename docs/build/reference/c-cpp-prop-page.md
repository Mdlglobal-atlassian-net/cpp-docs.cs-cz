---
title: Vlastnosti CC++ /Project (Visual Studio)
description: Referenční příručka k vlastnostem stránky vlastností Microsoft CC++ /Project sady Visual Studio.
ms.date: 02/09/2020
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: fdfcaaebe8394fedd160c6c02e8c938543f845e2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257751"
---
# <a name="cc-property-pages"></a>Stránky vlastnostíC++ C/a

Následující stránky vlastností se nacházejí v nabídce > **vlastnosti** **projektu** > **Vlastnosti konfigurace** > **C/C++** :

## <a name="cc-general-properties"></a>Vlastnosti CC++ /obecné

### <a name="additional-include-directories"></a>Další adresáře k zahrnutí

Určuje jeden nebo více adresářů, které mají být přidány do cesty include; oddělte je středníkem, pokud je více než jedna. Nastaví [/i (další adresáře k zahrnutí)](i-additional-include-directories.md).

### <a name="additional-using-directories"></a>Další #using adresářů

Určuje jeden nebo více adresářů (oddělené názvy adresářů a středníkem), které budou prohledány k překladu názvů předaných do direktivy #using. Nastaví [/AI](ai-specify-metadata-directories.md).

### <a name="debug-information-format"></a>Formát ladicích informací

Určuje typ ladicích informací generovaných kompilátorem.  Tato vlastnost vyžaduje kompatibilní nastavení linkeru. Nastaví [/Z7,/Zi,/Zi (formát ladicích informací)](z7-zi-zi-debug-information-format.md).

#### <a name="choices"></a>Vlastnit

- **None** – nevytváří žádné ladicí informace, takže kompilace může být rychlejší.
- **Kompatibilní s C7** – vyberte typ informací o ladění vytvořených pro program a zda jsou tyto informace uloženy v souborech objektů (. obj) nebo v databázi programu (PDB).
- **Databáze programu** – vytvoří databázi programu (PDB) obsahující informace o typech a symbolickém ladění pro použití s ladicím programem. Symbolické ladicí informace obsahují názvy a typy proměnných a funkcí a čísla řádků.
- **Databáze programu pro funkci upravit a pokračovat** – vytvoří databázi programu, jak je popsáno výše, ve formátu, který podporuje funkci [Upravit a pokračovat](/visualstudio/debugger/edit-and-continue) .

### <a name="support-just-my-code-debugging"></a>Podpora ladění Pouze můj kód

Přidá podpůrný kód pro povolení ladění [pouze můj kód](/visualstudio/debugger/just-my-code) v této kompilační jednotce. Nastaví [/JMC](jmc.md).

### <a name="common-language-runtime-support"></a>Podpora modulu CLR (Common Language RunTime)

Použijte službu .NET Runtime.  Tento přepínač není kompatibilní s některými jinými přepínači. Podrobnosti najdete v dokumentaci k přepínačům [/CLR](clr-common-language-runtime-compilation.md) .

#### <a name="choices"></a>Vlastnit

- **Bez podpory modulu** CLR – žádná podpora modulu CLR (Common Language Runtime)
- **Podpora modulu CLR (Common Language RunTime)** – vytvoří metadata pro vaši aplikaci, která mohou být spotřebována jinými aplikacemi CLR. Umožňuje aplikaci také využívat typy a data v metadatech jiných komponent CLR.
- **Podpora modulu CLR (Common Language RunTime) čistě MSIL** – vytvoří výstupní soubor pouze [MSIL](/dotnet/standard/managed-code)bez nativního spustitelného kódu, ačkoli může obsahovat nativní typy zkompilované do jazyka MSIL.
- **Bezpečná podpora jazyka MSIL modulu** CLR – vytvoří pouze jazyk MSIL (bez nativního spustitelného kódu) a ověřitelný výstupní soubor.

### <a name="consume-windows-runtime-extension"></a>Využívat rozšíření prostředí Windows Runtime

Využijte rozšíření programovacích jazyků Windows Runtime. Nastaví [/ZW](zw-windows-runtime-compilation.md).

### <a name="suppress-startup-banner"></a>Potlačit úvodní nápis

Potlačí zobrazení nápisu přihlášení při spuštění kompilátoru a zobrazení informačních zpráv během kompilace.

### <a name="warning-level"></a>Úroveň upozornění

Vyberte, jak striktní má kompilátor obsahovat chyby kódu. Nastaví [/W0-/W4](compiler-option-warning-level.md).

#### <a name="choices"></a>Vlastnit

- Vypnout **všechna upozornění** – 0 úrovně 0 zakáže všechna upozornění.
- **Level1** -Level 1 zobrazuje závažná upozornění. Úroveň 1 je výchozí úroveň pro upozornění na příkazovém řádku.
- **Level2** -Level 2 zobrazuje všechna upozornění úrovně 1 a upozornění méně závažná než úroveň 1.
- **Level3** -Level 3 zobrazuje všechna upozornění úrovně 2 a všechna ostatní upozornění doporučená pro produkční účely.
- **Level4** 4 zobrazuje všechna upozornění úrovně 3 a informační upozornění, která lze ve většině případů bezpečně ignorovat.
- **Povolit všechna upozornění** – povolí všechna upozornění, včetně těch, které jsou ve výchozím nastavení zakázané.

### <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby

Zpracovává upozornění kompilátoru jako chyby. Pro nový projekt může být nejvhodnější použít [/WX](wx-treat-linker-warnings-as-errors.md) při každé kompilaci. Vyřešte všechna upozornění, abyste minimalizovali nedostatky v obtížném hledání kódu.

### <a name="warning-version"></a>Verze upozornění

Skrýt upozornění zavedená po určité verzi kompilátoru. Nastaví [/WV: xx\[. yy\[. zzzzz\]\]](wx-treat-linker-warnings-as-errors.md).

### <a name="diagnostics-format"></a>Formát diagnostiky

Povolí bohatou diagnostiku s informacemi o sloupci a zdrojovém kontextu v diagnostických zprávách.

#### <a name="choices"></a>Vlastnit

- **Blikající kurzor** – poskytuje informace o sloupci v diagnostické zprávě. A vypíše relevantní řádek zdrojového kódu se blikajícím kurzorem, který označuje problematický sloupec.
- **Informace o sloupci** – dále uvádí číslo sloupce v řádku, kde se Diagnostika vydá, pokud je to možné.
- **Classic** – vypíše jenom předchozí stručné diagnostické zprávy s číslem řádku.

### <a name="sdl-checks"></a>Kontroly SDL

Další doporučené kontroly SDL (Security Development Lifecycle); zahrnuje povolení dalších funkcí pro generování zabezpečeného kódu a umožňuje další upozornění týkající se zabezpečení jako chyb. Nastaví [/SDL,/SDL-](sdl-enable-additional-security-checks.md).

### <a name="multi-processor-compilation"></a>Kompilace s využitím více procesorů

Kompilace s více procesory.

## <a name="cc-optimization-properties"></a>Vlastnosti jazykaC++ C/optimalizace

### <a name="optimization"></a>Optimalizace

Vyberte možnost pro optimalizaci kódu; Pokud chcete použít konkrétní možnosti optimalizace, klikněte na vlastní. Nastaví [/od](od-disable-debug.md), [/O1,/O2](o-options-optimize-code.md).

#### <a name="choices"></a>Vlastnit

- **Vlastní** optimalizace.
- **Zakázáno** – zakázat optimalizaci.
- **Maximální optimalizace (upřednostnění velikosti)** – ekvivalent/og/OS/Oy/Ob2/GS/GF/Gy
- **Maximální optimalizace (upřednostnění rychlosti)** – ekvivalent/og/Oi/ot/Oy/Ob2/GS/GF/Gy
- **Optimalizace (upřednostnit rychlost)** – ekvivalent/og/Oi/ot/Oy/Ob2

### <a name="inline-function-expansion"></a>Rozšíření vložené funkce

Vyberte úroveň rozšíření [vložené funkce](../../cpp/inline-functions-cpp.md) pro sestavení. Nastaví [/OB1,/Ob2](ob-inline-function-expansion.md).

#### <a name="choices"></a>Vlastnit

- **Výchozí**
- **Disabled** – zakáže vložené rozšíření, které je ve výchozím nastavení zapnuté.
- **Pouze __inline** – rozbalí pouze funkce označené jako **inline**, `__inline`, `__forceinline`nebo `__inline`. Nebo v C++ členské funkci definované v rámci deklarace třídy.
- **Všechny vhodné** funkce rozšíření označené jako **vložené** nebo `__inline` a všechny další funkce, které kompilátor zvolí. (K rozšíření dochází na uvážení kompilátoru, často se označuje jako *Automatické vkládání*.)

### <a name="enable-intrinsic-functions"></a>Povolit vnitřní funkce

Povolí vnitřní funkce.  Použití vnitřních funkcí generuje rychlejší, ale pravděpodobně větší, kód. Nastaví [/Oi](oi-generate-intrinsic-functions.md).

### <a name="favor-size-or-speed"></a>Upřednostnit velikost nebo rychlost

Zda se má upřednostnit velikost kódu nebo rychlost kódu; Je nutné zapnout globální optimalizaci. Nastaví [/ot,/OS](os-ot-favor-small-code-favor-fast-code.md).

#### <a name="choices"></a>Vlastnit

- **Upřednostnit malý** kód pro upřednostnění kódu. Minimalizuje velikost exe a knihoven DLL tím, že instruuje kompilátor, aby upřednostňuje velikost před rychlostí.
- **Upřednostnit rychlý** kód pro rychlé upřednostnění kódu Maximalizuje rychlost exe a knihoven DLL tím, že instruuje kompilátor o upřednostnění rychlosti. (Výchozí hodnota je.)
- **Není k** dispozici žádná Optimalizace velikosti a rychlosti.

### <a name="omit-frame-pointers"></a>Vynechat ukazatele na rámec

Zakazuje vytváření ukazatelů na rámce v zásobníku volání.

### <a name="enable-fiber-safe-optimizations"></a>Povolit optimalizace bezpečné pro vlákna

Povoluje optimalizaci paměťového prostoru při použití vláken a přístup k thread localmu úložišti. Nastaví [/gt](gt-support-fiber-safe-thread-local-storage.md).

### <a name="whole-program-optimization"></a>Optimalizace celého programu

Umožňuje optimalizaci mezi moduly tím, že se odloží generování kódu na čas propojení. Vyžaduje možnost linkeru "generování kódu při propojování". Nastaví [/GL](gl-whole-program-optimization.md).

## <a name="cc-preprocessor-properties"></a>Vlastnosti CC++ /preprocesoru

### <a name="preprocessor-definitions"></a>Definice preprocesoru

Definuje symboly předzpracování pro zdrojový soubor.

### <a name="undefine-preprocessor-definitions"></a>Zrušit Definice preprocesoru

Určuje jeden nebo více zrušení definujících preprocesoru. Nastaví [/u](u-u-undefine-symbols.md).

### <a name="undefine-all-preprocessor-definitions"></a>Zrušit definici všech definic preprocesoru

Zruší definici všech dříve definovaných hodnot preprocesoru. Nastaví [/u](u-u-undefine-symbols.md).

### <a name="ignore-standard-include-paths"></a>Ignorovat standardní cesty zahrnutí

Zabraňuje kompilátoru v hledání souborů k zahrnutí v adresářích zadaných v proměnných prostředí INCLUDE.

### <a name="preprocess-to-a-file"></a>Předzpracovat do souboru

Předzpracovává C a C++ zdrojové soubory a zapisuje předzpracovaný výstup do souboru. Tato možnost potlačí kompilaci a nevytvoří soubor *`.obj`* .

### <a name="preprocess-suppress-line-numbers"></a>Potlačit čísla řádků při předzpracování

Předzpracování bez #line direktiv

### <a name="keep-comments"></a>Zachovat komentáře

Potlačí pruh komentáře ze zdrojového kódu; vyžaduje, aby byla nastavena jedna z možností předzpracování. Nastaví [/c](c-preserve-comments-during-preprocessing.md).

## <a name="cc-code-generation-properties"></a>Vlastnosti generováníC++ kódu C//

### <a name="enable-string-pooling"></a>Povolit sdružování řetězců

Kompilátor vytvoří v imagi programu pouze jednu kopii stejného řetězce jen pro čtení. Výsledkem je menší programy, optimalizace označované jako *sdružování řetězců*. [/O1,/O2](o-options-optimize-code.md)a [/Zi](z7-zi-zi-debug-information-format.md) automaticky nastaví možnost [/GF](gf-eliminate-duplicate-strings.md) .

### <a name="enable-minimal-rebuild"></a>Povolit minimální opětovné sestavení

Povoluje minimální opětovné sestavení, které určuje, zda se mají C++ znovu kompilovat zdrojové soubory, C++ které obsahují změněné definice třídy, uložené v hlavičkách *`.h`* soubory.

### <a name="enable-c-exceptions"></a>Povolit C++ výjimky

Určuje model zpracování výjimek, který má kompilátor použít.

#### <a name="choices"></a>Vlastnit

- **Ano, s výjimkami SEH** – model zpracování výjimek, který zachytává asynchronní (strukturované) aC++synchronní () výjimky. Nastaví [/EHa](eh-exception-handling-model.md).
- **Ano** – model zpracování výjimek, který zachytává C++ pouze výjimky a instruuje kompilátor, aby předpokládal, že externí funkce jazyka C C++ nikdy nevyvolají výjimku. Nastaví [/EHsc](eh-exception-handling-model.md).
- **Ano s funkcemi extern jazyka C** – model zpracování výjimek, který zachytává C++ pouze výjimky a instruuje kompilátor, aby předpokládal, že externí funkce jazyka c vyvolávají výjimku. Nastaví [/EHS](eh-exception-handling-model.md).
- **Bez** zpracování výjimek.

### <a name="smaller-type-check"></a>Kontrola menšího typu

Povolte kontrolu převodu na menší typy, nekompatibilní s jinými typy optimalizace než s laděním. Nastaví [/RTCc](rtc-run-time-error-checks.md).

### <a name="basic-runtime-checks"></a>Základní kontroly za běhu

Povolit základní kontroly chyb za běhu, nekompatibilní s žádným typem optimalizace jiným než ladění. Nastaví [/RTCs,/RTCu,/RTC1](rtc-run-time-error-checks.md).

#### <a name="choices"></a>Vlastnit

- **Rámce zásobníku** – povolí kontrolu chyb rámce zásobníku za běhu.
- **Neinicializované proměnné** – sestavy při použití proměnné bez inicializace.
- **Obě (/RTC1, equiv. to/RTCsu)** – ekvivalent hodnoty/rtcsu
- **Výchozí** – výchozí kontroly za běhu.

### <a name="runtime-library"></a>Běhová knihovna

Zadejte běhovou knihovnu pro propojování. Nastaví [/Mt,/MTD,/MD,/MDD](md-mt-ld-use-run-time-library.md).

#### <a name="choices"></a>Vlastnit

- **Vícevláknové** – způsobí, že aplikace použije vícevláknovou statickou verzi knihovny run-time.
- **Vícevláknové ladění** – definuje _DEBUG a _MT. Tato možnost také způsobí, že kompilátor umístí knihovnu *LIBCMTD. lib* do souboru *`.obj`* , takže linker použije *LIBCMTD. lib* k vyřešení externích symbolů.
- **Vícevláknová knihovna DLL** – způsobí, že vaše aplikace bude používat knihovnu run-time specifickou pro knihovnu DLL určenou pro více vláken a. Definuje _MT a _DLL a způsobí, že kompilátor umístí do souboru *`.obj`* knihovnu s názvem *Msvcrt. lib* .
- **Vícevláknová knihovna DLL pro ladění** – definuje _DEBUG, _MT a _DLL a způsobí, že vaše aplikace použije ladění běhové knihovny, která je specifická pro knihovnu DLL. Také způsobí, že kompilátor umístí do souboru *`.obj`* název knihovny *msvcrtd. lib* .

### <a name="struct-member-alignment"></a>Zarovnání členů struktury

Určuje hranice 1, 2, 4 nebo 8 bajtů pro zarovnání členů struktury. Nastaví [/zp](zp-struct-member-alignment.md).

#### <a name="choices"></a>Vlastnit

- **1 bajtové** sady strukturují hranice na 1 bajtech. Stejné jako **`/Zp`** .
- **2 bajty** – sady se strukturují na hranicích na dvou bajtech.
- **4 bajty** – sady se strukturují na hranicích na 4 bajtech.
- **8 bajtů** – sady pro struktury na hranici 8 bajtů (výchozí).
- **16 bajtů** – sady se strukturují na hranici 16 bajtů.
- **Výchozí** nastavení – výchozí zarovnání

### <a name="security-check"></a>Kontrolu zabezpečení

Kontrola zabezpečení pomáhá detekovat přetečení vyrovnávací paměti zásobníku, což je běžný pokus o útok na zabezpečení programu.

#### <a name="choices"></a>Vlastnit

- **Zakázat kontrolu zabezpečení** – zakázat kontrolu zabezpečení. Nastaví [/GS-](gs-buffer-security-check.md).
- **Povolit kontrolu zabezpečení** – povolit kontrolu zabezpečení. Nastaví [/GS](gs-buffer-security-check.md).

### <a name="control-flow-guard"></a>Ochrana toku řízení

Kontrola zabezpečení Guard pomáhá detekovat pokusy o odeslání do neplatného bloku kódu.

#### <a name="choices"></a>Vlastnit

- **Ano** – povolit kontrolu zabezpečení pomocí sady Guard [/Guard: CF](guard-enable-control-flow-guard.md).
- **Ne**

### <a name="enable-function-level-linking"></a>Povolit propojování na úrovni funkcí

Umožňuje kompilátoru zabalit jednotlivé funkce ve formě zabalených funkcí (sekvence COMDAT). Vyžaduje se pro úpravy a pokračování v práci. Nastaví [/Gy](gy-enable-function-level-linking.md).

### <a name="enable-parallel-code-generation"></a>Povolit generování paralelního kódu

Umožňuje kompilátoru generovat paralelní kód pro cykly identifikované pomocí `#pragma loop(hint_parallel[(n)])`, pokud je povolena optimalizace.

### <a name="enable-enhanced-instruction-set"></a>Povolit rozšířenou sadu instrukcí

Povolí použití instrukcí, které se nacházejí na procesorech podporujících rozšířené sady instrukcí. Například vylepšení SSE, SSE2, AVX a AVX2 pro platformu IA-32. A, AVX a AVX2 vylepšení na platformě x64. Aktuálně **`/arch:SSE`** a **`/arch:SSE2`** jsou k dispozici pouze při sestavování pro architekturu x86. Pokud není zadána žádná možnost, kompilátor použije pokyny nalezené u procesorů, které podporují SSE2. Použití rozšířených instrukcí se dá v **`/arch:IA32`** zakázat. Další informace najdete v tématu [/arch (x86)](arch-x86.md), [/arch (x64)](arch-x64.md) a [/arch (ARM)](arch-arm.md).

#### <a name="choices"></a>Vlastnit

- **Streaming SIMD Extensions** -streaming SIMD Extensions. Nastaví **`/arch:SSE`**
- **Streaming SIMD Extensions 2** – streaming SIMD Extensions 2. Nastaví **`/arch:SSE2`**
- **Rozšířená rozšíření vektoru** – Pokročilá rozšíření vektoru. Nastaví **`/arch:AVX`**
- **Rozšířená rozšíření vektorů 2** – rozšířená rozšíření vektoru 2. Nastaví **`/arch:AVX2`**
- **Bez rozšířených instrukcí** – bez rozšířených instrukcí Nastaví **`/arch:IA32`**
- **Nenastaveno** -není nastaveno.

### <a name="floating-point-model"></a>Model plovoucí desetinné čárky

Nastaví model plovoucí desetinné čárky. Nastaví [/FP: Restricted,/FP: Strict,/FP: Fast](fp-specify-floating-point-behavior.md).

#### <a name="choices"></a>Vlastnit

- **Přesné** – výchozí. Vylepšuje konzistenci testů s plovoucí desetinnou čárkou pro rovnost a nerovnost.
- **Striktní** – nejpřísnější model plovoucí desetinné čárky. **`/fp:strict`** způsobí, že **`fp_contract`** vypnuto a **`fenv_access`** být zapnuté. **`/fp:except`** je předpokládaná a je možné ji zakázat explicitním zadáním **`/fp:except-`** . Při použití s **`/fp:except-`** **`/fp:strict`** vynutila striktní sémantiku s plovoucí desetinnou čárkou, ale bez ohledu na výjimečné události.
- **Fast** – vytvoří ve většině případů nejrychlejší kód.

### <a name="enable-floating-point-exceptions"></a>Povolit výjimky s plovoucí desetinnou čárkou

Spolehlivý model výjimek s plovoucí desetinnou čárkou Výjimky budou vyvolány okamžitě po aktivaci. Nastaví [/FP: except](fp-specify-floating-point-behavior.md).

### <a name="create-hotpatchable-image"></a>Vytvoření image opravitelnou za provozu

Když je technologie HotPatching zapnutá, kompilátor zajistí, že první instrukce každé funkce jsou dvě bajty, jak je potřeba pro Hot patching. Nastaví [/hotpatch](hotpatch-create-hotpatchable-image.md).

### <a name="spectre-mitigation"></a>Zmírnění Spectre

Spectre zmírnění hrozeb pro CVE 2017-5753. Nastaví [/Qspectre](qspectre.md).

#### <a name="choices"></a>Vlastnit

- **Povoleno** – povolit funkci zmírnění Spectre pro CVE 2017-5753
- **Zakázané** – nenastavené

## <a name="cc-language-properties"></a>Vlastnosti jazykaC++ C/jazyka

### <a name="disable-language-extensions"></a>Zakázat jazyková rozšíření

Potlačí nebo povolí jazyková rozšíření. Nastaví [/za](za-ze-disable-language-extensions.md).

### <a name="conformance-mode"></a>Režim shody

Povolí nebo potlačí režim shody. Nastaví [/Permissive-](permissive-standards-conformance.md).

### <a name="treat-wchar_t-as-built-in-type"></a>Považovat WChar_t za vestavěný typ

Je-li tato možnost zadána, typ **wchar_t** se změní do nativního typu, který se mapuje na `__wchar_t` stejným způsobem jako **krátká** mapování na `__int16`. [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) je ve výchozím nastavení zapnuté.

### <a name="force-conformance-in-for-loop-scope"></a>Vynutit shodu oboru smyčky for

Slouží k implementaci standardního C++ chování pro smyčky příkazů for s rozšířeními Microsoftu. Nastaví [/za,/ze (zakáže jazyková rozšíření](za-ze-disable-language-extensions.md). [/Zc: forScope](zc-forscope-force-conformance-in-for-loop-scope.md) je ve výchozím nastavení zapnuté.

### <a name="remove-unreferenced-code-and-data"></a>Odebrat neodkazovaný kód a data

Je-li zadán parametr, kompilátor již negeneruje informace o symbolech pro neodkazovaný kód a data.

### <a name="enforce-type-conversion-rules"></a>Vynucení pravidel převodu typů

Slouží k identifikaci typu odkazu rvalue jako výsledku operace přetypování na Standard C++ 11.

### <a name="enable-run-time-type-information"></a>Povolit informace běhového typu

Přidá kód pro kontrolu C++ typů objektů v době běhu (informace o typu modulu runtime). Nastaví [/gr,/GR-](gr-enable-run-time-type-information.md).

### <a name="open-mp-support"></a>Otevřít podporu MP

Povolí jazykové rozšíření OpenMP 2,0. Nastaví [/OpenMP](openmp-enable-openmp-2-0-support.md).

### <a name="c-language-standard"></a>C++Standardní jazyk

Určuje C++ jazykový Standard, který kompilátor povoluje. Pokud je to možné, použijte nejnovější verzi. Nastaví [/std: c++ 14,/std: c++ 17,/std: c + + nejnovější](std-specify-language-standard-version.md).

#### <a name="choices"></a>Vlastnit

- **Výchozí**
- **Standard ISO C++ 14**
- **Standard ISO C++ 17**
- **Náhled – funkce z nejnovější C++ pracovní verze**

### <a name="enable-c-modules-experimental"></a>Povolit C++ moduly (experimentální)

Experimentální podpora C++ modulů TS a standardní moduly knihovny.

## <a name="cc-precompiled-headers-properties"></a>Vlastnosti předkompilovaných hlaviček jazyka C/C++

### <a name="createuse-precompiled-header"></a>Vytvořit/použít předkompilovanou hlavičku

Povolí vytvoření nebo použití předkompilované hlavičky během sestavení. Nastaví [/YC](yc-create-precompiled-header-file.md), [/Yu](yu-use-precompiled-header-file.md).

#### <a name="choices"></a>Vlastnit

- **Create** – instruuje kompilátor, aby vytvořil soubor předkompilované hlavičky (. pch), který představuje stav kompilace v určitém bodě.
- **Pomocí** -instruuje kompilátor, aby v aktuální kompilaci použil existující soubor předkompilované hlavičky (. pch).
- **Bez použití předkompilovaných hlaviček** – bez použití předkompilovaných hlaviček.

### <a name="precompiled-header-file"></a>Soubor předkompilované hlavičky

Určuje název hlavičkového souboru, který se má použít při vytváření nebo používání souboru předkompilované hlavičky. Nastaví [/YC](yc-create-precompiled-header-file.md), [/Yu]] (Yu-use-Předkompilovaná-header-File.MD).

### <a name="precompiled-header-output-file"></a>Výstupní soubor předkompilované hlavičky

Určuje cestu nebo název generovaného souboru předkompilované hlavičky. Nastaví [/FP](fp-name-dot-pch-file.md).

## <a name="cc-output-files-properties"></a>Vlastnosti CC++ /výstupních souborů

### <a name="expand-attributed-source"></a>Rozbalit zdroj s atributy

Vytvoří soubor výpisu s rozbalenými atributy vloženými do zdrojového souboru. Nastaví [/FX](fx-merge-injected-code.md).

### <a name="assembler-output"></a>Výstup assembleru

Určuje obsah výstupního souboru jazyka sestavení. Nastaví [/FA,/FAc,/FAS,/FAcs](fa-fa-listing-file.md).

#### <a name="choices"></a>Vlastnit

- **Žádný výpis** – žádný výpis
- **Výpis pouze sestavení** – kód sestavení; *`.asm`*
- **Sestavení s počítačovým kódem** – počítač a kód sestavení; *`.cod`*
- **Sestavení se** zdrojovým kódem a kódem sestavení; *`.asm`*
- **Sestavení, strojové kódy a zdrojové** sestavení, strojový kód a zdrojový kód; *`.cod`*

### <a name="use-unicode-for-assembler-listing"></a>Použití Unicode pro výpis assembleru

Způsobí, že se výstupní soubor vytvoří ve formátu UTF-8.

### <a name="asm-list-location"></a>Umístění seznamu ASM

Určuje relativní cestu nebo název souboru výpisu ASM; může být název souboru nebo adresáře. Nastaví [/FA](fa-fa-listing-file.md).

### <a name="object-file-name"></a>Název souboru objektu

Určuje název, kterým se má přepsat výchozí název souboru objektu. může být název souboru nebo adresáře. Nastaví [/FO](fo-object-file-name.md).

### <a name="program-database-file-name"></a>Název souboru databáze programu

Určuje název souboru PDB generovaného kompilátorem; Určuje také základní název pro požadovaný soubor IDB generovaný kompilátorem; může být název souboru nebo adresáře. Nastaví [/FD](fd-program-database-file-name.md).

### <a name="generate-xml-documentation-files"></a>Generovat soubory dokumentace XML

Určuje, že má kompilátor generovat soubory komentáře dokumentace XML (. XDC). Nastaví [/doc](doc-process-documentation-comments-c-cpp.md).

### <a name="xml-documentation-file-name"></a>Název souboru dokumentace XML

Určuje název generovaných souborů dokumentace XML; může být název souboru nebo adresáře. Nastaví [/DOC: > název\<](doc-process-documentation-comments-c-cpp.md).

## <a name="cc-browse-information-properties"></a>Vlastnosti informacíC++ o C/Procházet

### <a name="enable-browse-information"></a>Povolit informace o procházení

Určuje úroveň informací o procházení v souboru *`.bsc`* . Nastaví [/fr](fr-fr-create-dot-sbr-file.md).

### <a name="browse-information-file"></a>Soubor s informacemi o procházení

Určuje nepovinný název souboru s informacemi o prohlížeči. Nastaví [/FR\<název >](fr-fr-create-dot-sbr-file.md).

## <a name="cc-advanced-properties"></a>Vlastnosti CC++ /pokročilé

### <a name="calling-convention"></a>Konvence volání

Vyberte výchozí konvenci volání aplikace (může být přepsána funkcí). Nastaví [/GD,/GR,/GZ,/GV](gd-gr-gv-gz-calling-convention.md).

#### <a name="choices"></a>Vlastnit

- **__cdecl** – určuje __cdecl konvenci volání pro všechny funkce s C++ výjimkou členských funkcí a funkcí označených __stdcall nebo __fastcall.
- **__fastcall** – určuje __fastcall konvenci volání pro všechny funkce s C++ výjimkou členských funkcí a funkcí označených __cdecl nebo __stdcall. Všechny funkce __fastcall musí mít prototypy.
- **__stdcall** – určuje __stdcall konvenci volání pro všechny funkce s C++ výjimkou členských funkcí a funkcí označených __cdecl nebo __fastcall. Všechny funkce __stdcall musí mít prototypy.
- **__vectorcall** – určuje __vectorcall konvenci volání pro všechny funkce s C++ výjimkou členských funkcí a funkcí označených __cdecl, __fastcall nebo __stdcall. Všechny funkce __vectorcall musí mít prototypy.

### <a name="compile-as"></a>Kompilovat jako

Umožňuje vybrat možnost jazyka kompilace pro soubory *`.c`* a *`.cpp`* . Nastaví [/TC,/TP](tc-tp-tc-tp-specify-source-file-type.md).

#### <a name="choices"></a>Vlastnit

- **Výchozí** – výchozí.
- **Kompilovat jako kód jazyka c** – kompilovat jako kód jazyka c.
- **Kompilovat jako C++**  kód – kompilovat jako C++ kód.

### <a name="disable-specific-warnings"></a>Zakázat specifická upozornění

Zakáže zadaná čísla upozornění. Číslice upozornění uveďte v seznamu oddělených středníky. Nastaví [/wd\<num >](compiler-option-warning-level.md).

### <a name="forced-include-file"></a>Vynucený soubor k zahrnutí

jeden nebo více souborů s vynuceným zahrnutím. Nastaví [/fi\<název >](fi-name-forced-include-file.md).

### <a name="forced-using-file"></a>Vynucený soubor #using

Určuje jeden nebo více vynucených #using souborů. Nastaví [/fu\<název >](fu-name-forced-hash-using-file.md).

### <a name="show-includes"></a>Zobrazit zahrnutí

Generuje seznam souborů k zahrnutí s výstupem kompilátoru. Nastaví [/showIncludes](showincludes-list-include-files.md).

### <a name="use-full-paths"></a>Použít úplné cesty

Používejte v diagnostických zprávách úplné cesty. Nastaví [/FC](fc-full-path-of-source-code-file-in-diagnostics.md).

### <a name="omit-default-library-name"></a>Vynechat název výchozí knihovny

Nezahrnuje názvy výchozích knihoven v *`.obj`* soubory. Nastaví [/zl](zl-omit-default-library-name.md).

### <a name="internal-compiler-error-reporting"></a>Zasílání zpráv o vnitřních chybách kompilátoru

> [!NOTE]
> Tato možnost je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

### <a name="treat-specific-warnings-as-errors"></a>Považovat specifická upozornění za chyby

Zpracovává konkrétní upozornění kompilátoru jako chybu, kde n je upozornění kompilátoru.

### <a name="additional-options"></a>Další možnosti

Další možnosti
