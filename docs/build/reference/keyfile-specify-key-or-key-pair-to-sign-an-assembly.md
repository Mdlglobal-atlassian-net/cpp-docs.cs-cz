---
title: -KEYFILE (zadat klíč nebo pár klíčů pro podepsání sestavení) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
dev_langs:
- C++
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 476fd1e49a8c93363f00215d422a79eda808c321
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Zadat klíč nebo pár klíčů pro podepsání sestavení)
```  
/KEYFILE:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Soubor, který obsahuje klíč. Umístěte řetězec v uvozovkách ("") Pokud obsahuje mezeru.  
  
## <a name="remarks"></a>Poznámky  
 Linkeru vloží veřejný klíč do manifestu a následně podepíše konečné sestavení s privátním klíčem. Chcete-li vygenerovat soubor klíče, zadejte [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* na příkazovém řádku. Podepsané sestavení říká, že je mít silný název.  
  
 Pokud je kompilovat s [/LN](../../build/reference/ln-create-msil-module.md), název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení obsahující explicitní odkaz na modul, prostřednictvím [#using](../../preprocessor/hash-using-directive-cpp.md), nebo při propojování s [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).  
  
 Vaše informace šifrování můžete předat také linkeru s [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md). Použití [/delaysign](../../build/reference/delaysign-partially-sign-an-assembly.md) Pokud chcete, aby částečně podepsané sestavení. V tématu [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) Další informace o podepisování sestavení.  
  
 V případě obě **/keyfile** a **/keycontainer** jsou zadány (pomocí parametru příkazového řádku nebo ve vlastních atributů), linkeru se nejdřív pokusí použít kontejner klíčů. Pokud tato operace úspěšná, je podepsaný sestavení s informacemi v kontejneru klíčů. Pokud linkeru nenajde kontejner klíčů, pokusí se/keyfile zadaný soubor. Pokud tato operace úspěšná, sestavení je podepsaná pomocí informací v souboru klíče a informace o klíči budou nainstalováni v kontejneru klíčů (podobné sn -i), aby na další kompilace kontejner klíče budou platné.  
  
 Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.  
  
 V tématu [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) Další informace o podepisování sestavení.  
  
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