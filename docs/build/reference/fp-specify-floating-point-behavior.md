---
title: /fp (určení chování hodnot s plovoucí desetinnou čárkou)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: c90a35bbaf967ecf50977987865d6a768b019fe3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150776"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (určení chování hodnot s plovoucí desetinnou čárkou)

Určuje způsob, jakým kompilátor zpracovává výrazy, optimalizace a výjimky s plovoucí desetinnou čárkou. Možnosti **/FP** určují, zda bude generovaný kód umožňovat změnu prostředí s plovoucí desetinnou čárkou v režimu zaokrouhlování, masek výjimek a dílčím normálním chování a zda kontroly stavu s plovoucí desetinnou čárkou vracejí aktuální, přesné výsledky. Určuje, zda kompilátor generuje kód, který udržuje zdrojovou operaci a řazení výrazu, a odpovídá standardu pro šíření NaN, nebo pokud místo toho generuje efektivnější kód, který může změnit pořadí nebo kombinovat operace a použít zjednodušení. algebraických transformace, které nejsou povoleny standardem.

## <a name="syntax"></a>Syntaxe

> **/FP:** [**přesný** | **striktní** | **Fast** | **s výjimkou**[ **-** ]]

### <a name="arguments"></a>Argumenty

#### <a name="precise"></a>popsat

Ve výchozím nastavení kompilátor používá chování `/fp:precise`.

V části `/fp:precise` kompilátor zachovává vlastnosti řazení zdrojového výrazu a vlastnosti zaoblení kódu s plovoucí desetinnou čárkou, když generuje a optimalizuje kód objektu pro cílový počítač. Kompilátor se zaokrouhluje na přesnost zdrojového kódu ve čtyřech konkrétních bodech během vyhodnocování výrazu: u přiřazení na přetypování, když se argument s plovoucí desetinnou čárkou předává volání funkce a když se hodnota s plovoucí desetinnou čárkou vrátí z volání funkce. Mezilehlé výpočty se můžou provádět na přesnosti počítače. Přetypování se dá použít k explicitnímu zaokrouhlení zprostředkujících výpočtů.

Kompilátor neprovádí transformace algebraických pro výrazy s plovoucí desetinnou čárkou, jako je například opětovné přidružení nebo distribuce, pokud není zaručena transformace, aby vytvořila bitový identický výsledek.
Výrazy, které zahrnují speciální hodnoty (NaN, + Infinity,-Infinity,-0,0), se zpracovávají podle specifikací IEEE-754. Například `x != x` vyhodnotí jako **true** , pokud je x NaN. *Smluvní strany*s plovoucí desetinnou čárkou, tedy pokyny pro počítače, které kombinují operace s plovoucí desetinnou čárkou, mohou být vygenerovány v `/fp:precise`.

