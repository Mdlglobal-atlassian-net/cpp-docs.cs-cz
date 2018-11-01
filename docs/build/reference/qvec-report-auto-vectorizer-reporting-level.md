---
title: /Qvec-report (Úroveň sestavy s automatickou vektorizací)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: dc8c1d3bc65b0160fd489f1cdebe06e4fc9a0992
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590226"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Úroveň sestavy s automatickou vektorizací)

Povolí funkci vykazování sady kompilátor [automatický Vektorizér](../../parallel/auto-parallelization-and-auto-vectorization.md) a určuje úroveň pro výstup informačních zpráv během kompilace.

## <a name="syntax"></a>Syntaxe

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Poznámky

**/ Qvec-report: 1**<br/>
Vypíše informační zpráva pro smyčky, které jsou vektorizována.

**/ Qvec-report: 2**<br/>
Vypíše informační zpráva pro smyčky, které jsou vektorizovaná a smyček, které nejsou společně s kód důvodu vektorizována.

Informace o kódech příčiny a zprávy najdete v tématu [zprávy nástrojů pro vektorizaci a](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /Qvec-report v sadě Visual Studio

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.

1. V **stránky vlastností** dialogovém okně **C/C++** vyberte **příkazového řádku**.

1. V **další možnosti** zadejte `/Qvec-report:1` nebo `/Qvec-report:2`.

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Nastavení parametru kompilátoru /Qvec-report prostřednictvím kódu programu

- Použijte tento příklad kódu v <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Paralelní programování v nativním kódu](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)