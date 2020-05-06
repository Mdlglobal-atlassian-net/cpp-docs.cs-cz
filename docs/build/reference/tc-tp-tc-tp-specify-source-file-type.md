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
ms.openlocfilehash: fa35249983284261252c8ada65e79ed1cb6ec79a
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825389"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (zadání typu zdrojového souboru)

Možnost **/TC** určuje, že jeho argument filename je zdrojový soubor jazyka C, a to i v případě, že nemá příponu. C. Parametr **/TP** určuje, že jeho argument filename je zdrojový soubor C++, a to i v případě, že nemá příponu. cpp nebo. příponu CXX. Mezera mezi možností a názvem souboru je volitelná. Jednotlivé možnosti určují jeden soubor. Chcete-li zadat další soubory, opakujte možnost.

**/TC** a **/TP** jsou globálními variantami **/TC** a **/TP**. Určují kompilátor, aby považoval všechny soubory pojmenované na příkazovém řádku jako zdrojové soubory jazyka C (**/TC**) nebo zdrojové soubory jazyka C++ (**/TP**) bez ohledu na umístění na příkazovém řádku ve vztahu k možnosti. Tyto globální možnosti lze přepsat v jednom souboru prostřednictvím **/TC** nebo **/TP**.

## <a name="syntax"></a>Syntaxe

> **/Tc** _Název souboru_ /TC\
> **/TP** _název_souboru_\
> **/TC**\
> **/TP**

### <a name="arguments"></a>Argumenty

*Bitmap*<br/>
Zdrojový soubor jazyka C nebo C++.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **předpokládá,** že soubory s příponou. c jsou zdrojové soubory jazyka c a soubory s příponou. cpp nebo. příponu CXX jsou zdrojové soubory jazyka C++.

Je-li zadána možnost **TC** nebo **TC** , je možnost ["/Zc: Wchar_t (wchar_t je nativní typ)](zc-wchar-t-wchar-t-is-native-type.md) ignorována.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku **vlastnosti** > konfigurace**Upřesnit** vlastnost**C/C++** > .

1. Upravte vlastnost **kompilovat jako** . Chcete-li změny použít, klikněte na **tlačítko OK** nebo **použít** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Příklady

Tento příkazový řádek CL určuje, že MAIN. c, TEST. prg a COLLATE. PRG jsou všechny zdrojové soubory jazyka C. CL nebude rozpoznávat PRINT. prg.

> HLAVNÍ CL. Tisk C/TcTEST.PRG/TcCOLLATE.PRG. PRG

Tento příkazový řádek CL určuje, že TEST1. c, TEST2. příponu CXX, TEST3. huh a TEST4. o jsou kompilovány jako soubory jazyka C++ a TEST5. z je kompilován jako soubor jazyka C.

> CL TEST1. TEST2 C. PŘÍPONU CXX TEST3. HUH TEST4. O/TC TEST5. Z/TP

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
