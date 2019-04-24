---
title: /AI (Zadat adresáře metadat)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
ms.openlocfilehash: 3633cfe34a4f9c627f84cf401cb559f02f8c8229
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273219"
---
# <a name="ai-specify-metadata-directories"></a>/AI (Zadat adresáře metadat)

Určuje adresář, který kompilátor bude vyhledávání pro přeložení referencí souboru předaných `#using` směrnice.

## <a name="syntax"></a>Syntaxe

> **/AI**_adresáře_

## <a name="arguments"></a>Arguments

*directory*<br/>
Adresář nebo cesta, které má kompilátor prohledat.

## <a name="remarks"></a>Poznámky

Lze předat pouze jeden adresář **/AI** vyvolání. Zadejte jednu **/AI** možnost pro každou cestu, kterou má kompilátor prohledat. Například pro přidání do vyhledávací cesty kompilátoru C:\Project\Meta a C:\Common\Meta `#using` direktivy, přidejte `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` do příkazového řádku kompilátoru nebo přidejte všechny adresáře do **další # adresáře using** Vlastnost v sadě Visual Studio.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. Upravit **další # adresáře using** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[#using – direktiva](../../preprocessor/hash-using-directive-cpp.md)
