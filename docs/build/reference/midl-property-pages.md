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
ms.openlocfilehash: d6833230baca892836c187799df7f0658aa16772
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336242"
---
# <a name="midl-property-pages"></a>MIDL – stránky vlastností

Stránky vlastností MIDL jsou k dispozici jako vlastnost položky na . IDL soubor v projektu C++, který používá COM. Použijte je ke konfiguraci [kompilátoru MIDL](/windows/win32/midl/using-the-midl-compiler-2). Informace o tom, jak programově přistupovat k možnostem <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> MIDL pro projekty jazyka C++, naleznete v tématu objekt. Viz také [Obecná syntaxe příkazového řádku MIDL](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Stránka obecné vlastnosti

### <a name="preprocessor-definitions"></a>Definice preprocesoru

Určuje jednu nebo více definic, včetně maker\]MIDL ([/D](/windows/win32/midl/-d)).\[

### <a name="additional-include-directories"></a>Další zahrnutí adresářů

Určuje jeden nebo více adresářů, které chcete přidat\]do cesty zahrnutí ([/I](/windows/win32/midl/-i)\[cesta ).

### <a name="additional-metadata-directories"></a>Další adresáře metadat

Zadejte adresář obsahující soubor Windows.Foundation.WinMD (\][/metadata_dir](/windows/win32/midl/-metadata-dir) \[cesta ).

### <a name="enable-windows-runtime"></a>Povolení prostředí Windows Runtime

Povolte sémantiku prostředí Windows Runtime k vytvoření souboru metadat systému Windows ([/winrt](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignorovat standardní cestu zahrnutí

Ignorujte aktuální adresáře a adresáře INCLUDE ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>Kompatibilní s MkTypLib

Vynutí kompatibilitu s mktyplib.exe verze 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Úroveň upozornění

Vybere přísnost chyb kódu MIDL ([/W](/windows/win32/midl/-w)).

**Choices**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Považovat upozornění za chyby

Umožňuje MIDL považovat všechna upozornění za chyby ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Potlačit spouštěcí banner

Potlačit zobrazení spouštěcího banneru a informační zprávy ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>C Typ znaku kompilátoru

Určuje výchozí typ znaku kompilátoru Jazyka C, který bude použit ke kompilaci generovaného kódu. ([/char](/windows/win32/midl/-char) signed|unsigned|ascii7).

**Choices**

- **Podepsáno** - podepsáno
- **Nepodepsáno** - nepodepsané
- **Ascii** - Ascii

### <a name="target-environment"></a>Cílové prostředí

Určuje, na které prostředí se má cílit ([/env](/windows/win32/midl/-env) arm32|win32|ia64|x64).

**Choices**

- **Není nastaveno** - Win32
- **Microsoft Windows 32-bit** - Win32
- **Microsoft Windows 64-bit na Itanium** - IA64
- **Microsoft Windows ARM** – ARM
- **Microsoft Windows ARM64** - ARM64
- **Microsoft Windows 64-bit na x64** - X64

### <a name="generate-stubless-proxies"></a>Generovat proxy servery bez útržku

Generovat plně interpretované zástupné procedury s rozšířeními a proxy servery bez útržku pro rozhraní objektů ([/Oicf](/windows/win32/midl/-oi), [/Oif](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Potlačení upozornění kompilátoru

Potlačit varovné zprávy kompilátoru ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Režim konfigurace aplikace

Povolit vybrané atributy ACF v souboru IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>ID národního prostředí

Určuje soubor LCID pro vstupní soubory, názvy souborů a cesty adresářů ([/lcid](/windows/win32/midl/-lcid) DECIMAL).

### <a name="multi-processor-compilation"></a>Kompilace s více procesory

Spusťte více instancí současně.

## <a name="output-property-page"></a>Stránka výstupní vlastnosti

### <a name="output-directory"></a>Výstupní adresář

Určuje výstupní adresář ([/out](/windows/win32/midl/-out) [directory]).

### <a name="metadata-file"></a>Soubor metadat

Určuje název generovaného souboru metadat ([/winmd](/windows/win32/midl/-winmd) název souboru).

### <a name="header-file"></a>Soubor záhlaví

Určuje název generovaného souboru záhlaví ([/h](/windows/win32/midl/-h) název souboru).

### <a name="dlldata-file"></a>Soubor DllData

Určuje název souboru DLLDATA ( název souboru[/dlldata).](/windows/win32/midl/-dlldata)

### <a name="iid-file"></a>IID soubor

Určuje název souboru identifikátoru rozhraní ([/iid](/windows/win32/midl/-iid) název souboru).

### <a name="proxy-file"></a>Soubor proxy

Určuje název souboru proxy ([/proxy](/windows/win32/midl/-proxy) název souboru).

### <a name="generate-type-library"></a>Generovat knihovnu typů

Zadejte, chcete-li nevygenerovat knihovnu typů ([/notlb] pro ne).

### <a name="type-library"></a>Knihovna typů

Určuje název souboru knihovny typů ([/tlb](/windows/win32/midl/-tlb) název souboru).

### <a name="generate-client-stub-files"></a>Generovat soubory se zakázaným inzerováním klienta

Generovat pouze soubor se zakázaným inzerováním klienta ([/client](/windows/win32/midl/-client) [stub|none]).

**Choices**

- **Pahýl** - Pahýl
- **Žádné** - Žádné

### <a name="generate-server-stub-files"></a>Generovat soubory se zakázaným inzerováním serveru

Generovat pouze soubor se zakázaným inzerováním serveru ([/server](/windows/win32/midl/-server) [stub|none]).

**Choices**

- **Pahýl** - Pahýl
- **Žádné** - Žádné

### <a name="client-stub-file"></a>Soubor se zakázaným inzerováním klienta

Zadejte soubor se zakázaným inzerováním klienta ([/cstub](/windows/win32/midl/-cstub) [file]).

### <a name="server-stub-file"></a>Soubor se zakázaným inzerováním serveru

Zadejte soubor se zakázaným inzerováním serveru ([/sstub](/windows/win32/midl/-sstub) [file]).

### <a name="type-library-format"></a>Formát knihovny typů

Určuje formát souboru knihovny typů ([/oldtlb|/newtlb]).

**Choices**

- **NewFormat** - Nový formát
- **OldFormat** - starý formát

## <a name="advanced-property-page"></a>Stránka rozšířené vlastnosti

### <a name="c-preprocess-options"></a>C Možnosti předběžného zpracování

Určuje přepínače, které mají být předávány přepínacímu procesoru C ([/cpp_opt](/windows/win32/midl/-cpp-opt) přepínače).

### <a name="undefine-preprocessor-definitions"></a>Nedefinovat definice preprocesoru

Určuje jednu nebo více nedefinovate, včetně maker MIDL ([/U](/windows/win32/midl/-U) [makra]).

### <a name="enable-error-checking"></a>Povolit kontrolu chyb

Vyberte možnost kontroly chyb ([/error all|none]).

**Choices**

- **EnableCustom** - vše
- **Vše** - Vše
- **Žádné** - Žádné

### <a name="check-allocations"></a>Zkontrolovat přidělení

Zkontrolujte chyby nedostatku paměti ([/error](/windows/win32/midl/-error) allocation).

### <a name="check-bounds"></a>Zkontrolovat hranice

Zkontrolujte velikost vs specifikace délky přenosu[(/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Zkontrolovat rozsah výčtu

Zkontrolujte, zda výčet hodnoty mají být v povoleném rozsahu ([/error](/windows/win32/midl/-error) výčet).

### <a name="check-reference-pointers"></a>Kontrola ukazatelů odkazů

Zkontrolujte ukazatele ref, které mají být non-null ([/error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>Kontrola dat se zakázaným inzerováním

Vyzařují další kontrolu platnosti dat se zakázaným inzerováním na straně serveru ([/error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Předřadit s oborem názvů ABI

Předřadit obor názvů ABI na všechny typy.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Ověřit parametry

Vygenerujte další informace pro ověření parametrů ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Zarovnání členů struktury

Určuje úroveň balení konstrukcí v cílovém systému (/ZpN).

**Choices**

- **Není nastaveno** - není nastaveno
- **1 Bajt** - Zp1
- **2 Bajt** - Zp2
- **4 Bajt** - Zp4
- **8 Bajt** - Zp8

### <a name="redirect-output"></a>Výstup přesměrování

Přesměruje výstup z obrazovky na soubor ([/o.](/windows/win32/midl/-o)

### <a name="minimum-target-system"></a>Minimální cílový systém

Nastavte minimální cílový systém ([/target](/windows/win32/midl/-target) STRING).
