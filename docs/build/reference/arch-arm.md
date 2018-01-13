---
title: -arch (ARM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 468401bcee2d627149175d022c420b8bb905c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="arch-arm"></a>/arch (ARM)
Určuje architekturu pro generování kódu na ARM. Viz také [/arch (x86)](../../build/reference/arch-x86.md) a [/arch (x64)](../../build/reference/arch-x64.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## <a name="arguments"></a>Arguments  
 **/arch:ARMv7VE**  
 Umožňuje použití rozšíření virtualizace ARMv7VE pokyny.  
  
 **/arch:VFPv4**  
 Umožňuje použití pokyny ARM VFPv4. Pokud není tato možnost zadána, VFPv3 je výchozí.  
  
## <a name="remarks"></a>Poznámky  
 `_M_ARM_FP` – Makro (pro pouze ARM) určuje, která, pokud existuje, **/arch** – možnost kompilátoru byl použit. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).  
  
 Při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) zkompilovat, **/arch** nemá žádný vliv na generování kódu pro spravovaný funkce. **/ arch** jen ovlivňuje generování pro nativní funkce kódu.  
  
### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru /arch:ARMv7VE nebo /arch:VFPv4 v sadě Visual Studio  
  
1.  Otevřete **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  V **další možnosti** přidejte `/arch:ARMv7VE` nebo `/arch:VFPv4`.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/ arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)