---
title: /MD,-MT,-LD (použití knihovny run-time)
ms.date: 07/17/2019
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
ms.openlocfilehash: a66677ebbef984e9a4c8190f184ca3a9126a7b83
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550755"
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
|**/MD**|Způsobí, že aplikace použije verzi knihovny runtime, která je vícevláknová a specifická pro knihovnu DLL. Definuje `_MT` a `_DLL` způsobí, že kompilátor umístí do souboru. obj název knihovny Msvcrt. lib.<br /><br /> Aplikace kompilované s tímto parametrem jsou staticky propojeny se souborem MSVCRT.lib. Tato knihovna poskytuje vrstvu kódu, která linkeru umožňuje překládat externí odkazy. Skutečný pracovní kód je obsažen v MSVCR*číslo_verze*. Knihovna DLL, která musí být k dispozici v době běhu do aplikací propojených s knihovnou MSVCRT. lib.|
|**/MDd**|Definuje `_DEBUG` , a `_MT` `_DLL` a způsobí, že aplikace použije ladění verze běhové knihovny specifické pro vícevláknové zpracování a DLL. Navíc způsobí, že kompilátor umístí knihovnu s názvem MSVCRTD.lib do souboru .obj.|
|**/MT**|Způsobí, že aplikace použije vícevláknovou statickou verzi knihovny runtime. Definuje `_MT` a způsobí, že kompilátor umístí do souboru. obj název knihovny Libcmt. lib, takže linker použije Libcmt. lib k vyřešení externích symbolů.|
|**/MTd**|Definuje `_DEBUG` a `_MT` . Tento parametr navíc způsobí, že kompilátor umístí knihovnu s názvem LIBCMTD.lib do souboru .obj, aby linker použil k překladu externích symbolů soubor LIBCMTD.lib.|
|**/LD**|Vytvoří knihovnu DLL.<br /><br /> Předá do linkeru možnost **/DLL** . Linker hledá, ale nevyžaduje `DllMain` funkci. Pokud nezapíšete `DllMain` funkci, linker vloží `DllMain` funkci, která vrací hodnotu true.<br /><br /> Propojí spouštěcí kód knihovny DLL.<br /><br /> Vytvoří knihovnu importu (.lib), není-li na příkazovém řádku zadán soubor exportu (.exp). Knihovnu importu propojíte s aplikacemi, které volají vaši knihovnu DLL.<br /><br /> Interpretuje [/FE (pojmenování souboru exe)](fe-name-exe-file.md) jako pojmenování knihovny DLL namísto souboru. exe. Ve výchozím nastavení se název programu zobrazí jako *Base*. dll namísto názvu *souboru.* exe.<br /><br /> Implikuje **/Mt** , pokud explicitně neurčíte **/MD**.|
|**/LDd**|Vytvoří ladicí knihovnu DLL. Definuje `_MT` a `_DEBUG` .|

Další informace o knihovnách run-time jazyka C a o tom, které knihovny se používají při kompilaci s možností [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md), naleznete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

Všechny moduly předané danému vyvolání linkeru musí být kompilovány se stejnou možností kompilátoru Run-Time Library (**/MD**, **/Mt**, **/ld**).

Další informace o tom, jak používat ladicí verze knihoven run-time, naleznete v tématu [C Run-Time Library Reference](../../c-runtime-library/c-run-time-library-reference.md).

Další informace o knihovnách DLL naleznete v tématu [Create C/C++ dlls in Visual Studio](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace**  >  Stránka vlastností generování kódu**C/C++**  >  **Code Generation** .

1. Upravte vlastnost **běhové knihovny** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
