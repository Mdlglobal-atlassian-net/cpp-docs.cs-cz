---
title: -ALLOWBIND (zabránit vazbě knihoven DLL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31968e27c46cb5ea220a4cfe19c36820c4cf8444
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zabránit vazbě knihoven DLL)
```  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 /ALLOWBIND:No nastaví trochu v záhlaví knihovny DLL, která určuje Bind.exe, že bitovou kopii nesmí být vázána. Je možné, knihovny DLL vázat, pokud byly digitálně podepsané (vazba zruší platnost podpisu).  
  
 Můžete upravit existující knihovny DLL pro funkci /ALLOWBIND s [/ALLOWBIND](../../build/reference/allowbind.md) – možnost nástroje EDITBIN nástroje.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte položku **vlastnosti konfigurace**, **Linkeru**a vyberte **příkazového řádku**.  
  
3.  Zadejte `/ALLOWBIND:NO` do **další možnosti**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [BindImage – funkce](http://msdn.microsoft.com/library/windows/desktop/ms679278.aspx)   
 [BindImageEx – funkce](http://msdn.microsoft.com/library/windows/desktop/ms679279.aspx)