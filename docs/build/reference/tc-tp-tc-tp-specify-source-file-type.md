---
title: "-Tc, - Tp,-TC, - TP (zadání typu zdrojového souboru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
dev_langs: C++
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.assetid: 7d9d0a65-338b-427c-8b48-fff30e2f9d2b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3b7508bf3ff65e27cab3260577d2831de00eb2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)
**/Tc** možnost určuje, že `filename` je C zdrojového souboru, i když nemá .c rozšíření. **/Tp** možnost určuje, že `filename` je zdrojového souboru C++, i když nemá příponu sada nebo .cxx. Mezery mezi parametrem a `filename` je volitelný. Každá možnost určuje jeden soubor. Chcete-li zadat další soubory, opakujte možnost.  
  
 **/TC** a **/TP** globální variant **/Tc** a **/Tp**. Určí pro kompilátor považovat všechny soubory s názvem na příkazovém řádku jako zdrojové soubory C (**/TC**) nebo zdrojové soubory C++ (**/TP**), bez ohledu na umístění na příkazovém řádku ve vztahu k možnost. Tyto globální možnosti je možné přepsat na jeden soubor prostřednictvím **/Tc** nebo **/Tp**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Tcfilename  
/Tpfilename  
/TC  
/TP  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 C nebo C++ zdrojového souboru.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení CL předpokládá, že jsou soubory s příponou .c zdrojové soubory C a C++ zdrojové soubory jsou soubory s sada nebo .cxx rozšíření.  
  
 Při buď **TC** nebo **Tc** je zadána možnost, všechny specifikaci [/Zc: wchar_t (wchar_t je nativní typ)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) možnost je ignorována.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **Upřesnit** stránku vlastností.  
  
4.  Změnit **zkompilovat jako** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.  
  
## <a name="examples"></a>Příklady  
 Následující příkazový řádek CL Určuje, že MAIN.c, TEST.prg a COLLATE.prg jsou všechny zdrojové soubory C. CL nerozpozná PRINT.prg.  
  
```  
CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG  
```  
  
 Následující příkazový řádek CL Určuje, že TEST1.c, TEST2.cxx, TEST3.huh a TEST4.o zjišťují jako soubory C++ a kompiluje TEST5.z jako soubor C.  
  
```  
CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)