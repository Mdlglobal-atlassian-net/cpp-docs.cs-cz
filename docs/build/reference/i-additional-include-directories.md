---
title: /I (Další adresáře souborů k zahrnutí)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 0dc1769924880d8cb1b5dc173dd614e87584cac9
ms.sourcegitcommit: 45835842604602a011813d0cd70abc5df91b89ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750389"
---
# <a name="i-additional-include-directories"></a>/I (Další adresáře souborů k zahrnutí)

Adresář se přidá do seznamu adresářů hledat vkládané soubory.

## <a name="syntax"></a>Syntaxe

> **/I**[] č.*adresáře*

### <a name="arguments"></a>Arguments

*Adresář*<br/>
Adresář, který má být přidán do seznamu adresáře hledat vkládané soubory.

## <a name="remarks"></a>Poznámky

Chcete-li přidat více než jeden adresář, použijte tuto možnost více než jednou. Jsou prohledány adresáře pouze do určeného zahrnutého souboru se nenašel.

Můžete použít tuto možnost ([/X (Ignore Standard Include Paths)](../../build/reference/x-ignore-standard-include-paths.md)) možnost.

Kompilátor vyhledá adresářů v následujícím pořadí:

1. Pokud je určen pomocí [#include – direktiva](../../preprocessor/hash-include-directive-c-cpp.md) v podobě dvojitých uvozovek, nejprve hledá místní adresáře. Hledání začne ve stejném adresáři jako soubor, který obsahuje **#include** příkazu. Pokud se to nepodaří najít soubor, hledá v aktuálně otevřenou adresářů zahrňte soubory v obráceném pořadí, v jakém byly otevřeny. Hledání začne v adresáři nadřazeného souboru zahrnutí a pokračuje směrem nahoru přes adresáře všech nadřazených soubory k zahrnutí.

1. Pokud zadaný pomocí **#include** – direktiva v úhel párování formuláře nebo v případě neúspěchu vyhledávání místní adresář, hledání adresářů určené vlastností **/I** možnost v pořadí, CL aktivovanými na příkazovém řádku.

1. Adresáře určené v **zahrnout** proměnné prostředí.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. Upravit **další adresáře souborů k zahrnutí** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Příklad

Následující příkaz hledá soubory k zahrnutí požadoval MAIN.c v následujícím pořadí: nejprve, pokud zadaný pomocí dvojité uvozovky, místní soubory budou prohledány. V dalším kroku vyhledávání bude pokračovat v adresář \INCLUDE a potom v adresáři \MY\INCLUDE a nakonec v adresářích přiřazená k proměnné prostředí INCLUDE.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)