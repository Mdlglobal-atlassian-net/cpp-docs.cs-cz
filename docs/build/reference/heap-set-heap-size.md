---
title: /HEAP (Nastavit velikost haldy)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: f155ad56ec1a90479b402e38e7ec7f3e3d80e470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439520"
---
# <a name="heap-set-heap-size"></a>/HEAP (Nastavit velikost haldy)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Možnost/HEAP nastaví velikost haldy v bajtech. Tato možnost je použita pouze při vytváření souboru. exe.

Argument *Reserve* Určuje celkové přidělení haldy ve virtuální paměti. Výchozí velikost haldy je 1 MB. Linker zaokrouhlí zadanou hodnotu na nejbližší 4 bajty.

Volitelný `commit` argument určuje velikost fyzické paměti, která se má přidělit v čase. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší hodnota `commit` šetří čas, když aplikace potřebuje více místa v haldě, ale zvyšuje požadavky na paměť a případně i čas spuštění.

Zadejte hodnoty *rezervy* a `commit` v desítkovém nebo jazykovém zápisu jazyka C.

Tato funkce je také k dispozici prostřednictvím definičního souboru modulu s [Velikost haldy](heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **linker** .

1. Klikněte na stránku vlastnost **systému** .

1. Upravte vlastnost **Velikost potvrzené velikosti haldy** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz témata <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
