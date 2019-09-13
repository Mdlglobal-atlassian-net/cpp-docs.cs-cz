---
title: /Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)
ms.date: 01/11/2018
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
ms.openlocfilehash: c93da6d2498d46e4b7bf3ad37dde852bb6bc82a1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927634"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)

Možnost **/TC** určuje, že jeho argument filename je zdrojový soubor jazyka C, a to i v případě, že nemá příponu. C. Parametr **/TP** určuje, že jeho argument filename je C++ zdrojový soubor, a to i v případě, že nemá příponu. cpp nebo. příponu CXX. Mezera mezi možností a názvem souboru je volitelná. Jednotlivé možnosti určují jeden soubor. Chcete-li zadat další soubory, opakujte možnost.

**/TC** a **/TP** jsou globálními variantami **/TC** a **/TP**. Určují kompilátor, aby považoval všechny soubory pojmenované na příkazovém řádku jako zdrojové soubory jazyka C ( **/TC**) nebo C++ zdrojové soubory ( **/TP**), bez ohledu na umístění na příkazovém řádku ve vztahu k možnosti. Tyto globální možnosti lze přepsat v jednom souboru prostřednictvím **/TC** nebo **/TP**.

## <a name="syntax"></a>Syntaxe

> **/TC** _název souboru_ **/TP název_souboru**/TC/TP
>  
> 
> 

## <a name="arguments"></a>Arguments

*Bitmap*<br/>
Zdrojový soubor jazyka C++ C nebo.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **předpokládá,** že soubory s příponou. c jsou zdrojové soubory c a soubory s příponou. cpp nebo. příponu CXX C++ .

Je-li zadána možnost **TC** nebo **TC** , je parametr [/Zc: Wchar_t (wchar_t je nativní typ)](zc-wchar-t-wchar-t-is-native-type.md) ignorován.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **Upřesnit** .

1. Upravte vlastnost **kompilovat jako** . Chcete-li změny použít, klikněte na **tlačítko OK** nebo **použít** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Příklady

Tento příkazový řádek CL určuje, že MAIN. c, TEST. prg a COLLATE. PRG jsou všechny zdrojové soubory jazyka C. CL nebude rozpoznávat PRINT. prg.

> HLAVNÍ CL. Tisk C/TcTEST.PRG/TcCOLLATE.PRG. PRG

Tento příkazový řádek CL určuje, že TEST1. c, TEST2. příponu CXX, TEST3. huh a TEST4. o jsou kompilovány C++ jako soubory a TEST5. z je kompilován jako soubor jazyka c.

> CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
