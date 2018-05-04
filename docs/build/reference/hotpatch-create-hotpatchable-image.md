---
title: -hotpatch (vytvořit bitovou kopii opravitelnou za provozu) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb0f27c8da03104ee3633d9ea1a5f1232407931e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Vytvořit bitovou kopii s možností provádění oprav za běhu)
Připraví bitovou kopii této technologie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/hotpatch  
```  
  
## <a name="remarks"></a>Poznámky  
 Když **/hotpatch** se používá v kompilaci, kompilátor zajišťuje, že první instrukce jednotlivé funkce alespoň dva bajty, což je vyžadováno pro této technologie.  
  
 K dokončení přípravy provádění bitovou kopii opravitelnou za provozu, když použijete **/hotpatch** zkompilovat, je nutné použít [/FUNCTIONPADMIN (vytvořit kopii opravitelnou za provozu)](../../build/reference/functionpadmin-create-hotpatchable-image.md) propojení. Při kompilování a propojit bitovou kopii pomocí jednoho volání cl.exe, **/hotpatch** znamená **/functionpadmin**.  
  
 Protože pokyny jsou vždy dva bajty nebo větší v architektuře ARM a protože x64 kompilace vždy považuje jako **/hotpatch** byl zadán, nemusíte určit **/hotpatch** při Při kompilaci pro tyto cíle; Nicméně je nutné stále propojit pomocí **/functionpadmin** k vytvoření bitové kopie opravitelnou za provozu pro ně. **/Hotpatch** kompilátoru možnost jenom ovlivňuje x86 kompilace.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Přidat možnost kompilátoru **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="guidance"></a>Doprovodné materiály  
 Další informace o správě aktualizací najdete v tématu "Zabezpečení pokyny pro aktualizaci Správa" na [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)