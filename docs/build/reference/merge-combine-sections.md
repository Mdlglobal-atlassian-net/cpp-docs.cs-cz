---
title: /MERGE (kombinované oddíly)
ms.date: 11/04/2016
f1_keywords:
- /merge
- VC.Project.VCLinkerTool.MergeSections
helpviewer_keywords:
- sections, combining
- /MERGE linker option
- sections, naming
- sections
- -MERGE linker option
- MERGE linker option
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
ms.openlocfilehash: e0329c6a29a8667a09a56d894386f5c173a77916
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532181"
---
# <a name="merge-combine-sections"></a>/MERGE (kombinované oddíly)

```
/MERGE:from=to
```

## <a name="remarks"></a>Poznámky

Parametr / merge Sloučí první oddíl (*z*) s druhým oddílem (*k*), výsledný oddíl *k*. Například `/merge:.rdata=.text`.

Pokud se druhý oddíl neexistuje, přejmenuje odkaz v části *z* jako *k*.

/ Merge možnost je užitečná pro vytváření ovladače VxD a přepisování názvy oddílů generovaný kompilátorem.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **sloučení oddílů** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)