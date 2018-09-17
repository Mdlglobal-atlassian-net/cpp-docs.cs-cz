---
title: -showIncludes (seznam vložených souborů) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs:
- C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51305212f97482c6963ee2ba0d272c5c4692416e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709384"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)