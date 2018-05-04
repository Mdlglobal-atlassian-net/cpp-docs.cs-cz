---
title: -POČÍTAČE (určení cílové platformy) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e82cc0fec843dede07f474e1ad5bbdfcc2958f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="machine-specify-target-platform"></a>/MACHINE (určení cílové platformy)
```  
/MACHINE:{ARM|EBC|X64|X86}  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /MACHINE určuje cílovou platformu programu.  
  
 Obvykle není nutné možnost /MACHINE zadávat. Volba LINK odvodí typ počítače ze souborů .obj. Ale v některých případech nelze určit odkaz typu počítačů a problémy [linkerů LNK1113 chyba](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Pokud k takové chybě dojde, zadejte volbu /MACHINE.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **cílový počítač** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)