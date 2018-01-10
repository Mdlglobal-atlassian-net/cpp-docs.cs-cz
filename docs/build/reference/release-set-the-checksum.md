---
title: "-RELEASE (nastavení kontrolního součtu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
dev_langs: C++
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b961c55f04b4f830de30c3d886d9aaee9ef71ea2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="release-set-the-checksum"></a>/RELEASE (nastavení kontrolního součtu)
```  
/RELEASE  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost/Release nastaví kontrolního součtu v hlavičce souboru s příponou .exe.  
  
 Operační systém vyžaduje kontrolního součtu pro ovladače zařízení. Nastavení kontrolního součtu pro verze ovladače zařízení pro zajištění kompatibility s budoucí operační systémy.  
  
 / Release možnost je ve výchozím nastavení při [/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) je zadána možnost.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **nastavení kontrolního součtu** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)