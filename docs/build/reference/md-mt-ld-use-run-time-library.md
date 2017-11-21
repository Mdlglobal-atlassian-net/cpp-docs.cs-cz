---
title: "-MD,. -MT, -LD (použít běhovou knihovnu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
dev_langs: C++
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb4405c893552f38e613b9cb23ae0335c1a914c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (Použít běhovou knihovnu)
Označuje, zda je vícevláknový modul knihovnou DLL, a určuje prodejní nebo ladicí verze knihovny runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/MD[d]  
/MT[d]  
/LD[d]  
```  
  
## <a name="remarks"></a>Poznámky  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/MD**|Způsobí, že aplikace použije verzi knihovny runtime, která je vícevláknová a specifická pro knihovnu DLL. Definuje `_MT` a `_DLL` a způsobí, že kompilátor název knihovny MSVCRT.lib umístěte do souboru .obj.<br /><br /> Aplikace kompilované s tímto parametrem jsou staticky propojeny se souborem MSVCRT.lib. Tato knihovna poskytuje vrstvu kódu, která linkeru umožňuje překládat externí odkazy. Skutečné pracovní kódu je součástí MSVCR*cisloverze*. Knihovny DLL, které musí být k dispozici v době běhu aplikací propojená s MSVCRT.lib.|  
|**/ MDd**|Definuje `_DEBUG`, `_MT`, a `_DLL` a způsobí, že aplikace pro používání ladění vícevláknový specifické a knihovny DLL verze běhové knihovny. Navíc způsobí, že kompilátor umístí knihovnu s názvem MSVCRTD.lib do souboru .obj.|  
|**/ MT**|Způsobí, že aplikace použije vícevláknovou statickou verzi knihovny runtime. Definuje `_MT` a způsobí, že kompilátor umístěte název knihovny LIBCMT.lib do souboru .obj tak, aby linkeru použije LIBCMT.lib přeložit externí symboly.|  
|**/ MTd**|Definuje `_DEBUG` a `_MT`. Tento parametr navíc způsobí, že kompilátor umístí knihovnu s názvem LIBCMTD.lib do souboru .obj, aby linker použil k překladu externích symbolů soubor LIBCMTD.lib.|  
|**/LD**|Vytvoří knihovnu DLL.<br /><br /> Předává **/dll** možnosti linkeru. Linkeru hledá, ale nevyžaduje, `DllMain` funkce. Pokud jste Nezapisovat `DllMain` vloží linkeru funkce, `DllMain` funkce, která vrátí hodnotu TRUE.<br /><br /> Propojí spouštěcí kód knihovny DLL.<br /><br /> Vytvoří knihovnu importu (.lib), není-li na příkazovém řádku zadán soubor exportu (.exp). Knihovnu importu propojíte s aplikacemi, které volají vaši knihovnu DLL.<br /><br /> Interpretuje [/Fe (název souboru EXE)](../../build/reference/fe-name-exe-file.md) jako pojmenování knihovny DLL, nikoli soubor .exe. Ve výchozím nastavení, stane se název programu *basename*.dll místo *basename*.exe.<br /><br /> Znamená **/MT** explicitně nezadáte **/MD**.|  
|**/ LDd**|Vytvoří ladicí knihovnu DLL. Definuje `_MT` a `_DEBUG`.|  
  
 Další informace o běhové knihovny jazyka C a které knihovny se používají při kompilaci s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), najdete v části [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).  
  
 Všechny moduly předaný dané vyvolání linkeru musí být zkompilován s stejná knihovna RTL – možnost kompilátoru (**/MD**, **/MT**, **/LD**).  
  
 Další informace o tom, jak používat ladicí verze běhové knihovny najdete v tématu [referenční dokumentace knihoven C Run-Time](../../c-runtime-library/c-run-time-library-reference.md).  
  
 Výběr příslušné knihovny runtime jazyka C popisuje také článek Q140584 znalostní báze Knowledge Base.  
  
 Další informace o rozhraní DLLs najdete v tématu [knihovny DLL v jazyce Visual C++](../../build/dlls-in-visual-cpp.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **C/C++** složky.  
  
3.  Vyberte **generování kódu** stránku vlastností.  
  
4.  Změnit **Runtime Library** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)