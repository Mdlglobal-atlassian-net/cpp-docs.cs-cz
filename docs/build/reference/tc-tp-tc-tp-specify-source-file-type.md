---
title: /Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)
ms.date: 1/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: e435b48359a708408ff8659e53c9e7c4f7e80261
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619112"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)

**/Tc** možnost určuje, že je její argument souboru filename zdrojový soubor jazyka C i v případě, že nemá příponu .c. **/Tp** možnost určuje, že její parametr filename je zdrojový soubor jazyka C++ i v případě, že nemá příponu .cpp nebo .cxx. Mezera mezi možností a název souboru je volitelný. Jednotlivé možnosti určuje jeden soubor. Chcete-li určit další soubory, opakujte možnost.

**/TC** a **/TP** globální variant **/Tc** a **/Tp**. Určí pro kompilátor, aby považoval všechny soubory s názvem v příkazovém řádku jako zdrojové soubory jazyka C (**/TC**) nebo zdrojové soubory C++ (**/TP**), bez ohledu na umístění na příkazovém řádku ve vztahu k možnost. Tyto globální možnosti můžete přepsat na jeden soubor prostřednictvím **/Tc** nebo **/Tp**.

## <a name="syntax"></a>Syntaxe

> **/TC** _filename_
>  **/Tp** _filename_
>  **/TC** 
>  **/TP**

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Zdrojový soubor jazyka C nebo C++.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **CL** předpokládá, že jsou soubory s příponou .c zdrojových souborech jazyka C a C++ zdrojové soubory jsou soubory .cpp nebo .cxx rozšíření.

Při buď **TC** nebo **Tc** je zadána možnost, všechny specifikace [/Zc: wchar_t (wchar_t je nativní typ)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) možnost je ignorována.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit** stránku vlastností.

1. Upravit **zkompilovat jako** vlastnost. Zvolte **OK** nebo **použít** změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Příklady

Cl – příkazový řádek určuje, že MAIN.c TEST.prg a COLLATE.prg jsou všechny zdrojové soubory jazyka C. CL nerozpozná PRINT.prg.

> HLAVNÍ CL. C /TcTEST.PRG /TcCOLLATE.PRG tisk. PRG

Cl – příkazový řádek určuje, že TEST1.c, TEST2.cxx, TEST3.huh a TEST4.o jsou kompilovány jako soubory C++ a TEST5.z je zkompilován jako soubor C.

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
