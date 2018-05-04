---
title: -homeparams (Kopírovat parametry registru do zásobníku) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffc9b37ebdcbb380186c7840f5ebd956708a2dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Kopírovat parametry registru do zásobníku)
Vynutí parametry předané zaregistruje k zápisu na jejich umístění v zásobníku při vstupu funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost kompilátoru je pouze pro [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilátory (nativní a multiplatformní kompilace).  
  
 Když jsou parametry předané [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilace, konvence volání vyžadují stackspace parametrů, dokonce i pro parametry předané v registrech. Další informace najdete v tématu [předání parametru](../../build/parameter-passing.md). Však ve výchozím nastavení v sestavení pro vydání, parametry registru budou zapsány do zásobníku, do místa, které už poskytuje pro parametry. Díky tomu je obtížné ladění sestavení optimalizované (verze) vašeho programu.  
  
 Sestavení pro vydání, použijte **/homeparams** zajistit, že při ladění aplikace. **/ homeparams** implikují nevýhodou výkon, protože nevyžaduje cyklus načíst parametry registru do zásobníku.  
  
 V sestavení ladicí verze bude v zásobníku vždy zahrnovat parametry předané v registrech.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)