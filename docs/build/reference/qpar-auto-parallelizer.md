---
title: /Qpar (automatický modul pro paralelní zpracování)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: c1ddea73c5aa8d3e7e70b45834cb04154bf3b4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319223"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (automatický modul pro paralelní zpracování)

Umožňuje [automatický Paralelizér](../../parallel/auto-parallelization-and-auto-vectorization.md) funkce kompilátoru, aby automaticky umožní souběžné smyčky ve vašem kódu.

## <a name="syntax"></a>Syntaxe

```
/Qpar
```

## <a name="remarks"></a>Poznámky

Když kompilátor automaticky parallelizes smyčky v kódu, šíří výpočtu mezi více jádry procesoru. Smyčka je paralelizovaná pouze v případě, že kompilátor zjistí, že je možné provést a že paralelizace by mohly zlepšit výkon.

`#pragma loop()` Direktivy připravené vám pomoct optimalizace paralelní zpracování konkrétní smyčky. Další informace najdete v tématu [smyčky](../../preprocessor/loop.md).

Informace o tom, jak povolit výstupní zprávy pro automatický paralelizér, naleznete v tématu [/Qpar-report (úroveň sestav automatický Paralelizér)](qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /Qpar v sadě Visual Studio

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.

1. V **stránky vlastností** dialogovém okně **C/C++** vyberte **příkazového řádku**.

1. V **další možnosti** zadejte `/Qpar`.

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Nastavení parametru kompilátoru /Qpar prostřednictvím kódu programu

- Použijte tento příklad kódu v <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](q-options-low-level-operations.md)<br/>
[/Qpar-report (úroveň generování sestav s automatickou paralelizací)](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[#pragma loop()](../../preprocessor/loop.md)<br/>
[Paralelní programování v nativním kódu](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
