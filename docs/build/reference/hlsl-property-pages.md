---
title: HLSL – stránky vlastností
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: a45ae433e5adaa8aeaf32215d4af7ad0a247af04
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606407"
---
# <a name="hlsl-compiler-property-pages"></a>Stránky vlastností kompilátoru HLSL

Pomocí stránky vlastností kompilátoru HLSL (fxc. exe) můžete nakonfigurovat, jak jsou sestaveny jednotlivé soubory HLSL shaderu. Argumenty příkazového řádku kompilátoru HLSL můžete zadat také pomocí vlastnosti **Další možnosti** na stránce vlastností **příkazového řádku** . To zahrnuje argumenty, které se nedají konfigurovat pomocí jiných vlastností HLSL stránek vlastností. Informace o kompilátoru HLSL naleznete v tématu [efekt – nástroj kompilátoru](https://go.microsoft.com/fwlink/p/?LinkID=258285&clcid=0x409) .

## <a name="hlsl-general-property-page"></a>Obecná stránka vlastností HLSL

### <a name="additional-include-directories"></a>Další adresáře k zahrnutí

Určuje jeden nebo více adresářů, které mají být přidány do cesty include; oddělte je středníkem, pokud je více než jedna. (/I [cesta])

### <a name="entrypoint-name"></a>Název vstupního bodu

Určuje název vstupního bodu pro shader (/E [název])

### <a name="disable-optimizations"></a>Zakázat optimalizace

**Ano (/od)** pro zákaz optimalizace; v opačném případě **ne**. Ve výchozím nastavení je hodnota **Yes (/od)** pro konfiguraci **ladění** a **ne** pro konfigurace **vydání** .

Argument příkazového řádku **/od** pro kompilátor HLSL implicitně používá argument příkazového řádku **/GFP** , ale výstup nemusí být totožný s výstupem vytvořeným předáním argumentů příkazového řádku **/od** a **/GFP** . explicitně.

### <a name="enable-debugging-information"></a>Povolit ladicí informace

**Ano (/Zi)** pro povolení ladicích informací; v opačném případě **ne**. Ve výchozím nastavení je tato hodnota **Ano (/Zi)** pro konfiguraci **ladění** a **ne** pro konfigurace **vydání** .

### <a name="shader-type"></a>Typ shaderu

Určuje druh shaderu. Různé druhy shaderů implementují různé části grafického kanálu. Některé druhy shaderů jsou k dispozici pouze v novějších modelech shaderů (které jsou určeny vlastností **modelu shaderu** ) – například byly představeny výpočetní shadery v modelu shaderu 5.

Tato vlastnost odpovídá  **\[typu]** v argumentu příkazového řádku **/t \[Type] _\[model]** kompilátoru HLSL. Vlastnost **model shader** určuje část **[model]** argumentu.

**Vlastnit**

- **Účinek**
- **Vertex shader**
- **Pixel shader**
- **Shader geometrie**
- **Shader trupu**
- **Shader domény**
- **Výpočetní shader**
- **Knihovna**
- **Generovat objekt kořenového podpisu**

### <a name="shader-model"></a>Model shaderu

Určuje model shaderu. Různé modely shaderů mají různé možnosti. Obecně platí, že novější modely shaderů nabízejí rozšířené možnosti, ale vyžadují pokročilejší grafický hardware pro spuštění kódu shaderu. Některé druhy shaderů (které jsou určené vlastností **typu shaderu** ) jsou k dispozici pouze v novějších modelech shaderu, například výpočetní shadery byly představeny v modelu shader model 5.

Tato vlastnost odpovídá  **\[modelu]** v argumentu příkazového řádku **/t \[Type] _\[model]** kompilátoru HLSL. Vlastnost **Type shader** určuje část **[type]** argumentu.

### <a name="all-resources-bound"></a>Všechny prostředky svázané

Kompilátor bude předpokládat, že všechny prostředky, na které může shader odkazovat, jsou svázané a jsou v dobrém stavu po dobu trvání spuštění shaderu (/all_resources_bound). K dispozici pro shader model 5,1 a vyšší.

### <a name="enable-unbounded-descriptor-tables"></a>Povolit neohraničené tabulky deskriptorů

Informujte kompilátor, že shader může obsahovat deklaraci pole prostředků s neohraničeným rozsahem (/enable_unbounded_descriptor_tables). K dispozici pro shader model 5,1 a vyšší.

### <a name="set-root-signature"></a>Nastavit kořenový podpis

Připojte kořenový podpis k bytovému kódu shaderu (/setrootsignature). K dispozici pro shader model 5,0 a vyšší.

### <a name="preprocessor-definitions"></a>Definice preprocesoru

Přidá jednu nebo více definic symbolů preprocesoru, které se použijí pro soubor zdrojového kódu HLSL. K oddělení definic symbolů použijte středníkem.

Tato vlastnost odpovídá argumentu příkazového řádku  **\[/d definitions]** kompilátoru HLSL.

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>Kompilovat vlastní efekt pixel shaderu Direct2D

Zkompilujte vlastní efekt Direct2D, který obsahuje pixel shadery. Nepoužívejte pro svůj vlastní efekt vrcholů nebo výpočtů.

### <a name="multi-processor-compilation"></a>Kompilace více procesorů

Spouštějte více instancí současně.

## <a name="advanced-property-page"></a>Upřesnit stránku vlastností

### <a name="suppress-startup-banner"></a>Potlačit úvodní nápis

Potlačí zobrazení úvodního nápisu a informační zprávy. /nologo

### <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby

Zpracovává všechna upozornění kompilátoru jako chyby. Pro nový projekt může být nejvhodnější používat/WX ve všech kompilacích; řešení všech upozornění zajistí nejmenší možné nedostatky v obtížném hledání kódu.

## <a name="output-files-property-page"></a>Stránka vlastností výstupní soubory

### <a name="header-variable-name"></a>Název proměnné záhlaví

Určuje název proměnné v hlavičkovém souboru (/vn [název]).

### <a name="header-file-name"></a>Název hlavičkového souboru

Určuje název hlavičkového souboru obsahujícího kód objektu. (/FH [název])

### <a name="object-file-name"></a>Název souboru objektu

Určuje název souboru objektu. (/FO [název])

### <a name="assembler-output"></a>Výstup assembleru

Určuje obsah výstupního souboru jazyka sestavení. (/FC,/FX)

**Vlastnit**

- **Žádný výpis** – žádný výpis
- **Výpis pouze sestavení** -soubor kódu sestavení
- **Kód sestavení a hexadecimální** kód sestavení a soubor s výpisem šestnáctkové soustavy

### <a name="assembler-output-file"></a>Výstupní soubor assembleru

Určuje název souboru výpisu kódu sestavení.

## <a name="see-also"></a>Viz také:

[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)<br>
[Stránky vlastností příkazového řádku](command-line-property-pages.md)<br>
[Kompilování shaderů](https://go.microsoft.com/fwlink/p/?LinkID=258284&clcid=0x409)
