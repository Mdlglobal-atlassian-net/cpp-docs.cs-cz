---
title: Stránky vlastností kompilátoru MIDL
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 260936d01a611f061b0b4fa9a5c087ff38cc66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076134"
---
# <a name="midl-property-pages"></a>MIDL – stránky vlastností

Stránky vlastností MIDL jsou k dispozici jako vlastnost položky v. Soubor IDL v C++ projektu, který používá com. Použijte je ke konfiguraci [kompilátoru MIDL](/windows/win32/midl/using-the-midl-compiler-2). Informace o tom, jak programově přistupovat k možnostem C++ MIDL pro projekty, naleznete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> Object. Viz také [Obecná syntaxe příkazového řádku MIDL](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Obecná stránka vlastností

### <a name="preprocessor-definitions"></a>Definice preprocesoru

Určuje jednu nebo více definic, včetně maker MIDL ([/d](/windows/win32/midl/-d))\[maker\]).

### <a name="additional-include-directories"></a>Další adresáře k zahrnutí

Určuje jeden nebo více adresářů, které mají být přidány do cesty include ([/i](/windows/win32/midl/-i)\[cesta\]).

### <a name="additional-metadata-directories"></a>Další adresáře metadat

Zadejte adresář obsahující soubor Windows. Foundation. WinMD ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[cesta\]).

### <a name="enable-windows-runtime"></a>Povolit prostředí Windows Runtime

