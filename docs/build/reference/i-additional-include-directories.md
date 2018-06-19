---
title: -I (Další adresáře souborů k zahrnutí) | Microsoft Docs
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
ms.openlocfilehash: 435714d72eeabe74f0cd85509d74dff5d541b019
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373124"
---
# <a name="i-additional-include-directories"></a>/I (další adresáře souborů k zahrnutí)
Přidá do seznamu adresářů hledali zahrnout soubory adresáře.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/I[ ]directory  
```  
  
## <a name="arguments"></a>Arguments  
 `directory`  
 Adresář, který má být přidán do seznamu adresářů hledali zahrnout soubory.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li přidat více než jeden adresář, použijte tuto možnost více než jednou. Adresáře budou prohledávány pouze dokud je najít zadaný soubor.  
  
 Tuto možnost lze použít s Ignorovat standardní cesty zahrnutí ([/X (Ignorovat standardní cesty zahrnutí)](../../build/reference/x-ignore-standard-include-paths.md)) možnost.  
  
 Kompilátor vyhledává adresářů v následujícím pořadí:  
  
1.  Adresáře, který obsahuje zdrojový soubor.  
  
2.  Adresáře zadaným **/I** možnost, v pořadí CL zaznamená je.  
  
3.  Zadaný v adresáře **zahrnout** proměnné prostředí.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Obecné** stránku vlastností.  
  
4.  Změnit **další adresáře Include** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz hledá zahrnout soubory požadoval MAIN.c v následujícím pořadí: první v adresáři obsahující MAIN.c, pak v adresáři \INCLUDE, a potom v adresáři \MY\INCLUDE a nakonec v adresáři přiřazení k zahrnutí proměnné prostředí.  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)