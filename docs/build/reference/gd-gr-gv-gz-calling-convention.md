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
ms.openlocfilehash: 73fce079a98a3f4afaa35f8b8c6630fc8a9b4ca4
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825523"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konvence volání)

Tyto možnosti určují pořadí, ve kterém jsou argumenty funkce vloženy do zásobníku, zda volající funkce nebo volaná funkce odebere argumenty ze zásobníku na konci volání a konvenci Name-upravení, kterou kompilátor používá k identifikaci jednotlivých funkcí.

## <a name="syntax"></a>Syntaxe

> **/GD**\
> **/GR**\
> **/GV**\
> **/GZ**

## <a name="remarks"></a>Poznámky

**/GD**, výchozí nastavení, určuje [__cdecl](../../cpp/cdecl.md) konvence volání pro všechny funkce s výjimkou členských funkcí jazyka C++ a funkcí, které jsou označeny [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)nebo [__vectorcall](../../cpp/vectorcall.md).

**/Gr** určuje konvenci `__fastcall` volání pro všechny funkce s výjimkou členských funkcí jazyka C++ `main`, funkcí nazvaných a funkcí `__cdecl`, `__stdcall`které jsou `__vectorcall`označeny, nebo. Všechny `__fastcall` funkce musí mít prototypy. Tato konvence volání je k dispozici pouze v kompilátorech cílících na platformu x86 a jsou ignorovány kompilátory, které cílí na jiné architektury.

**/GZ** určuje konvenci `__stdcall` volání pro všechny funkce s výjimkou členských funkcí jazyka C++ `main`, funkcí nazvaných a funkcí `__cdecl`, `__fastcall`které jsou `__vectorcall`označeny, nebo. Všechny `__stdcall` funkce musí mít prototypy. Tato konvence volání je k dispozici pouze v kompilátorech cílících na platformu x86 a jsou ignorovány kompilátory, které cílí na jiné architektury.

**/GV** Určuje `__vectorcall` konvenci volání pro všechny funkce s výjimkou členských funkcí jazyka C++ `main`, funkce s názvem `vararg` , funkce s proměnným seznamem argumentů nebo funkce, které jsou `__cdecl`označeny `__stdcall`konfliktem `__fastcall` , nebo. Tato konvence volání je k dispozici pouze v architekturách x86 a x64, které podporují/arch: SSE2 a vyšší a jsou ignorovány kompilátory, které cílí na architekturu ARM.

Funkce, které přijímají proměnlivý počet argumentů, musí `__cdecl`být označeny.

**/GD**, **/gr**, **/GV** a **/GZ** nejsou kompatibilní s [/clr: Safe](clr-common-language-runtime-compilation.md) nebo **/clr: Pure**. Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017 a novější.

> [!NOTE]
> Ve výchozím nastavení pro procesory x86 používají členské funkce jazyka C++ [__thiscall](../../cpp/thiscall.md).

Pro všechny procesory, členská funkce, která je explicitně `__cdecl`označena `__vectorcall`jako, `__stdcall` `__fastcall`,, nebo používá specifikovanou konvenci volání, pokud není v této architektuře ignorována. Členská funkce, která přijímá proměnný počet argumentů, vždy používá konvenci `__cdecl` volání.

Tyto možnosti kompilátoru nemají žádný vliv na dekoraci názvů metod a funkcí jazyka C++. Pokud nejsou deklarovány jako `extern "C"`, metody a funkce jazyka C++ používají jiné schéma upravení názvů. Další informace najdete v tématu [dekorované názvy](decorated-names.md).

Další informace o konvencích volání naleznete v tématu [konvence volání](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>__cdecl specifické

U procesorů x86 jsou všechny argumenty funkce předány v zásobníku zprava doleva. V architekturách ARM a x64 jsou některé argumenty předány registrem a zbytek se předává v zásobníku zprava doleva. Rutina volání odvolá argumenty ze zásobníku.

V případě jazyka C `__cdecl` používá konvence pojmenování název funkce před podtržítkem ( `_` ); neprovádí se žádný překlad případu. Pokud není deklarován `extern "C"`jako, funkce jazyka C++ použijí jiné schéma upravení názvů. Další informace najdete v tématu [dekorované názvy](decorated-names.md).

## <a name="__fastcall-specifics"></a>__fastcall specifické

Některé argumenty `__fastcall` funkce jsou předány v registrech (pro procesory x86, ECX a EDX) a zbývající jsou vloženy do zásobníku zprava doleva. Volaná rutina před vrácením z zásobníku tyto argumenty převezme. **/Gr** obvykle zkracuje dobu provádění.

> [!NOTE]
> Buďte opatrní při použití konvence `__fastcall` volání pro všechny funkce, které jsou zapsány ve vloženém jazyce sestavení. Vaše použití registrů může být v konfliktu s použitím kompilátoru.

V případě jazyka C `__fastcall` používá konvence pojmenování název funkce před znakem v (**\@**) následovaný velikostí argumentů funkce v bajtech. Neprovádí se žádný překlad případu. Kompilátor používá tuto šablonu pro konvenci vytváření názvů:

`@function_name@number`

Při použití konvence `__fastcall` pojmenování použijte standardní soubory k zahrnutí. Jinak obdržíte nevyřešené externí odkazy.

## <a name="__stdcall-specifics"></a>__stdcall specifické

Argumenty `__stdcall` funkce jsou vloženy do zásobníku zprava doleva a volaná funkce tyto argumenty z zásobníku před tím, než se vrátí.

V případě jazyka C `__stdcall` konvence pojmenování používá název funkce předchází podtržítkem (**\_**) a následuje znakem "at"**\@**() a velikostí argumentů funkce v bajtech. Neprovádí se žádný překlad případu. Kompilátor používá tuto šablonu pro konvenci vytváření názvů:

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall specifické

Celočíselné argumenty `__vectorcall` funkce jsou předávány hodnotou, pomocí až dvou (na platformě x86) nebo čtyř (na platformě x64) registrech v celočíselném formátu a až šesti XMM registrů pro hodnoty s plovoucí desetinnou čárkou a vektoru a zbytek se předává v zásobníku zprava doleva. Volaná funkce vyčistí zásobník před jeho vrácením. V XMM0 se vrátí vektorové a návratové hodnoty s plovoucí desetinnou čárkou.

V případě jazyka C `__vectorcall` používá konvence pojmenování název funkce následovaný dvěma znaménky**\@**() a velikostí argumentů funkce v bajtech. Neprovádí se žádný překlad případu. Kompilátor používá tuto šablonu pro konvenci vytváření názvů:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku**rozšířených** vlastností **C/C++** > .

1. Upravte vlastnost **konvence volání** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Viz také

- [Parametry kompilátoru MSVC](compiler-options.md)
- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
