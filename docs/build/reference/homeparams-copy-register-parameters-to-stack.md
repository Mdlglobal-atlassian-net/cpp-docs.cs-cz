---
title: "-homeparams (Kopírovat parametry registru do zásobníku) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fff1b206620ef9efee3fc22c83c8d5317e99b607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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