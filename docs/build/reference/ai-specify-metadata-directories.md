---
title: -AI (zadat adresáře metadat) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
dev_langs:
- C++
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bde5c93c8a211bb0fc66028932a0a7d50415236d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ai-specify-metadata-directories"></a>/AI (Zadat adresáře metadat)
Určuje adresář, který bude kompilátor hledat řešení předaný odkazů na soubor `#using` – direktiva.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/AIdirectory  
```  
  
## <a name="arguments"></a>Arguments  
 `directory`  
 Adresář nebo cesta, které má kompilátor prohledat.  
  
## <a name="remarks"></a>Poznámky  
 Pouze jednomu adresáři se dá předat do **/AI** volání. Zadejte jednu **/AI** možnost pro každou z cest chcete kompilátoru pro vyhledávání. Například přidat cestu pro hledání kompilátoru C:\Project\Meta i C:\Common\Meta `#using` Přidání direktivy, `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` na příkazový řádek kompilátoru nebo přidat každý adresář k **další #using adresáře** Vlastnost v sadě Visual Studio.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V navigačním podokně vyberte **vlastnosti konfigurace**, **C/C++**, **Obecné**.  
  
3.  Změnit **další #using adresáře** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [#using – direktiva](../../preprocessor/hash-using-directive-cpp.md)