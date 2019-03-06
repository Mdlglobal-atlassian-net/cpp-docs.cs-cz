---
title: /HEAP (Nastavit velikost haldy)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 500e1eca9385697829edca46e5e703a5238684a7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422368"
---
# <a name="heap-set-heap-size"></a>/HEAP (Nastavit velikost haldy)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Možnost /HEAP nastaví velikost haldy v bajtech. Tato možnost je pouze pro použití při vytváření souboru s příponou .exe.

*Rezervovat* argument určuje celkový počet haldy ve virtuální paměti. Výchozí velikost haldy je 1 MB. Linker se zaokrouhlí nahoru zadanou hodnotu do nejbližší 4 bajty.

Volitelný `commit` argument určuje množství fyzické paměti do okamžiku přidělit. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší `commit` hodnotu šetří čas, kdy aplikace potřebuje více místa v haldě, ale zvyšuje požadavky na paměť a případně i čas spuštění.

Zadejte *rezervovat* a `commit` hodnoty v desítkovém zápisu nebo v zápisu jazyka.

Tato funkce je také k dispozici prostřednictvím souboru definice modulu s [HEAPSIZE](../../build/reference/heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **systému** stránku vlastností.

1. Upravit **velikost potvrzení změn haldy** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
