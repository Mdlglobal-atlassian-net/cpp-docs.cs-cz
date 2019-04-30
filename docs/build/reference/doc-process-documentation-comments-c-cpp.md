---
title: /doc (zpracování dokumentačních komentářů) (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
ms.openlocfilehash: 90f63a972245114424b64d4131420dcb4e1e925a
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342914"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (zpracování dokumentačních komentářů) (C/C++)

V souborech zdrojového kódu a chcete vytvořit soubor .xdc pro každý soubor zdrojového kódu, který se dokumentační komentáře způsobí, že kompilátor zpracování dokumentačních komentářů.

## <a name="syntax"></a>Syntaxe

> **/ doc**[*název*]

## <a name="arguments"></a>Arguments

*name*<br/>
Název, který kompilátor vytvoří soubor .xdc. Platné jen v případě jeden soubor .cpp se předává v kompilace.

## <a name="remarks"></a>Poznámky

Zpracování souborů .xdc do souboru XML s xdcmake.exe. Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](xdcmake-reference.md).

Můžete přidat komentáře dokumentace do souborů se zdrojovým kódem. Další informace najdete v tématu [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments-visual-cpp.md).

Použít soubor .xml generovaný s podporou technologie IntelliSense, ujistěte se, název souboru souboru .xml, který je stejný jako sestavení, které chcete podporovat a vložit ho do XML je ve stejném adresáři jako sestavení. Při sestavení se odkazuje v projektu sady Visual Studio, je také najít soubor .xml. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense) a [zadávání komentářů ke kódu XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **výstupní soubory** stránku vlastností.

1. Upravit **Generovat soubory dokumentace XML** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
