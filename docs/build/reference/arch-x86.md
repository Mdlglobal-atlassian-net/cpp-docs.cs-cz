---
title: -arch (x86) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87e1826e324f8e544a791520a3ac035f5ab07100
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="arch-x86"></a>/arch (x86)
Určuje architekturu pro generování kódu na x86. Viz také [/arch (x64)](../../build/reference/arch-x64.md) a [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## <a name="arguments"></a>Arguments  
 **/arch:IA32**  
 Určuje žádné rozšířené pokyny a také určuje x87 pro výpočty s plovoucí desetinnou čárkou.  
  
 **/arch:SSE**  
 Umožňuje použití SSE pokyny.  
  
 **/arch:SSE2**  
 Umožňuje použití SSE2 pokyny. Toto je výchozí pokyn na x86 platformy, pokud žádné **/arch** je zadána možnost.  
  
 **/arch:AVX**  
 Umožňuje použití Intel Advanced Vector rozšíření pokyny.  
  
 **/arch:AVX2**  
 Umožňuje použití Intel Advanced Vector Extensions 2 pokyny.  
  
## <a name="remarks"></a>Poznámky  
 Pokyny SSE a SSE2 existují na různé procesory Intel a AMD. Podle pokynů AVX existují na procesory Intel Sandy most a AMD Bulldozer procesory. AVX2 pokyny jsou podporovány Intel Haswell a Broadwell procesory a na základě AMD rýpadla procesory.  
  
 `_M_IX86_FP`, `__AVX__` a `__AVX2__` znamenat makra, která, pokud existuje, **/arch** – možnost kompilátoru byl použit. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** možnost a `__AVX2__` makro byly zavedeny v sadě Visual Studio 2013 Update 2, verze 12.0.34567.1.  
  
 Pro optimalizaci rozhodne, kdy a jak postupujte podle pokynů SSE a SSE2 při **/arch** je zadán. Používá SSE a SSE2 pokyny pro některé skalární s plovoucí desetinnou čárkou výpočty při určování, zda je rychlejší používat SSE/SSE2 pokyny a registrů místo x87 s plovoucí desetinnou čárkou zaregistrujte zásobníku. V důsledku toho kódu může skutečně používáte kombinaci x87 i SSE/SSE2 pro výpočty s plovoucí desetinnou čárkou. Navíc se **/arch:SSE2**, SSE2 pokyny lze použít pro některé operace 64bitové celé číslo.  
  
 Kromě pokynů SSE a SSE2, kompilátor používá také další pokyny, které se nacházejí na revize procesoru, které podporují SSE a SSE2. Příkladem je CMOV pokyn, nejprve se zobrazily v revize Pentium Pro procesory Intel.  
  
 Protože x86 kompilátoru generuje kód této používá SSE2 pokyny ve výchozím nastavení, je nutné zadat **/arch:IA32** zakázat generování SSE a SSE2 pokyny pro x86 procesory.  
  
 **/ arch** jen ovlivňuje generování pro nativní funkce kódu. Při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) zkompilovat, **/arch** nemá žádný vliv na generování kódu pro spravovaný funkce.  
  
 **/ arch** a [/QIfist](../../build/reference/qifist-suppress-ftol.md) nelze použít na stejné kompilace. Konkrétně, pokud nepoužíváte `_controlfp` k úpravě FP řídicího slova a potom běhu spuštění sad x87 FPU řízení word přesnost řízení pole Kód na 53 bitů. Proto každých float a dvojité operace ve výrazu používají mantisy 53 bitů a exponent 15 bitů. Ale každé operace jednoduchou přesností SSE používá mantisy 24bitový a exponentem 8bitové a operace s dvojitou přesností SSE2 používají mantisy 53 bitů a exponentem 11 bitů. Další informace najdete v tématu [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Tyto rozdíly jsou možné v stromu jeden výraz, ale není v případech, kde je zahrnuta přiřazení uživatelských po každém dílčím výrazu. Zvažte následující:  
  
```cpp  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 Porovnání:  
  
```cpp  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Nastavení této možnosti kompilátoru pro AVX AVX2, IA32 SSE nebo SSE2 v sadě Visual Studio  
  
1.  Otevřete **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++** složky.  
  
3.  Vyberte **generování kódu** stránku vlastností.  
  
4.  Změnit **povolit rozšířené instrukce nastavit** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/ arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)