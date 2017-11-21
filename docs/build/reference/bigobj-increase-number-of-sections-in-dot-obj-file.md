---
title: "-bigobj (zvýšit počet oddílů v. Soubor obj) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /bigobj
dev_langs: C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 73e6da121b099bdf6e67cdffe4d7d2bd0892d32a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zvýšit počet oddílů v souboru .Obj)
**/ bigobj** zvyšuje počet oddíly, které může obsahovat soubor objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/bigobj  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, soubor objekt může obsahovat až 65 536 (2 ^ 16) adresovatelné oddíly. Toto je případ, bez ohledu na to, která je zadána cílová platforma. **/ bigobj** zvyšuje tuto adresu kapacitu do 4 294 967 296 (2 ^ 32).  
  
 Většina moduly nikdy vygeneruje soubor .obj, který obsahuje více než 65 536 části. Ale počítač generovaného kódu nebo kód, který výrazně využívá knihovny šablon můžou vyžadovat .obj soubory, které mohou být uloženy další části. **/ bigobj** je povolit ve výchozím nastavení na projekty Windows Store, protože tento kód XAML generované počítač obsahuje velký počet hlaviček. Pokud tuto možnost na projekt aplikace Windows Store zakážete budete pravděpodobně dojde k chybě kompilátoru C1128.  
  
 Linkers dodané před Visual C++ 2005 nelze číst soubory .obj, které byly vytvořeny s **/bigobj**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)