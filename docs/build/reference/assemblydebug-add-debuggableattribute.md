---
title: -ASSEMBLYDEBUG (přidat atribut DebuggableAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
dev_langs:
- C++
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1a6060059609488eb902cbaba4f825663d3475b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372467"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (Přidat atribut DebuggableAttribute)
```  
/ASSEMBLYDEBUG[:DISABLE]  
```  
  
 / ASSEMBLYDEBUG vysílá **atribut DebuggableAttribute** atribut s ladicí informace o sledování a zakáže JIT optimalizace. Toto je stejné jako ve zdroji zadání následující atribut:  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
 Vysílá /ASSEMBLYDEBUG:disable **atribut DebuggableAttribute** atribut ale zakáže sledování informace o ladění a umožňuje JIT optimalizace. Toto je stejné jako ve zdroji zadání následující atribut:  
  
```  
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE  
```  
  
 Ve výchozím nastavení se není emitování **atribut DebuggableAttribute** atribut.  
  
 Atribut DebuggableAttribute lze také přidat k sestavení přímo ve zdrojovém kódu. Například  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
## <a name="remarks"></a>Poznámky  
 Je potřeba explicitně určit, aby spravovaný image debuggable. Pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) samostatně není dostatečná.  
  
 Další možnosti linkeru, které mají vliv vytváření sestavení jsou:  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **ladění** stránku vlastností.  
  
4.  Změnit **Debuggable sestavení** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)