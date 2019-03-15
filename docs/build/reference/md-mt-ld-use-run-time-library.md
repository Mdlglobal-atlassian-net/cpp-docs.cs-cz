---
title: / MD, -MT, -LD (použití knihovny Run-Time)
ms.date: 11/04/2016
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
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
ms.openlocfilehash: 59b0483d76a2a98c1f278a323a827b243d21adea
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822486"
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
|**/MD**|Způsobí, že aplikace použije verzi knihovny runtime, která je vícevláknová a specifická pro knihovnu DLL. Definuje `_MT` a `_DLL` a způsobí, že kompilátor umístí knihovnu s názvem MSVCRT.lib do souboru .obj.<br /><br /> Aplikace kompilované s tímto parametrem jsou staticky propojeny se souborem MSVCRT.lib. Tato knihovna poskytuje vrstvu kódu, která linkeru umožňuje překládat externí odkazy. Skutečný pracovní kód je obsažen v knihovně MSVCR*číslo_verze*. Knihovny DLL, která musí být k dispozici v době běhu k aplikacím propojeným s knihovnou MSVCRT.lib.|
|**/MDd**|Definuje `_DEBUG`, `_MT`, a `_DLL` a způsobí, že aplikace použije ladicí Vícevláknová a specifická knihovnu DLL verze knihovny run-time. Navíc způsobí, že kompilátor umístí knihovnu s názvem MSVCRTD.lib do souboru .obj.|
|**/MT**|Způsobí, že aplikace použije vícevláknovou statickou verzi knihovny runtime. Definuje `_MT` a způsobí, že kompilátor umístí knihovnu s názvem LIBCMT.lib do souboru .obj, aby linker použil k překladu externích symbolů LIBCMT.lib.|
|**/MTd**|Definuje `_DEBUG` a `_MT`. Tento parametr navíc způsobí, že kompilátor umístí knihovnu s názvem LIBCMTD.lib do souboru .obj, aby linker použil k překladu externích symbolů soubor LIBCMTD.lib.|
|**/LD**|Vytvoří knihovnu DLL.<br /><br /> Předává **/dll** – možnost linkeru. Propojovací program hledá, ale nevyžaduje, `DllMain` funkce. Pokud nenapíšete `DllMain` vloží linker funkci `DllMain` funkce, která vrací hodnotu TRUE.<br /><br /> Propojí spouštěcí kód knihovny DLL.<br /><br /> Vytvoří knihovnu importu (.lib), není-li na příkazovém řádku zadán soubor exportu (.exp). Knihovnu importu propojíte s aplikacemi, které volají vaši knihovnu DLL.<br /><br /> Interpretuje [/Fe (pojmenování souboru EXE)](fe-name-exe-file.md) jako pojmenování knihovny DLL a nikoli souboru .exe. Ve výchozím nastavení, název programu bude *basename*.dll namísto *basename*.exe.<br /><br /> Zahrnuje **/MT** Pokud explicitně neurčíte **/MD**.|
|**/LDd**|Vytvoří ladicí knihovnu DLL. Definuje `_MT` a `_DEBUG`.|

Další informace o běhové knihovny jazyka C a které knihovny se používají při kompilaci s [/CLR (kompilace Common Language Runtime)](clr-common-language-runtime-compilation.md), naleznete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

Všechny moduly předané danému vyvolání linkeru musí být zkompilovány s možností kompilátoru stejné knihovny run-time (**/MD**, **/MT**, **/LD**).

Další informace o použití ladicích verzí knihoven runtime naleznete v tématu [C Run-Time Library Reference](../../c-runtime-library/c-run-time-library-reference.md).

Další informace o knihovnách DLL naleznete v tématu [knihovny DLL v jazyce Visual C++](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **C/C++** složky.

1. Vyberte **generování kódu** stránku vlastností.

1. Upravit **knihovny prostředí Runtime** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
