---
title: -Fo (název souboru objektů) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9ab671cbae276796ce89ec12cecbc16334e234e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724238"
---
# <a name="fo-object-file-name"></a>/Fo (název souboru objektů)

Určuje název souboru objektů (.obj) nebo adresáře se použije místo výchozího.

## <a name="syntax"></a>Syntaxe

```
/Fopathname
```

## <a name="remarks"></a>Poznámky

Pokud tuto možnost nepoužijete, soubor objektu používá základní název zdrojového souboru a příponou. Můžete použít libovolný název a příponu, která má, ale doporučené konvence je použít. Knihovna

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **výstupní soubory** stránku vlastností.

1. Upravit **název souboru objektů** vlastnost.  Ve vývojovém prostředí, soubor objektu musí mít příponu. Knihovna

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz vytvoří objektový soubor s názvem THIS.obj v existující adresář, \OBJECT, na jednotce B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Viz také

[Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)