Povolit sémantiku prostředí Windows Runtime k vytvoření souboru metadat systému Windows ([/WinRT](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignorovat standardní cestu zahrnutí

Ignorujte aktuální a adresáře INCLUDE ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>Kompatibilní s MkTypLib

Vynutí kompatibilitu s MkTypLib. exe verze 2,03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Úroveň upozornění

Vybere striktní chyby kódu MIDL ([/w](/windows/win32/midl/-w)).

**Vlastnit**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby

Umožňuje MIDL považovat všechna upozornění za chyby ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Potlačit úvodní nápis

Potlačí zobrazení úvodního nápisu a informační zprávy ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>Typ znaku kompilátoru jazyka C

Určuje výchozí znakový typ kompilátoru jazyka C, který bude použit ke kompilaci generovaného kódu. (podpis[/char](/windows/win32/midl/-char) | unsigned | ascii7).

**Vlastnit**

- Podepsaný **podpisem**
- **Unsigned** – bez znaménka
- **ASCII** – ASCII

### <a name="target-environment"></a>Cílové prostředí

Určuje, které prostředí se má cílit ([/ENV](/windows/win32/midl/-env) arm32 | Win32 | ia64 | x64).

**Vlastnit**

- **Nenastaveno** -Win32
- **Microsoft Windows 32 – bit** – Win32
- **Microsoft Windows 64 – bit v Itanium** -ia64
- **Microsoft Windows ARM** – ARM
- **Microsoft Windows ARM64** – ARM64
- **Microsoft Windows 64 – bit na platformě x64** – x64

### <a name="generate-stubless-proxies"></a>Generovat proxy bez zástupných procedur

Vygenerujte plně interpretované zástupné procedury s rozšířeními a proxy servery bez zástupných procedur pro rozhraní objektů ([/oicf](/windows/win32/midl/-oi), [/OIF](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Potlačení upozornění kompilátoru

Potlačit varovné zprávy kompilátoru ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Režim konfigurace aplikace

Povolí vybrané atributy ACF v souboru IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>ID národního prostředí

Určuje LCID pro vstupní soubory, názvy souborů a cesty adresáře ([/LCID](/windows/win32/midl/-lcid) Decimal).

### <a name="multi-processor-compilation"></a>Kompilace s využitím více procesorů

Spouštějte více instancí současně.

## <a name="output-property-page"></a>Výstupní stránka vlastností

### <a name="output-directory"></a>Výstupní adresář

Určuje výstupní adresář ([/out](/windows/win32/midl/-out) [adresář]).

### <a name="metadata-file"></a>Soubor metadat

Určuje název generovaného souboru metadat ([/winmd](/windows/win32/midl/-winmd) filename).

### <a name="header-file"></a>Hlavičkový soubor

Určuje název vygenerovaného souboru hlaviček ([/h](/windows/win32/midl/-h) filename).

### <a name="dlldata-file"></a>Soubor DllData

Určuje název souboru DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) filename).

### <a name="iid-file"></a>IID – soubor

Určuje název souboru identifikátoru rozhraní ([/IID](/windows/win32/midl/-iid) filename).

### <a name="proxy-file"></a>Soubor proxy

Určuje název souboru proxy ([/proxy](/windows/win32/midl/-proxy) filename).

### <a name="generate-type-library"></a>Generovat knihovnu typů

Určete, že se nemá generovat knihovna typů ([/notlb] pro ne).

### <a name="type-library"></a>Knihovna typů

Určuje název souboru knihovny typů ([/TLB](/windows/win32/midl/-tlb) filename).

### <a name="generate-client-stub-files"></a>Vygenerovat soubory zástupných procedur klienta

Vygenerujte pouze zástupný soubor klienta ([/Client](/windows/win32/midl/-client) [zástupné soubory | None]).

**Vlastnit**

- **Stub** – zástupná procedura
- **Žádné** – žádné

### <a name="generate-server-stub-files"></a>Generovat soubory zástupných procedur serveru

Vygenerujte jenom soubor stub serveru ([/Server](/windows/win32/midl/-server) [zástupné procedury | None]).

**Vlastnit**

- **Stub** – zástupná procedura
- **Žádné** – žádné

### <a name="client-stub-file"></a>Soubor stub klienta

Zadejte soubor stub klienta ([/cstub](/windows/win32/midl/-cstub) [soubor]).

### <a name="server-stub-file"></a>Soubor se zástupnými procedurami serveru

Zadejte soubor zástupných procedur serveru ([/sstub](/windows/win32/midl/-sstub) [soubor]).

### <a name="type-library-format"></a>Formát knihovny typů

Určuje formát souboru knihovny typů ([/oldtlb |/newtlb]).

**Vlastnit**

- **NewFormat** – nový formát
- **OldFormat** – starý formát

## <a name="advanced-property-page"></a>Upřesnit stránku vlastností

### <a name="c-preprocess-options"></a>Možnosti předzpracování jazyka C

Určuje přepínače předané preprocesoru kompilátoru jazyka C ([/cpp_optm](/windows/win32/midl/-cpp-opt) přepínačům).

### <a name="undefine-preprocessor-definitions"></a>Zrušit Definice preprocesoru

Určuje jednu nebo více undefined, včetně maker MIDL ([/u](/windows/win32/midl/-U) [makra]).

### <a name="enable-error-checking"></a>Povolit kontrolu chyb

Vyberte možnost kontroly chyb ([/Error All | None]).

**Vlastnit**

- **EnableCustom** – vše
- **Vše** – vše
- **Žádné** – žádné

### <a name="check-allocations"></a>Kontrolovat přidělení

Podívejte se na chyby z důvodu nedostatku paměti ([/Error](/windows/win32/midl/-error) Allocation).

### <a name="check-bounds"></a>Kontrolovat meze

Kontrolní velikost vs specifikace přenosové délky ([/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Kontrolovat rozsah výčtu

Ověřte, jestli hodnoty výčtu mají být v povoleném rozsahu ([/Error](/windows/win32/midl/-error) Enum).

### <a name="check-reference-pointers"></a>Kontrolovat referenční ukazatele

Kontroluje, zda odkazují ukazatele na hodnotu nenulového typu ([/Error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>Kontrolovat data zástupných procedur

Vygeneruje další kontrolu platnosti dat zástupných procedur na straně serveru ([/error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Předřadit obor názvů ABI

Předřaďte obor názvů ABI všem typům.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Ověřit parametry

Vygenerujte Další informace pro ověřování parametrů ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Zarovnání členů struktury

Určuje úroveň balení struktur v cílovém systému (/ZpN).

**Vlastnit**

- **Nenastavené** – nenastavené
- **1 bajt** – Zp1
- **2 bajt** – Zp2
- **4 bajt** – Zp4
- **8 bajtů** – ZP8

### <a name="redirect-output"></a>Přesměrovat výstup

Přesměruje výstup z obrazovky do souboru ([/o](/windows/win32/midl/-o) File).

### <a name="minimum-target-system"></a>Minimální cílový systém

Nastavte minimální cílový systém ([/target](/windows/win32/midl/-target) řetězec).
