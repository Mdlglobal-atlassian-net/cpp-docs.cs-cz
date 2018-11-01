---
title: /STACK (přidělení zásobníku)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
ms.openlocfilehash: 2ccdd33c77f5c7bfa9ee5dcd041f6778e8eb85d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572026"
---
# <a name="stack-stack-allocations"></a>/STACK (přidělení zásobníku)

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Možnost /STACK nastaví velikost zásobníku v bajtech. Tuto možnost použijte pouze v případě, že sestavujete soubor .exe.

Hodnota `reserve` určuje celkové přidělení zásobníku ve virtuální paměti. Pro ARM je x86 a x64 počítače, je výchozí velikost zásobníku 1 MB.

Parametr `commit` podléhá interpretaci operačního systému. V systémech Windows RT určuje množství fyzické paměti, kterou lze v jednom okamžiku přidělit. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší hodnota `commit` šetří čas, potřebuje-li aplikace více místa v zásobníku, ale zvyšuje požadavky na paměť a případně i čas spuštění. Pro ARM je x86 a x64 počítače, je výchozí potvrzená hodnota 4 KB.

Hodnoty `reserve` a `commit` zadávejte v desítkovém zápisu nebo v zápisu jazyka C.

Dalším způsobem, jak nastavit velikost zásobníku je [STACKSIZE](../../build/reference/stacksize.md) prohlášení v souboru definice modulu (.def). **STACKSIZE** přidělení zásobníku (/ STACK) Pokud jsou zadány oba. Po sestavení souboru .exe s použitím můžete změnit velikost zásobníku [EDITBIN](../../build/reference/editbin-reference.md) nástroj.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **systému** stránku vlastností.

1. Změňte některou z následujících vlastností:

   - **Velikost potvrzení zásobníku**

   - **Velikost rezervace zásobníku**

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> vlastnosti.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)