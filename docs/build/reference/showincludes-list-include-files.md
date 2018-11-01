---
title: /showIncludes (seznam vložených souborů)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
ms.openlocfilehash: 7be3d93f91133ad1a29e6b4d6d2c50157a3376b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523042"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (seznam vložených souborů)

Způsobí, že kompilátor výstup seznam vložených souborů. Vnořené zahrnout soubory jsou také zobrazené (soubory, které jsou zahrnuty ze souborů, které zahrnete).

## <a name="syntax"></a>Syntaxe

```
/showIncludes
```

## <a name="remarks"></a>Poznámky

Při vloženého souboru dochází během kompilace, zpráva se výstup, například:

```
Note: including file: d:\MyDir\include\stdio.h
```

Vnořené zahrnout soubory jsou označeny odsazení, jeden prostor pro každou úroveň vnoření, například:

```
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

V takovém případě `2.h` byla zahrnuta z v rámci `1.h`, proto odsazení.

**/Showincludes** možnost vysílá do `stderr`, nikoli `stdout`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **zobrazit zahrnuje** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)