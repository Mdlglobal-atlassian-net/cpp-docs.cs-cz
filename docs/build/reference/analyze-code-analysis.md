---
title: -analyze (Analýza kódu) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4893f30bae3b29538c8bead637cb4d083087a57b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="analyze-code-analysis"></a>/analyze (Analýza kódu)

Umožňuje zadat parametry pro analýzu a řízení kódu.

## <a name="syntax"></a>Syntaxe

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Arguments

 /analyze  
 Zapne analýzu ve výchozím režimu. Výstup analýzy přejde na **výstup** okno jako další chybové zprávy. Použití **/ analyze –** explicitně vypnout analýzy.

 /analyze:WX-  
 Určení **/ analyze: WX –** znamená, že upozornění analýzy kódu nejsou považovány za chyby při kompilaci pomocí **wdn**. Další informace najdete v tématu [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md).

 / analyze: protokolu `filename`  
 Analyzátor podrobné výsledky se zapisují jako XML soubor, který je zadán `filename`.

 /analyze:quiet  
 Vypnutím analyzátor výstup do **výstup** okno.

 / analyze: velikost zásobníku `number`  
 `number` Parametr, který se používá tato možnost určuje velikost v bajtech, pro které upozornění rámce zásobníku [C6262](/visualstudio/code-quality/c6262) se vygeneruje. Pokud tento parametr není zadán, má rámec zásobníku ve výchozím nastavení velikost 16 kB.

 / analyze: max_paths `number`  
 `number` Parametr, který se používá tato možnost určuje maximální počet cesty kódu má být analyzován. Pokud tento parametr není zadán, je ve výchozím nastavení tento počet 256. Vyšší hodnoty provádějí důkladnější kontrolu, ale analýza může trvat déle.

 /analyze:only  
 Kompilátor zpravidla generuje kód a po spuštění analýzy provádí další kontrolu syntaxe. **/ Analyze: pouze** možnost vypne Tento průchod generování kódu; díky tomu analysis rychlejší, ale nejsou vygenerované kompilace chyby a upozornění, které může byly zjištěny předejte generování kódu kompilátoru. Pokud program obsahuje chyby generování kódu, mohou být výsledky analýzy nespolehlivé; proto doporučujeme, abyste tento parametr použili pouze v případě, že kód již prošel kontrolou syntaxe generování kódu bez chyb.

 / analyze: ruleset `<file_path>.ruleset`  
Umožňuje určit, které pravidlo nastaví pro analýzu, včetně vlastních sad pravidel, můžete vytvořit sami. Když tento přepínač nastavíte, stroj pravidel je efektivnější, protože se vyloučí, které nejsou členy zadané sady pravidel, kterou dřív, než spustíte. Pokud není nastaven přepínač, modul kontroluje všechna pravidla.

Sady pravidel, které jsou dodávány pomocí sady Visual Studio se nacházejí v **%VSINSTALLDIR%\Team sad Tools\Rule Tools\Static analýzy.**

Následující ukázkové sady vlastní pravidlo informuje stroj pravidel kontroluje C6001 a C26494. Tento soubor můžete umístit kdekoli, dokud má `.ruleset` rozšíření a můžete zadat úplnou cestu v argumentu.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze: modulu plug-in  
Umožňuje zadaný PREfast modul plug-in běží v rámci analýzy kódu. LocalEspC.dll je modul plug-in, který implementuje analýzy kódu pro concurrency související kontroluje v rozsahu C261XX upozornění. Například [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Spustit LocalEspC.dll, použijte tuto možnost kompilátoru: **/ analyze: modul plug-in LocalEspC.dll**

Pokud chcete spustit CppCoreCheck.dll, nejprve spusťte tento příkaz z příkazového řádku vývojáře:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Potom pomocí této možnosti kompilátoru: **/ analyze: modul plug-in EspXEngine.dll**.

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [analýzy kódu pro C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) a [analýzy kódu pro C/C++ upozornění](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **analýza kódu** uzlu.

1. Vyberte **Obecné** stránku vlastností.

1. Změňte jednu nebo více **analýza kódu** vlastnosti.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

1. V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru](../../build/reference/compiler-options.md)
- [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)