---
title: /X (ignorování standardních cest zahrnutí)
ms.date: 07/18/2019
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 16f903b98d69472fe1a33b084fe6393ecf9ec001
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341049"
---
# <a name="x-ignore-standard-include-paths"></a>/X (ignorování standardních cest zahrnutí)

Zabraňuje kompilátoru v hledání zahrnutých souborů v adresářích zadaných v cestě a proměnných prostředí INCLUDE.

## <a name="syntax"></a>Syntaxe

```
/X
```

## <a name="remarks"></a>Poznámky

Tuto možnost můžete použít s možností [/i (další adresáře include)](i-additional-include-directories.md) ( **/i**`directory`).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na  stránku vlastností preprocesoru.

1. Upravte vlastnost **umístění Ignore Standard include** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Příklad

V následujícím příkazu `/X` instruuje kompilátor, aby ignoroval umístění zadaná cestou a zahrnovala proměnné prostředí, a `/I` Určuje adresář, ve kterém se mají hledat soubory k zahrnutí:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
