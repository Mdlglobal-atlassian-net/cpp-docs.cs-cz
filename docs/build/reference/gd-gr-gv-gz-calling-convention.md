---
title: /Gd, /Gr, /Gv, /Gz (Konvence volání)
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: ab10ac1a4d0c327ff4d0ae54620f3fde752e020b
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150807"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konvence volání)

Tyto možnosti určují pořadí, ve kterém jsou argumenty funkce vloženy do zásobníku, zda volající funkce nebo volaná funkce odebere argumenty ze zásobníku na konci volání a konvenci Name-upravení, kterou kompilátor používá k identifikaci jednotlivé funkce.

## <a name="syntax"></a>Syntaxe

> **/GD**<br/>
> **/GR**<br/>
> **/GV**<br/>
> **/GZ**

## <a name="remarks"></a>Poznámky

**/GD**, výchozí nastavení, určuje [__cdecl](../../cpp/cdecl.md) konvence volání pro všechny C++ funkce s výjimkou členských funkcí a funkcí, které jsou označeny [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)nebo [__vectorcall](../../cpp/vectorcall.md).

**/Gr** určuje konvenci volání `__fastcall` pro všechny funkce s C++ výjimkou členských funkcí, funkcí nazvaných `main`a funkcí, které jsou označeny `__cdecl`, `__stdcall`nebo `__vectorcall`. Všechny funkce `__fastcall` musí mít prototypy. Tato konvence volání je k dispozici pouze v kompilátorech cílících na platformu x86 a jsou ignorovány kompilátory, které cílí na jiné architektury.

**/GZ** určuje konvenci volání `__stdcall` pro všechny funkce s C++ výjimkou členských funkcí, funkcí nazvaných `main`a funkcí, které jsou označeny `__cdecl`, `__fastcall`nebo `__vectorcall`. Všechny funkce `__stdcall` musí mít prototypy. Tato konvence volání je k dispozici pouze v kompilátorech cílících na platformu x86 a jsou ignorovány kompilátory, které cílí na jiné architektury.

**/GV** určuje konvenci volání `__vectorcall` pro všechny funkce s C++ výjimkou členských funkcí, funkcí nazvaných `main`, funkcí se seznamem argumentů `vararg` proměnných, nebo funkcí, které jsou označeny konfliktní `__cdecl`, `__stdcall`nebo `__fastcall` atribut. Tato konvence volání je k dispozici pouze v architekturách x86 a x64, které podporují/arch: SSE2 a vyšší a jsou ignorovány kompilátory, které cílí na architekturu ARM.

Funkce, které přijímají proměnný počet argumentů, musí být označeny `__cdecl`.

**/GD**, **/gr**, **/GV** a **/GZ** nejsou kompatibilní s [/clr: Safe](clr-common-language-runtime-compilation.md) nebo **/clr: Pure**. Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017 a novější.

> [!NOTE]
> Ve výchozím nastavení pro procesory C++ x86 používají členské funkce [__thiscall](../../cpp/thiscall.md).

Pro všechny procesory, členská funkce, která je explicitně označena jako `__cdecl`, `__fastcall`, `__vectorcall`nebo `__stdcall` používá zadanou konvenci volání, pokud není v této architektuře ignorována. Členská funkce, která přijímá proměnný počet argumentů, vždy používá konvenci volání `__cdecl`.

Tyto možnosti kompilátoru nemají žádný vliv na název dekorace C++ metod a funkcí. Pokud se nedeklaruje jako C++ `extern "C"`, metody a funkce používají jiné schéma Name-upravení. Další informace najdete v tématu [dekorované názvy](decorated-names.md).

Další informace o konvencích volání naleznete v tématu [konvence volání](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>__cdecl specifické

U procesorů x86 jsou všechny argumenty funkce předány v zásobníku zprava doleva. V architekturách ARM a x64 jsou některé argumenty předány registrem a zbytek se předává v zásobníku zprava doleva. Rutina volání odvolá argumenty ze zásobníku.

V případě jazyka C `__cdecl` konvence pojmenování používá název funkce předchází podtržítkem (`_`); neprovádí se žádný překlad případu. Pokud se nedeklaruje jako C++ `extern "C"`, funkce používají jiné schéma s názvem upravení. Další informace najdete v tématu [dekorované názvy](decorated-names.md).

## <a name="__fastcall-specifics"></a>__fastcall specifické

Některé argumenty funkce `__fastcall` jsou předány v registrech (pro procesory x86, ECX a EDX) a zbývající jsou vloženy do zásobníku zprava doleva. Volaná rutina před vrácením z zásobníku tyto argumenty převezme. **/Gr** obvykle zkracuje dobu provádění.

> [!NOTE]
> Buďte opatrní při použití `__fastcall` konvence volání pro všechny funkce, které jsou napsány ve vloženém jazyce sestavení. Vaše použití registrů může být v konfliktu s použitím kompilátoru.

V případě jazyka C `__fastcall` konvence pojmenování používá název funkce, před kterým následuje znaménko ( **\@** ) následovaný velikostí argumentů funkce v bajtech. Neprovádí se žádný překlad případu. Kompilátor používá tuto šablonu pro konvenci vytváření názvů:

`@function_name@number`

Při použití `__fastcall` konvence pojmenování použijte standardní soubory k zahrnutí. Jinak obdržíte nevyřešené externí odkazy.

## <a name="__stdcall-specifics"></a>__stdcall specifické

Argumenty funkce `__stdcall` jsou vloženy do zásobníku zprava doleva a volaná funkce tyto argumenty ze zásobníku před vrácením vrátí.

V případě jazyka C `__stdcall` konvence pojmenování používá název funkce předchází podtržítkem ( **\_** ) a následuje znakem při znaménku ( **\@** ) a velikostí argumentů funkce v bajtech. Neprovádí se žádný překlad případu. Kompilátor používá tuto šablonu pro konvenci vytváření názvů:

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall specifické

Celočíselné argumenty funkce `__vectorcall` jsou předávány hodnotou, za použití až dvou (na platformě x86) nebo čtyř (na platformě x64) registrů celých čísel a až šesti registrů XMM pro hodnoty s plovoucí desetinnou čárkou a vektoru a zbytek se předává v zásobníku zprava doleva. Volaná funkce vyčistí zásobník před jeho vrácením. V XMM0 se vrátí vektorové a návratové hodnoty s plovoucí desetinnou čárkou.

V případě jazyka C `__vectorcall` konvence pojmenování používá název funkce následovaný dvěma znaménky ( **\@\@** ) a velikostí argumentů funkce v bajtech. Neprovádí se žádný překlad případu. Kompilátor používá tuto šablonu pro konvenci vytváření názvů:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Upřesnit** v jazyce **C/C++**  > .

1. Upravte vlastnost **konvence volání** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Viz také

- [Parametry kompilátoru MSVC](compiler-options.md)
- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
