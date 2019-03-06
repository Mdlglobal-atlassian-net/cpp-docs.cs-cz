---
title: /Fo (název souboru objektů)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: bcb0f96eba277b65e3478843ca0e1666f9c404aa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418357"
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

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz vytvoří objektový soubor s názvem THIS.obj v existující adresář, \OBJECT, na jednotce B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)
