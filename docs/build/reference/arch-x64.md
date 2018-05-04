---
title: -arch (x64) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 848d229d6cf8df7d08494d0c300e082c6dc7d0a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="arch-x64"></a>/arch (x64)
Určuje architekturu pro generování kódu na x64. Viz také [/arch (x86)](../../build/reference/arch-x86.md) a [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/arch:[AVX|AVX2]  
```  
  
## <a name="arguments"></a>Arguments  
 **/arch:AVX**  
 Umožňuje použití Intel Advanced Vector rozšíření pokyny.  
  
 **/arch:AVX2**  
 Umožňuje použití Intel Advanced Vector Extensions 2 pokyny.  
  
## <a name="remarks"></a>Poznámky  
 **/ arch** jen ovlivňuje generování pro nativní funkce kódu. Při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) zkompilovat, **/arch** nemá žádný vliv na generování kódu pro spravovaný funkce.  
  
 `__AVX__` – Symbol preprocesoru je definován při **/arch:AVX** – možnost kompilátoru je zadán. `__AVX2__` – Symbol preprocesoru je definován při **/arch:AVX2** – možnost kompilátoru je zadán. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** možnost byla zavedena v sadě Visual Studio 2013 Update 2, verze 12.0.34567.1.  
  
### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru /arch:AVX nebo /arch:AVX2 v sadě Visual Studio  
  
1.  Otevřete **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++** složky.  
  
3.  Vyberte **generování kódu** stránku vlastností.  
  
4.  V **povolit rozšířené instrukce nastavit** rozevíracího seznamu vyberte **Advanced rozšíření vektoru (nebo architektura: AVX)** nebo **Advanced Vector Extensions 2 (nebo architektura: AVX2)**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/ arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)