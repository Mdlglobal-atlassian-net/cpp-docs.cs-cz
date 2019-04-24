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
ms.openlocfilehash: 27de554e1933b2753f641be358461c8d7ff4fffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317923"
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

Dalším způsobem, jak nastavit velikost zásobníku je [STACKSIZE](stacksize.md) prohlášení v souboru definice modulu (.def). **STACKSIZE** přidělení zásobníku (/ STACK) Pokud jsou zadány oba. Po sestavení souboru .exe s použitím můžete změnit velikost zásobníku [EDITBIN](editbin-reference.md) nástroj.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **systému** stránku vlastností.

1. Změňte některou z následujících vlastností:

   - **Velikost potvrzení zásobníku**

   - **Velikost rezervace zásobníku**

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> vlastnosti.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
