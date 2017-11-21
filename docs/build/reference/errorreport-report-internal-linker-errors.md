---
title: "-ERRORREPORT (sestava interními chybami Linkeru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs: C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6242457bb4da3e19700f5018b2a484bfa05630b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (sestava s interními chybami linkeru)
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="remarks"></a>Poznámky  
 Umožňuje zadat informace o chybě (LED) interní kompilátoru přímo společnosti Microsoft.  
  
 Možnost **/errorReport:send** pokusí automaticky odesílat informace o chybách společnosti Microsoft, ale úspěch závisí na nastavení registru. Další informace o tom, jak nastavit na odpovídající hodnoty v registru najdete v tématu [jak zapnout automatické hlášení chyb v příkazového řádku nástroje sady Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695) na webu MSDN.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **vlastnosti konfigurace** složky.  
  
3.  Klikněte **Linkeru** složky.  
  
4.  Klikněte **Upřesnit** stránku vlastností.  
  
5.  Změnit **zasílání zpráv o chybách**vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/ errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md)   
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)