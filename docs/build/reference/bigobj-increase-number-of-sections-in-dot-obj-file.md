---
title: "-bigobj (zvýšit počet oddílů v. Soubor obj) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /bigobj
dev_langs:
- C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 178206536522630616bfae0506bfa3edec98068c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zvýšit počet oddílů v souboru .Obj)
**/ bigobj** zvyšuje počet oddíly, které může obsahovat soubor objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/bigobj  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, soubor objekt může obsahovat až 65 536 (2 ^ 16) adresovatelné oddíly. Toto je případ, bez ohledu na to, která je zadána cílová platforma. **/ bigobj** zvyšuje tuto adresu kapacitu do 4 294 967 296 (2 ^ 32).  
  
 Většina moduly nikdy vygeneruje soubor .obj, který obsahuje více než 65 536 části. Ale počítač generovaného kódu nebo kód, který výrazně využívá knihovny šablon můžou vyžadovat .obj soubory, které mohou být uloženy další části. **/ bigobj** je povolit ve výchozím nastavení v projektech univerzální platformu Windows (UWP), protože tento kód XAML generované počítač obsahuje velký počet hlaviček. Pokud tuto možnost na projekt aplikace UPW zakážete budete pravděpodobně dojde k chybě kompilátoru C1128.  
  
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