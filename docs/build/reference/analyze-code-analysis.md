---
title: /analyze (analýza kódu)
ms.date: 10/15/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: f537fdea2703805c7ab1c57ba0d4429f6b683ae4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444898"
---
# <a name="analyze-code-analysis"></a>/analyze (analýza kódu)

Umožňuje zadat parametry pro analýzu a řízení kódu.

## <a name="syntax"></a>Syntaxe

> **/analyze**[-] [ **: WX-** ] [ **: log** *filename*] [ **: quiet**] [ **: STACKSIZE** *Number*] [ **: max_paths** *číslo*] [ **: pouze**] [ **: RuleSet** *RuleSet*] [ **:p lugin** *plugin-DLL*]

## <a name="arguments"></a>Arguments

\ **/analyze**
Zapne analýzu ve výchozím režimu. Výstup analýzy přejde do okna **výstup** jako jiné chybové zprávy. K explicitnímu vypnutí analýzy použijte **/analyze-** .

**/analyze: WX-** \
Upozornění analýzy kódu nejsou při kompilaci pomocí **/WX**považována za chyby. Další informace najdete v tématu [/WX (úroveň upozornění)](compiler-option-warning-level.md).

**/analyze:** *název souboru* protokolu\
Podrobné výsledky analyzátoru se zapisují jako XML do souboru zadaného parametrem *filename*.

**/analyze: quiet**\
Vypne výstup analyzátoru do okna **výstup** .

**/analyze: STACKSIZE** *číslo*\
Parametr *Number* , který se používá s touto možností, určuje velikost rámce zásobníku, pro který je vygenerováno upozornění [C6262](/visualstudio/code-quality/c6262) . Mezera před *číslem* je volitelná. Pokud tento parametr není zadán, velikost rámce zásobníku je ve výchozím nastavení 16 KB.

**/analyze: max_paths** *číslo*\
Parametr *Number* , který se používá s tímto parametrem, určuje maximální počet cest kódu, které se mají analyzovat. Pokud není tento parametr zadán, bude ve výchozím nastavení číslo 256. Větší hodnoty způsobují důkladnější kontrolu, ale analýza může trvat delší dobu.

**/analyze: pouze**\
Kompilátor zpravidla generuje kód a po spuštění analýzy provádí další kontrolu syntaxe. Možnost **/analyze: Only** vypne průchod generování kódu. Zrychluje analýzu, ale chyby a upozornění, které může být generováno při generování kódu kompilátoru, se nemusí vydávat. Pokud program neuvolní chyby generování kódu, výsledky analýzy mohou být nespolehlivé. Tuto možnost doporučujeme použít pouze v případě, že kód již projde kontrolu syntaxe pro generování kódu bez chyb.

**/analyze: ruleset** *file_path. ruleset*\
Umožňuje určit, které sady pravidel se mají analyzovat, včetně vlastních sad pravidel, které můžete vytvořit sami. Pokud je tento přepínač nastaven, modul pravidel je efektivnější, protože před spuštěním vyloučí nečleny zadané sady pravidel. V opačném případě modul kontroluje všechna pravidla.

RuleSets, který se dodává se sadou Visual Studio, najdete v *sadě%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule sady.*

Následující ukázková sada vlastních pravidel informuje modul pravidel, aby kontroloval C6001 a C26494. Tento soubor můžete umístit kdekoli, dokud má příponu `.ruleset` a v argumentu zadáte úplnou cestu.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

**/analyze:** *plugin* modulů plug-in –\ dll
Povolí zadaný rychlý modul plug-in v rámci spuštění analýzy kódu.

::: moniker range="<=vs-2017"

LocalEspC. dll je modul plug-in, který implementuje kontroly analýzy kódu související s souběžnou analýzou v rozsahu upozornění C261XX. Například [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pokud chcete spustit LocalEspC. dll, použijte tuto možnost kompilátoru: **/analyze: plugin LocalEspC. dll.**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck. dll implementuje kontroly analýzy kódu související s souběžnou analýzou v rozsahu upozornění C261XX. Například [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Chcete-li spustit ConcurrencyCheck. dll, nejprve spusťte tento příkaz z příkazového řádku pro vývojáře:

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

Pak použijte tuto možnost kompilátoru: **/analyze: plugin EspXEngine. dll**.

::: moniker-end

Chcete-li spustit CppCoreCheck. dll, nejprve spusťte tento příkaz z příkazového řádku pro vývojáře:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Pak použijte tuto možnost kompilátoru: **/analyze: plugin EspXEngine. dll**.

## <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Analýza kódu pro c/C++ přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) a [Analýza kódu pro c/C++ upozornění](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **Obecné** > **Analýza kódu** .

1. Upravte jednu nebo více vlastností **analýzy kódu** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Viz také:

\ [možností kompilátoru MSVC](compiler-options.md)
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
