---
title: /analyze (analýza kódu)
ms.date: 10/01/2019
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
ms.openlocfilehash: d647045d76dc32544f8146424b220547890b0943
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816324"
---
# <a name="analyze-code-analysis"></a>/analyze (analýza kódu)

Povoluje analýzu kódu a možnosti řízení.

## <a name="syntax"></a>Syntaxe

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumenty

/Analyze zapne analýzu ve výchozím režimu. Výstup analýzy přejde do okna **výstup** jako jiné chybové zprávy. K explicitnímu vypnutí analýzy použijte **/analyze-** .

/analyze: WX-specifikovat **/analyze: WX-** znamená, že při kompilaci pomocí **/WX**se nepovažují upozornění analýzy kódu jako chyby. Další informace najdete v tématech [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](compiler-option-warning-level.md).

/analyze: log `filename` podrobné výsledky analyzátoru jsou zapsány jako XML do souboru určeného `filename`.

/analyze: quiet vypne výstup analyzátoru do okna **výstup** .

/analyze: STACKSIZE `number` parametr `number`, který se používá s touto možností určuje velikost rámce zásobníku, pro který je vygenerováno upozornění [C6262](/visualstudio/code-quality/c6262) . Mezera před `number` je volitelná. Pokud tento parametr není zadán, velikost rámce zásobníku je ve výchozím nastavení 16 KB.

/analyze: max_paths `number` parametr `number`, který se používá s touto možností určuje maximální počet cest kódu, které se mají analyzovat. Pokud tento parametr není zadán, bude ve výchozím nastavení číslo 256. Větší hodnoty provádějí důkladnější kontrolu, ale analýza může trvat delší dobu.

/analyze: obvykle kompilátor vygeneruje kód a po spuštění analyzátoru provede více kontroly syntaxe. Možnost **/analyze: Only** vypne průchod generování kódu; Díky tomu je analýza rychlejší, ale chyby kompilace a upozornění, která mohla být zjištěna předáním generování kódu kompilátorem, nejsou generována. Pokud program neuvolní chyby generování kódu, výsledky analýzy mohou být nespolehlivé; Proto doporučujeme použít tuto možnost pouze v případě, že kód již projde kontrolu syntaxe pro generování kódu bez chyb.

/analyze: RuleSet `<file_path>.ruleset` umožňuje určit, které sady pravidel se mají analyzovat, včetně vlastních sad pravidel, které můžete vytvořit sami. Pokud je tento přepínač nastaven, modul pravidel je efektivnější, protože před spuštěním vyloučí nečleny zadané sady pravidel. Když není přepínač nastavený, modul zkontroluje všechna pravidla.

RuleSets, který se dodává se sadou Visual Studio, najdete v **sadě%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule sady.**

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

/analyze: modul plug-in umožňuje spustit zadaný modul plug-in v rámci analýzy kódu.
LocalEspC. dll je modul plug-in, který implementuje kontroly analýzy kódu související s souběžnou analýzou v rozsahu upozornění C261XX. Například [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pokud chcete spustit LocalEspC. dll, použijte tuto možnost kompilátoru: **/analyze: plugin LocalEspC. dll.**

Chcete-li spustit CppCoreCheck. dll, nejprve spusťte tento příkaz z příkazového řádku pro vývojáře:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Pak použijte tuto možnost kompilátoru: **/analyze: plugin EspXEngine. dll**.

## <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Analýza kódu pro c/C++ přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) a [Analýza kódu pro c/C++ upozornění](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení této možnosti kompilátoru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte uzel **Vlastnosti konfigurace** .

1. Rozbalte uzel **Analýza kódu** .

1. Vyberte stránku vlastností **Obecné** .

1. Upravte jednu nebo více vlastností **analýzy kódu** .

### <a name="to-set-this-compiler-option-programmatically"></a>Chcete-li nastavit tuto možnost kompilátoru programově

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Další informace najdete v tématech

- [Možnosti kompilátoru MSVC](compiler-options.md)
- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
