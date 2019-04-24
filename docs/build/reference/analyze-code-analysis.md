---
title: /analyze (Analýza kódu)
ms.date: 04/26/2018
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
ms.openlocfilehash: 63cfd2bd206a361301c75110a684e1d2c642a1f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273154"
---
# <a name="analyze-code-analysis"></a>/analyze (Analýza kódu)

Umožňuje zadat parametry pro analýzu a řízení kódu.

## <a name="syntax"></a>Syntaxe

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Arguments

/ analyze zapne na analýzu ve výchozím režimu. Výstup analýzy se zobrazuje **výstup** okna jako další chybové zprávy. Použití **/ analyze-** k explicitnímu vypnutí analýzy.

/ analyze: WX-zadání **/ analyze: WX -** znamená, že upozornění analýzy kódu, které nemají být považována za chyby při kompilaci pomocí **/WX**. Další informace najdete v tématu [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](compiler-option-warning-level.md).

/ analyze: log `filename` podrobné výsledky analýzy jsou zapsány jako XML soubor, který je určen `filename`.

/ analyze: quiet zapne vypnout výstup analýzy **výstup** okna.

/ analyze: stacksize `number` `number` parametr, který se používá tato možnost určuje velikost v bajtech rámce zásobníku, pro které upozornění [C6262](/visualstudio/code-quality/c6262) je generován. Pokud tento parametr není zadán, má rámec zásobníku ve výchozím nastavení velikost 16 kB.

/ analyze: max_paths `number` `number` parametr, který se používá s tímto parametrem, určuje maximální počet analyzovaných cest kódu. Pokud tento parametr není zadán, je ve výchozím nastavení tento počet 256. Vyšší hodnoty provádějí důkladnější kontrolu, ale analýza může trvat déle.

/ analyze: pouze obvykle, kompilátor generuje kód a provádí další kontrolu po spuštění analýzy syntaxe. **/ Analyze: pouze** volba vypne tuto fázi generování kódu; tím se urychlí analýza, ale nejsou zaznamenávány chyby a upozornění, které mohou být zjištěna ve fázi generování kódu kompilátoru kompilace. Pokud program obsahuje chyby generování kódu, mohou být výsledky analýzy nespolehlivé; proto doporučujeme, abyste tento parametr použili pouze v případě, že kód již prošel kontrolou syntaxe generování kódu bez chyb.

/ analyze: ruleset `<file_path>.ruleset` umožňuje určit pravidlo, které nastaví pro analýzu, včetně vlastních sad pravidel, můžete vytvořit sami. Když tento přepínač nastavený, stroj pravidel je mnohem efektivnější, protože nezahrnuje jiné členy zadané sady dřív, než spustíte pravidel. Pokud není nastaven přepínač, modul kontroluje všechna pravidla.

Sady pravidel, které se dodávají pomocí sady Visual Studio se nacházejí v **%VSINSTALLDIR%\Team sad Tools\Rule Tools\Static analýzy.**

Následující ukázkové sady vlastních pravidel říká stroj pravidel kontroluje C6001 a C26494. Tento soubor můžete umístit kamkoli za předpokladu, má `.ruleset` rozšíření a můžete zadat úplnou cestu v argumentu.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze: modul plug-in umožňuje zadaný modul plug-in PREfast jako součást analýza kódu spuštěna.
LocalEspC.dll je modul plug-in, který implementuje analýzy souběžnosti související kód se změnami rozsah C261XX upozornění. Například [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Spustit LocalEspC.dll, použijte tuto možnost kompilátoru: **/ analyze: modul plug-in LocalEspC.dll**

Pokud chcete spustit CppCoreCheck.dll, nejprve spusťte tento příkaz z příkazového řádku pro vývojáře:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Pak pomocí této možnosti kompilátoru: **/ analyze: modul plug-in EspXEngine.dll**.

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [analýzy kódu pro C/C++ přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) a [analýzy kódu pro C/C++ upozornění](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **analýzy kódu** uzlu.

1. Vyberte **Obecné** stránku vlastností.

1. Změnit jedno nebo více **analýzy kódu** vlastnosti.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Viz také:

- [Parametry kompilátoru MSVC](compiler-options.md)
- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
