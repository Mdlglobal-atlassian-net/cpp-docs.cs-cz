---
title: "-doc (zpracování dokumentačních komentářů) (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8737c0e33d33fe062d9a07f18d9005e58463f5b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (zpracování dokumentačních komentářů) (C/C++)
V soubory zdrojového kódu a vytvořte projektový soubor pro každou souboru zdrojového kódu, který má dokumentační komentáře způsobí, že kompilátor zpracování dokumentačních komentářů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/doc[name]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`  
 Název projektový soubor, který bude vytvořen. Platí pouze, pokud jeden souboru, je předaná kompilace.  
  
## <a name="remarks"></a>Poznámky  
 Do souboru .xml s xdcmake.exe se zpracovávají soubory. Další informace najdete v tématu [referenční dokumentace nástroje XDCMake](../../ide/xdcmake-reference.md).  
  
 Dokumentační komentáře můžete přidat na zdrojové soubory vašeho kódu. Další informace najdete v tématu [doporučené značky pro dokumentační komentáře](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).  
  
 Pokud chcete použít soubor .xml vygenerované pomocí IntelliSense, ujistěte se, název souboru soubor .xml, který je stejný jako sestavení, které chcete podporovat a umístit soubor .xml je ve stejném adresáři jako sestavení. Při odkazování na sestavení v projektu sady Visual Studio, je také najít soubor .xml. Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense) a [zadávání komentářů ke kódu XML](/visualstudio/ide/supplying-xml-code-comments).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **C/C++** uzlu.  
  
4.  Vyberte **výstupní soubory** stránku vlastností.  
  
5.  Změnit **generování souborů dokumentace XML** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)