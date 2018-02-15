---
title: "-CLRIMAGETYPE (zadat typ obrázku CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8de8abb1602499cea0b1412d4199ea54b3bf601
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Zadat typ obrázku CLR)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>Poznámky  
 Linkeru přijme nativních objektů a také MSIL objekty, které jsou kompilovaná pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru byly zastaralé v sadě Visual Studio 2015. Při předávání smíšený objektů ve stejném sestavení, je, ověřitelnosti výsledné výstupního souboru, ve výchozím nastavení rovna nejnižší úroveň ověřitelnosti vstupní modulů. Například pokud předáte nativní image a image ve smíšeném režimu (zkompilovat pomocí **/CLR**), bude výsledný obraz bitové kopie ve smíšeném režimu.  
  
 /CLRIMAGETYPE slouží k určení s nižší úrovní ověřitelnosti, pokud je to, co potřebujete.  
  
 Informace o tom, jak určit typ obrázku CLR souboru najdete v tématu [/CLRHEADER](../../build/reference/clrheader.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **Upřesnit** stránku vlastností.  
  
5.  Změnit **typ obrázku CLR** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)