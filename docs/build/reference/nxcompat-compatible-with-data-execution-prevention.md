---
title: "-NXCOMPAT (kompatibilní s předcházením spuštění dat) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /NXCOMPAT
dev_langs: C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.assetid: 5858e7ff-24d3-4ac3-9046-af2c9e220d9b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d97b1b84ef6894e4ec161dbcecef47f6b676af23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (kompatibilní s předcházením spuštění dat)
Označuje, že spustitelný soubor testoval být kompatibilní s funkcí Zabránění spuštění dat systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/NXCOMPAT[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení **/NXCOMPAT** zapnutý.  
  
 **/NXCOMPAT:No** lze použít jako kompatibilní s předcházením spuštění dat explicitně zadat spustitelný soubor.  
  
 Další informace o zabránění spuštění dat najdete v těchto článcích:  
  
-   [Podrobný popis funkce Zabránění spuštění dat (DEP)](http://go.microsoft.com/fwlink/?LinkID=157771) na webu Microsoft Help a podpora  
  
-   [Zabránění spuštění dat](http://go.microsoft.com/fwlink/?LinkID=157770) na webu MSDN  
  
-   [Zabránění spuštění dat (Windows Embedded)](http://go.microsoft.com/fwlink/?LinkID=157768) na webu MSDN  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost v **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)