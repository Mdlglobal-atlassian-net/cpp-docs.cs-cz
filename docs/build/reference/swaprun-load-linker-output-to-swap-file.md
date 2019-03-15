---
title: /SWAPRUN (Načíst výstup linkeru do souboru odkládacího souboru)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
ms.openlocfilehash: bd0b3a46f52ec9b5a292e2f45671523d8c5cdf5e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817488"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Načíst výstup linkeru do souboru odkládacího souboru)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>Poznámky

/ Swaprun přikazuje operačnímu systému, aby první Kopírovat výstup linkeru do odkládacího souboru a pak spusťte image z něj. Toto je funkce Windows NT 4.0 (a novější).

Pokud síť není zadána, operační systém nejprve bitovou kopii ze sítě do odkládacího souboru a načtěte ho z něj. Tato možnost je užitečný ke spouštění aplikací v síti. Pokud je zadána CD, operační systém se zkopírovat bitovou kopii na vyměnitelném disku do stránkovacího souboru a pak ji zavede.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **systému** stránku vlastností.

1. Změňte některou z následujících vlastností:

   - **Spuštění odkládacího souboru z disku CD-ROM.**

   - **Spuštění odkládacího souboru ze sítě**

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> vlastnosti.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
