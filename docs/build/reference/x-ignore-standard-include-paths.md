---
title: /X (ignorování standardních cest zahrnutí)
ms.date: 11/04/2016
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: dba7e49880307002a3dee983264e93666adfef17
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818398"
---
# <a name="x-ignore-standard-include-paths"></a>/X (ignorování standardních cest zahrnutí)

Zabraňuje kompilátor hledal soubory k zahrnutí v adresářích zadaných v proměnné prostředí PATH či INCLUDE.

## <a name="syntax"></a>Syntaxe

```
/X
```

## <a name="remarks"></a>Poznámky

Můžete použít tuto možnost [/I (další vložené adresáře)](i-additional-include-directories.md) (**/I**`directory`) možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **preprocesor** stránku vlastností.

1. Upravit **Ignorovat standardní cestu zahrnují** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Příklad

V následujícím příkazu `/X` instruuje kompilátor, aby ignorovat umístění zadaná pomocí proměnné prostředí PATH či INCLUDE a `/I` Určuje adresář, do kterého se mají hledat vkládané soubory:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
