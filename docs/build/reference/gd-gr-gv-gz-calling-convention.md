---
title: / Gd, / GR, / gv, /Gz (konvence volání) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7e6c1466ecc7bce26eb4dabd816e1733f16ae13
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895133"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konvence volání)

Tyto možnosti určují pořadí ve funkci, která argumenty jsou vloženy do zásobníku, zda funkce volajícího nebo volaná funkce odstraní argumenty ze zásobníku volání na konci volání a konvence dekorování, který kompilátor používá k identifikaci jednotlivé funkce.

## <a name="syntax"></a>Syntaxe

> **/Gd**<br/>
> **/GR**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>Poznámky

**/GD –**, výchozí nastavení, určuje, [__cdecl](../../cpp/cdecl.md) konvence volání pro všechny funkce s výjimkou členských C++, funkce a funkce, které jsou označeny [__stdcall](../../cpp/stdcall.md), [__ fastcall](../../cpp/fastcall.md), nebo [__vectorcall](../../cpp/vectorcall.md).

**/GR** Určuje, `__fastcall` konvence volání pro všechny funkce s výjimkou členských funkcí jazyka C++, funkce s názvem `main`a funkce, které jsou označeny `__cdecl`, `__stdcall`, nebo `__vectorcall`. Všechny `__fastcall` funkce musejí mít prototypy. Tato konvence volání je k dispozici v kompilátorech, které se zaměřují x86 pouze a ignorováno kompilátory, které se zaměřují na jiné architektury.

**/GZ** Určuje, `__stdcall` konvence volání pro všechny funkce s výjimkou členských funkcí jazyka C++, funkce s názvem `main`a funkce, které jsou označeny `__cdecl`, `__fastcall`, nebo `__vectorcall`. Všechny `__stdcall` funkce musejí mít prototypy. Tato konvence volání je k dispozici v kompilátorech, které se zaměřují x86 pouze a ignorováno kompilátory, které se zaměřují na jiné architektury.

**/Gv** Určuje `__vectorcall` konvence volání pro všechny funkce s výjimkou členských funkcí jazyka C++, funkcí pojmenovaných jako hlavní, funkcí s `vararg` Proměnný seznam argumentů nebo funkce, které jsou označeny konfliktním `__cdecl`, `__stdcall`, nebo `__fastcall` atribut. Tato konvence volání je k dispozici pouze v x86 a x64 architektury, které podporují SSE2 a vyšší a je ignorován kompilátory, které se zaměřují na architekturu ARM.

Funkce vyžadující proměnný počet argumentů musí být označen `__cdecl`.

**/GD –**, **GR**, **/Gv** a **/Gz** nejsou kompatibilní s [/CLR: safe](../../build/reference/clr-common-language-runtime-compilation.md) nebo   **/CLR: pure**. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

> [!NOTE]
> Ve výchozím nastavení pro x86 procesory, členské funkce C++ použijí [klíčové slovo __thiscall](../../cpp/thiscall.md).

Pro všechny procesory, členská funkce, která je explicitně označena jako `__cdecl`, `__fastcall`, `__vectorcall`, nebo `__stdcall` používá zadané konvence volání, pokud není ignorována u této architektury. Členská funkce, která přijímá proměnný počet argumentů, vždy používá `__cdecl` konvence volání.

Tyto možnosti kompilátoru nemají žádný vliv na názvovou dekoraci metod C++ a funkcí. Pokud nejsou deklarovány jako `extern "C"`, používají jiné schéma dekorování C++ metody a funkce. Další informace najdete v tématu [dekorované názvy](../../build/reference/decorated-names.md).

Další informace o konvencích volání naleznete v tématu [konvence volání](../../cpp/calling-conventions.md).

## <a name="cdecl-specifics"></a>Specifikace __cdecl

Na x86 procesory, všechny argumenty jsou předány v zásobníku zprava doleva. Na ARM a x64 některé argumenty jsou předány registrem a ostatní jsou předány v zásobníku zprava doleva. Rutina volání vezme argumenty ze zásobníku POP.

Pro jazyk C `__cdecl` používá konvence pojmenování název funkce začínající podtržítkem ( `_` ); provádí se žádný překlad případu. Pokud nejsou deklarovány jako `extern "C"`, používají funkce jazyka C++ jiné schéma dekorování. Další informace najdete v tématu [dekorované názvy](../../build/reference/decorated-names.md).

## <a name="fastcall-specifics"></a>Specifikace __fastcall

Část `__fastcall` argumenty funkce předány v registrech (pro x86 procesory, ECX a EDX), a zbývající je vložena do zásobníku zprava doleva. Volaná rutina vyjme tyto argumenty ze zásobníku ještě před jeho vrácením. Obvykle **GR** snižuje dobu provádění.

> [!NOTE]
> Buďte opatrní při použití `__fastcall` konvence volání pro všechny funkce, který je napsán ve vloženém jazyce sestavení. Využití registrů by mohla v konfliktu s použitím kompilátoru.

Pro jazyk C `__fastcall` používá konvence pojmenování název funkce předchází zavináč (**\@**) následovaný velikostí argumentů funkce v bajtech. Provádí se žádný překlad případu. Kompilátor používá tuto šablonu pro vytváření názvů:

`@function_name@number`

Při použití `__fastcall` zásady vytváření názvů, použijte standardní soubory zahrnutí. V opačném případě získáte nevyřešené externí odkazy.

## <a name="stdcall-specifics"></a>Specifikace __stdcall

A `__stdcall` jsou argumenty funkce vloženy do zásobníku zprava doleva a volaná funkce tyto argumenty zobrazí ze zásobníku ještě před jeho vrácením.

Pro jazyk C `__stdcall` používá konvence pojmenování název funkce začínající podtržítkem (**\_**) a za nímž následuje zavináč (**\@**) a velikost funkce argumentů v bajtech. Provádí se žádný překlad případu. Kompilátor používá tuto šablonu pro vytváření názvů:

`_functionname@number`

## <a name="vectorcall-specifics"></a>Specifikace __vectorcall

A `__vectorcall` celočíselné argumenty funkce jsou předávány hodnotou, využívají až dva (na x86) nebo čtyři (na x64) celočíselné registry a až šest registrů XMM zaregistruje s plovoucí desetinnou čárkou a hodnoty vektoru a ostatní jsou předány v zásobníku zprava doleva. Volaná funkce vyčistí zásobník před jeho vrácením. Vektorové a vrácené hodnoty s plovoucí desetinnou čárkou jsou vráceny v XMM0.

Pro jazyk C `__vectorcall` zásady vytváření názvů používá název funkce následovaný dvěma zavináči (**\@\@**) a velikostí argumentů funkce v bajtech. Provádí se žádný překlad případu. Kompilátor používá tuto šablonu pro vytváření názvů:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** > **Upřesnit** stránku vlastností.

1. Upravit **konvence volání** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru](../../build/reference/compiler-options.md)
- [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
