---
title: "/ Tc, /Tp /TC, /TP (zadání typu zdrojového souboru) | Microsoft Docs"
ms.date: 1/11/2018
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3d51e4c6bbf6a77f86be5cabde9b65f8e4f8c9f
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)

**/Tc** možnost určuje, že její parametr filename je C zdrojového souboru, i v případě, že nemá příponu .c. **/Tp** možnost určuje, že její název souboru by se zdrojového souboru C++, i v případě, že nemá příponu sada nebo .cxx. Mezery mezi parametrem a název souboru je volitelný. Každá možnost určuje jeden soubor. Chcete-li zadat další soubory, opakujte možnost.

**/TC** a **/TP** globální variant **/Tc** a **/Tp**. Určí pro kompilátor považovat všechny soubory s názvem na příkazovém řádku jako zdrojové soubory C (**/TC**) nebo zdrojové soubory C++ (**/TP**), bez ohledu na umístění na příkazovém řádku ve vztahu k možnost. Tyto globální možnosti je možné přepsat na jeden soubor prostřednictvím **/Tc** nebo **/Tp**.

## <a name="syntax"></a>Syntaxe

> **/Tc** _filename_  
> **/Tp** _filename_  
> **/TC**  
> **/TP**  

## <a name="arguments"></a>Arguments

*filename*  
C nebo C++ zdrojového souboru.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **CL** předpokládá, že jsou soubory s příponou .c zdrojové soubory C a C++ zdrojové soubory jsou soubory s sada nebo .cxx rozšíření.

Při buď **TC** nebo **Tc** je zadána možnost, všechny specifikaci [/Zc: wchar_t (wchar_t je nativní typ)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) možnost je ignorována.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit** stránku vlastností.

1. Změnit **zkompilovat jako** vlastnost. Zvolte **OK** nebo **použít** proveďte změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Příklady

Tento příkaz CL Určuje, že MAIN.c, TEST.prg a COLLATE.prg jsou všechny zdrojové soubory C. CL nerozpozná PRINT.prg.

> CL HLAVNÍ. C /TcTEST.PRG /TcCOLLATE.PRG tisku. PRG

Tento příkaz CL Určuje, že TEST1.c, TEST2.cxx, TEST3.huh a TEST4.o zjišťují jako soubory C++ a kompiluje TEST5.z jako soubor C.

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
