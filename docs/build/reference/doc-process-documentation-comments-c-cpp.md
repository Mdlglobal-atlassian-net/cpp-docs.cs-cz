---
title: -doc (zpracování dokumentačních komentářů) (C/C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee09b3fe61c86015d8dc7464ef9925419fc745d9
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100324"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (zpracování dokumentačních komentářů) (C/C++)
V souborech zdrojového kódu a chcete vytvořit soubor .xdc pro každý soubor zdrojového kódu, který se dokumentační komentáře způsobí, že kompilátor zpracování dokumentačních komentářů.

## <a name="syntax"></a>Syntaxe

> **/ doc**[*název*]

## <a name="arguments"></a>Arguments

*Jméno*<br/>
Název, který kompilátor vytvoří soubor .xdc. Platné jen v případě jeden soubor .cpp se předává v kompilace.

## <a name="remarks"></a>Poznámky

Zpracování souborů .xdc do souboru XML s xdcmake.exe. Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](../../ide/xdcmake-reference.md).

Můžete přidat komentáře dokumentace do souborů se zdrojovým kódem. Další informace najdete v tématu [doporučené značky pro dokumentační komentáře](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).

Použít soubor .xml generovaný s podporou technologie IntelliSense, ujistěte se, název souboru souboru .xml, který je stejný jako sestavení, které chcete podporovat a vložit ho do XML je ve stejném adresáři jako sestavení. Při sestavení se odkazuje v projektu sady Visual Studio, je také najít soubor .xml. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense) a [zadávání komentářů ke kódu XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **výstupní soubory** stránku vlastností.

1. Upravit **Generovat soubory dokumentace XML** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)