Kompilátor generuje kód určený ke spuštění ve [výchozím prostředí s plovoucí desetinnou](#the-default-floating-point-environment) čárkou a předpokládá, že prostředí s plovoucí desetinnou čárkou není k dispozici nebo upraveno za běhu. To znamená, že předpokládá, že kód neprovádí zrušení maskování výjimek s plovoucí desetinnou čárkou, čtení nebo zápis stavových registrů s plovoucí desetinnou čárkou, nebo změnu režimů zaokrouhlení.

Pokud váš kód s plovoucí desetinnou čárkou nezávisí na pořadí operací a výrazů v příkazech s plovoucí desetinnou čárkou (například pokud nezáleží na tom, zda je `a * b + a * c` vypočítávána jako `(b + c) * a` nebo `2 * a` jako `a + a`), zvažte možnost [/FP: Fast](#fast) , která může způsobit rychlejší a efektivnější kód. Pokud váš kód závisí na pořadí operací a výrazů a přistupuje k němu nebo mění prostředí s plovoucí desetinnou čárkou (například pro změnu režimů zaokrouhlení nebo soutisku výjimek s plovoucí desetinnou čárkou), použijte [/FP: Strict](#strict).

#### <a name="strict"></a>přísné

`/fp:strict` má podobné chování jako `/fp:precise`. kompilátor zachovává vlastnosti řazení zdroje a zaokrouhlování kódu s plovoucí desetinnou čárkou, když generuje a optimalizuje kód objektu pro cílový počítač a při zpracování speciálních hodnot sleduje Standard. Kromě toho může program bezpečně přistupovat k prostředí s plovoucí desetinnou čárkou nebo ho upravovat za běhu.

V rámci `/fp:strict`kompilátor generuje kód, který umožňuje programu bezpečně zrušit maskování výjimek s plovoucí desetinnou čárkou, číst nebo zapisovat Registry stavu s plovoucí desetinnou čárkou nebo měnit režimy zaokrouhlení. Se zaokrouhluje na přesnost zdrojového kódu ve čtyřech konkrétních bodech během vyhodnocování výrazu: v přiřazení na přetypování, když se argument s plovoucí desetinnou čárkou předává volání funkce a když se hodnota s plovoucí desetinnou čárkou vrátí z volání funkce. Mezilehlé výpočty se můžou provádět na přesnosti počítače. Přetypování se dá použít k explicitnímu zaokrouhlení zprostředkujících výpočtů. Kompilátor neprovádí transformace algebraických pro výrazy s plovoucí desetinnou čárkou, jako je například opětovné přidružení nebo distribuce, pokud není zaručena transformace, aby vytvořila bitový identický výsledek. Výrazy, které zahrnují speciální hodnoty (NaN, + Infinity,-Infinity,-0,0), se zpracovávají podle specifikací IEEE-754. Například `x != x` vyhodnotí jako **true** , pokud je x NaN. Smluvní strany s plovoucí desetinnou čárkou nejsou vygenerovány v `/fp:strict`.

`/fp:strict` je výpočetně dražší než `/fp:precise`, protože kompilátor musí vložit další pokyny pro depeše a umožní programům přístup nebo upravit prostředí s plovoucí desetinnou čárkou za běhu. Pokud váš kód tuto schopnost nepoužívá, ale vyžaduje řazení zdrojového kódu a zaokrouhlování nebo spoléhá na speciální hodnoty, použijte `/fp:precise`. V opačném případě zvažte použití `/fp:fast`, což může způsobit rychlejší a menší kód.

#### <a name="fast"></a>světl

Možnost `/fp:fast` umožňuje kompilátoru změnit pořadí, kombinování nebo zjednodušení operací s plovoucí desetinnou čárkou pro optimalizaci kódu s plovoucí desetinnou čárkou pro rychlost a místo. Kompilátor může vynechat zaokrouhlování v příkazech přiřazení, přetypování nebo volání funkcí. Může změnit pořadí operací nebo provádět transformace algebraických, například pomocí asociativních a obchodních zákonů, i když tyto transformace vedou ke pozorování různých chování při zaokrouhlování. Kvůli této rozšířené optimalizaci se výsledek některých výpočtů s plovoucí desetinnou čárkou může lišit od těch, které jsou vytvořené jinými možnostmi `/fp`. Speciální hodnoty (NaN, + Infinity,-Infinity,-0,0) se nedají rozšířit nebo se chovat výhradně podle standardu IEEE-754. V `/fp:fast`můžou být vygenerovány kontrakty s plovoucí desetinnou čárkou. Kompilátor je stále svázán se základní architekturou v rámci `/fp:fast`a další optimalizace mohou být k dispozici prostřednictvím použití možnosti [/arch](arch-minimum-cpu-architecture.md) .

V části `/fp:fast`kompilátor generuje kód určený ke spuštění ve výchozím prostředí s plovoucí desetinnou čárkou a předpokládá, že prostředí s plovoucí desetinnou čárkou není k dispozici nebo upraveno za běhu. To znamená, že předpokládá, že kód neprovádí zrušení maskování výjimek s plovoucí desetinnou čárkou, čtení nebo zápis stavových registrů s plovoucí desetinnou čárkou, nebo změnu režimů zaokrouhlení.

`/fp:fast` je určena pro programy, které nevyžadují striktní řazení zdrojového kódu a zaokrouhlování výrazů s plovoucí desetinnou čárkou, a nespoléhá se na standardní pravidla pro zpracování speciálních hodnot, jako je NaN. Pokud váš kód s plovoucí desetinnou čárkou vyžaduje zachování řazení zdrojového kódu a zaokrouhlování nebo spoléhá na standardní chování speciálních hodnot, použijte [/FP: přesně](#precise). Pokud váš kód přistupuje k prostředí s plovoucí desetinnou čárkou a mění režimy zaokrouhlení, odmaskuje výjimky s plovoucí desetinnou čárkou nebo kontroluje stav s plovoucí desetinnou čárkou, použijte [/FP: Strict](#strict).

#### <a name="except"></a>výjimk

Možnost `/fp:except` generuje kód, který zajistí, že jakékoli nemaskované výjimky s plovoucí desetinnou čárkou jsou vyvolány v přesném okamžiku, kdy k nim dojde, a že nejsou vyvolány žádné další výjimky s plovoucí desetinnou čárkou. Ve výchozím nastavení možnost `/fp:strict` povolí `/fp:except`a `/fp:precise` ne. Možnost `/fp:except` není kompatibilní s `/fp:fast`. Možnost může být explicitně zakázána od nás `/fp:except-`.

Všimněte si, že `/fp:except` nepovoluje žádné výjimky s plovoucí desetinnou čárkou samotné, ale je vyžadováno, aby programy povolovaly výjimky s plovoucí desetinnou čárkou. Informace o tom, jak povolit výjimky s plovoucí desetinnou čárkou, najdete v tématu [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) .

## <a name="remarks"></a>Poznámky

Ve stejném příkazovém řádku kompilátoru lze zadat více možností `/fp`. V současné době může být použita pouze jedna z možností `/fp:strict`, `/fp:fast`a `/fp:precise`. Je-li na příkazovém řádku zadán více než jedna z těchto možností, má možnost pozdější přednost a kompilátor vygeneruje upozornění. Možnosti `/fp:strict` a `/fp:except` nejsou kompatibilní s `/clr`.

Možnost [/za](za-ze-disable-language-extensions.md) (kompatibilita ANSI) není kompatibilní s `/fp`.

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>Použití direktiv kompilátoru k řízení chování s plovoucí desetinnou čárkou

Kompilátor poskytuje tři direktivy pragma pro přepsání chování s plovoucí desetinnou čárkou zadanou na příkazovém řádku: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md)a [fp_contract](../../preprocessor/fp-contract.md). Tyto direktivy lze použít k řízení chování plovoucí desetinné čárky na úrovni funkce, nikoli v rámci funkce. Všimněte si, že tyto direktivy neodpovídají přímo možnostem `/fp`. Tato tabulka ukazuje, jak jsou namapovány možnosti `/fp` a direktivy pragma na sebe navzájem. Další informace naleznete v dokumentaci pro jednotlivé možnosti a direktivy pragma.

||float_control (přesný)|float_control (kromě)|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|vypnuto|vypnuto|vypnuto|on|
|`/fp:precise`|on|vypnuto|vypnuto|on|
|`/fp:strict`|on|on|on|vypnuto|

### <a name="the-default-floating-point-environment"></a>Výchozí prostředí s plovoucí desetinnou čárkou

Při inicializaci procesu je nastavené *výchozí prostředí s plovoucí* desetinnou čárkou. Toto prostředí maskuje všechny výjimky s plovoucí desetinnou čárkou, nastaví režim zaokrouhlení na nejbližší (`FE_TONEAREST`), zachová subnormální (denormální) hodnoty, používá výchozí přesnost mantisa (mantisy) pro **float**, **Double**a **Long Double** a kde je to podporováno, nastaví ovládací prvek Infinite na výchozí režim spřažení.

### <a name="floating-point-environment-access-and-modification"></a>Přístup a úpravy prostředí s plovoucí desetinnou čárkou

Modul Microsoft Visual C++ runtime poskytuje několik funkcí pro přístup k prostředí s plovoucí desetinnou čárkou a jeho úpravu. Mezi ně patří [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)a [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) a jejich varianty. Aby se zajistilo správné chování programu, když váš kód přistupuje k prostředí s plovoucí desetinnou čárkou nebo ho upravuje, `fenv_access` musí být povolený, buď pomocí `/fp:strict` nebo pomocí direktivy pragma `fenv_access`, aby tyto funkce měly nějaký účinek. Pokud `fenv_access` není povolen, může přístup nebo úprava prostředí s plovoucí desetinnou čárkou způsobit neočekávané chování programu: kód nemusí akceptovat požadované změny prostředí s plovoucí desetinnou čárkou. Registry stavu s plovoucí desetinnou čárkou nemusí hlásit očekávané nebo aktuální výsledky; a neočekávané výjimky s plovoucí desetinnou čárkou mohou nastat nebo by neměly nastat výjimky s plovoucí desetinnou čárkou.

Když váš kód přistupuje nebo upravuje prostředí s plovoucí desetinnou čárkou, musíte být opatrní při kombinování kódu, kde je `fenv_access` povoleno s kódem, který nemá `fenv_access` povolen. V kódu, kde `fenv_access` není povolen, kompilátor předpokládá, že je aktivní prostředí s plovoucí desetinnou čárkou platformy a že stav s plovoucí desetinnou čárkou není k dispozici nebo upraven. Před přenesením řízení do funkce, která nemá povolenou `fenv_access`, doporučujeme uložit a obnovit místní prostředí s plovoucí desetinnou čárkou do výchozího stavu. Tento příklad ukazuje, jak lze nastavit a obnovit `float_control` direktivu pragma:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Režimy zaokrouhlení s plovoucí desetinnou čárkou

V obou `/fp:precise` a `/fp:fast` kompilátor generuje kód určený ke spuštění ve výchozím prostředí s plovoucí desetinnou čárkou a předpokládá, že prostředí není k dispozici nebo upraveno za běhu. To znamená, že předpokládá, že kód neprovádí zrušení maskování výjimek s plovoucí desetinnou čárkou, čtení nebo zápis stavových registrů s plovoucí desetinnou čárkou, nebo změnu režimů zaokrouhlení.  Některé programy ale musí změnit prostředí s plovoucí desetinnou čárkou. Například Tato ukázka počítá chybovou mez násobení plovoucí desetinné čárky změnou režimů zaokrouhlení s plovoucí desetinnou čárkou:

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

Vzhledem k tomu, že kompilátor předpokládá, že je v rámci `/fp:fast` výchozí prostředí s plovoucí desetinnou čárkou, `/fp:precise` je zdarma ignorovat volání `_controlfp_s`. Například při kompilování pomocí `/O2` a `/fp:precise` pro architekturu x86 nejsou hranice vypočítány a výstupní program zahrnuje výstupy:

```Output
cLower = -inf
cUpper = -inf
```

Když se zkompiluje s `/O2` i `/fp:strict` pro architekturu x86, ukázkový výstup programu:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Speciální hodnoty s plovoucí desetinnou čárkou

V části `/fp:precise` a `/fp:strict`výrazy, které zahrnují speciální hodnoty (NaN, + Infinity,-Infinity,-0,0), se chovají podle specifikace IEEE-754. V části `/fp:fast`může být chování těchto speciálních hodnot nekonzistentní s IEEE-754.

Tato ukázka demonstruje různé chování speciálních hodnot v části `/fp:precise``/fp:strict` a `/fp:fast`:

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

Při kompilaci s `/O2` `/fp:precise` nebo `/O2` `/fp:strict` pro architekturu x86 jsou výstupy konzistentní se specifikací IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Při kompilaci s `/O2` `/fp:fast` pro architekturu x86 nejsou výstupy konzistentní s IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Transformace algebraických s plovoucí desetinnou čárkou

V rámci `/fp:precise` a `/fp:strict`kompilátor neprovádí matematické transformace, pokud není zaručena transformace, aby vytvořila bitový identický výsledek. Kompilátor může provádět takové transformace v rámci `/fp:fast`. Například výraz `a * b + a * c` ve vzorové funkci `algebraic_transformation` může být zkompilován do `a * (b + c)` v `/fp:fast`. Tyto transformace nejsou prováděny v rámci `/fp:precise` nebo `/fp:strict`a kompilátor generuje `a * b + a * c`.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Explicitní přetypování do plovoucí desetinné čárky

V rámci `/fp:precise` a `/fp:strict`kompilátor zaokrouhlí na přesnost zdrojového kódu ve čtyřech konkrétních bodech během vyhodnocování výrazu: v přiřazení na přetypování, když je argument s plovoucí desetinnou čárkou předán volání funkce a při vrácení hodnoty s plovoucí desetinnou čárkou z volání funkce. Přetypování se dá použít k explicitnímu zaokrouhlení zprostředkujících výpočtů. V části `/fp:fast`Kompilátor negeneruje explicitní přetypování v těchto bodech pro zajištění přesnosti zdrojového kódu. Tato ukázka demonstruje chování v rámci různých možností `/fp`:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Při kompilaci pomocí `/O2` `/fp:precise` nebo `/O2` `/fp:strict`, vidíte, že explicitní přetypování jsou vloženy do přetypovat i na návratový bod funkce v generovaném kódu pro architekturu x64:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

V části `/O2` `/fp:fast` vygenerovaný kód je zjednodušen, protože jsou optimalizována všechna přetypování typů:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **generování kódu** **C++ jazyka C/**  > .

1. Upravte vlastnost **modelu plovoucí desetinné** čárky.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
