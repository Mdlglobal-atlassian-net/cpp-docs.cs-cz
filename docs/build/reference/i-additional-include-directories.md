---
title: -I (Další adresáře souborů k zahrnutí) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs:
- C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a580488650a1272ec1dffcd1f0ba27c736df92da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705338"
---
# <a name="i-additional-include-directories"></a>/I (další adresáře souborů k zahrnutí)

Adresář se přidá do seznamu adresářů hledat vkládané soubory.

## <a name="syntax"></a>Syntaxe

```
/I[ ]directory
```

## <a name="arguments"></a>Arguments

*Adresář*<br/>
Adresář, který má být přidán do seznamu adresáře hledat vkládané soubory.

## <a name="remarks"></a>Poznámky

Chcete-li přidat více než jeden adresář, použijte tuto možnost více než jednou. Jsou prohledány adresáře pouze do určeného zahrnutého souboru se nenašel.

Tuto možnost můžete použít s Ignore Standard Include Paths ([/X (Ignore Standard Include Paths)](../../build/reference/x-ignore-standard-include-paths.md)) možnost.

Kompilátor vyhledá adresářů v následujícím pořadí:

1. Adresáře obsahujícího zdrojový soubor.

1. Adresářů zadaných spolu s **/I** možnost v pořadí, aktivovanými CL.

1. Adresáře určené v **zahrnout** proměnné prostředí.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **další adresáře souborů k zahrnutí** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Příklad

Následující příkaz hledá soubory k zahrnutí požadoval MAIN.c v následujícím pořadí: první v adresáři obsahující MAIN.c, pak v adresář \INCLUDE a potom v adresáři \MY\INCLUDE a nakonec v adresářích přiřazené k zahrnutí proměnné prostředí.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)