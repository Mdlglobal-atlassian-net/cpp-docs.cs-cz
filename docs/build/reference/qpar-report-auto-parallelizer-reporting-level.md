---
title: /Qpar-report (úroveň sestav s automatickou vektorizací)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 4ab14f890d888664b2847f3e3d4b193d7c77da1a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419904"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (úroveň sestav s automatickou vektorizací)

Povolí funkci vykazování sady kompilátoru [automatický Paralelizér](../../parallel/auto-parallelization-and-auto-vectorization.md) a určuje úroveň pro výstup informačních zpráv během kompilace.

## <a name="syntax"></a>Syntaxe

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Poznámky

**/Qpar-report:1**<br/>
Vypíše informační zpráva pro smyčky, které jsou paralelizována.

**/Qpar-report:2**<br/>
Vypíše informační zpráva pro smyčky, které jsou paralelizovaná a také pro smyčky, které nejsou společně s kód důvodu paralelizována.

Zprávy se hlásí do stdout. Pokud jsou hlášeny žádné informační zprávy, pak buď kód obsahuje žádnému zacyklení, nebo zadané úrovni vytváření sestav nebyla nastavena do smyčky sestavy, které nejsou paralelizována. Další informace o kódech příčiny a zprávy v tématu [zprávy nástrojů pro vektorizaci a](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /Qpar-report v sadě Visual Studio

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.

1. V **stránky vlastností** dialogovém okně **C/C++** vyberte **příkazového řádku**.

1. V **další možnosti** zadejte `/Qpar-report:1` nebo `/Qpar-report:2`.

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Nastavení parametru kompilátoru /Qpar-report prostřednictvím kódu programu

- Použijte tento příklad kódu v <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Paralelní programování v nativním kódu](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
