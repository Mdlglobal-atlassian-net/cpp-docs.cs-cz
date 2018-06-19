---
title: -KEYCONTAINER (zadat kontejner klíčů pro podepsání sestavení) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs:
- C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13058978b0833a17abbbfb68a2ed753aacfb6d49
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377884"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Zadat kontejner klíčů pro podpis sestavení)
```  
/KEYCONTAINER:name  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 *Jméno*  
 Kontejner, který obsahuje klíč. Umístěte řetězec v uvozovkách ("") Pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Linkeru vytvoří podepsané sestavení vložením veřejný klíč do manifestu a podepíše konečné sestavení s privátním klíčem. Chcete-li vygenerovat soubor klíče, zadejte [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* na příkazovém řádku. **sn -i** nainstaluje pár klíčů do kontejneru.  
  
 Pokud je kompilovat s [/LN](../../build/reference/ln-create-msil-module.md), název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení obsahující explicitní odkaz na modul, prostřednictvím [#using](../../preprocessor/hash-using-directive-cpp.md), nebo při propojování s [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 Vaše informace šifrování můžete předat také kompilátoru s [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Použití [/delaysign](../../build/reference/delaysign-partially-sign-an-assembly.md) Pokud chcete, aby částečně podepsané sestavení. V tématu [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Další informace o podepisování sestavení.  
  
 Další možnosti linkeru, které mají vliv vytváření sestavení jsou:  
  
-   [/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)