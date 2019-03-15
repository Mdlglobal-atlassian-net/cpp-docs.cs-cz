---
title: /fp (zadání chování plovoucí desetinné čárky)
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
ms.openlocfilehash: 616efc0980c6ddadfee078dbe7a382372c5636ec
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818164"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (zadání chování plovoucí desetinné čárky)

Určuje, jak kompilátor považuje výrazů s plovoucí desetinnou čárkou, optimalizací a výjimky. **/FP** určují, zda umožňuje generovaný kód s plovoucí desetinnou čárkou prostředí změní režim, výjimka masek a subnormal chování a zda kontroly stavu s plovoucí desetinnou čárkou vrátí aktuální, správné výsledky. Určuje, zda kompilátor generuje kód, který udržuje operaci správy zdrojových a výraz řazení a odpovídá standardu pro šíření hodnoty NaN, nebo pokud místo toho generuje efektivnější kód, který může změnit pořadí nebo kombinace operací a použití, která zjednodušuje jejich algebraický transformace, které nejsou povoleny Standard.

## <a name="syntax"></a>Syntaxe

> **/ FP:**[**přesné** | **striktní** | **rychlé** | **s výjimkou**[ **-**]]

### <a name="arguments"></a>Arguments

#### <a name="precise"></a>přesné

Ve výchozím nastavení, kterou kompilátor používá **/FP: precise** chování.

V části **/FP: precise** kompilátor zachová zdrojový výraz řazení a zaokrouhlení vlastnosti kód s plovoucí desetinnou čárkou, když ji vygeneruje a optimalizuje objektový kód pro cílový počítač. Kompilátor zaokrouhlí na přesnost zdrojového kódu na čtyři konkrétní body při vyhodnocení výrazu: v přiřazeních na zaokrouhlovat, když volání funkce je předán jako argument s plovoucí desetinnou čárkou a při hodnotu s plovoucí desetinnou čárkou je vrácená z volání funkce. Zprostředkující výpočty mohou být provedeny v počítači přesnosti. Zaokrouhlovat lze explicitně zaokrouhlit zprostředkující výpočty.

Kompilátor neprovádí algebraických transformace výrazů s plovoucí desetinnou čárkou, jako je například opětovné přiřazení nebo distribuce, pokud je zaručeno, že transformace bitový identické výsledkem.
Výrazy, které se týkají zvláštní hodnoty (NaN, + nekonečno, - nekonečno,-0.0) se zpracovávají podle specifikace IEEE 754. Například `x != x` vyhodnotí jako **true** Pokud x má NaN. S plovoucí desetinnou čárkou *staženiny*, tedy strojové instrukce, které kombinují operace s plovoucí desetinnou čárkou, mohou být generovány v rámci **/FP: precise**.

Kompilátor generuje kód určený ke spuštění v [výchozí prostředí s plovoucí desetinnou čárkou](#the-default-floating-point-environment) a předpokládá, že není prostředí s plovoucí desetinnou čárkou otevřeny nebo upraveny za běhu. To znamená předpokládá, že kód není odmaskování výjimek s plovoucí desetinnou čárkou, číst nebo zapisovat stav s plovoucí desetinnou čárkou registry nebo změnit režimech zaokrouhlení.

Pokud váš kód s plovoucí desetinnou čárkou není závislý v řádu operace a výrazů s plovoucí desetinnou čárkou příkazy (např. Pokud vám nezáleží, jestli `a * b + a * c` je vypočítán jako `(b + c) * a` nebo `2 * a` jako `a + a`), vezměte v úvahu [Fast](#fast) možnost, která můžete vytvářet kód rychlejší a efektivnější. Pokud váš kód jak závisí v řádu operace a výrazy a přistupuje k nebo mění s plovoucí desetinnou čárkou prostředí (například ke změně režimu zaokrouhlování nebo zachycují výjimky s plovoucí desetinnou čárkou), použijte [/FP: strict](#strict).

#### <a name="strict"></a>přísné

**/ FP: strict** něhož je chování podobný **/FP: precise**, to znamená, kompilátor zachovává pořadí zdroje a vlastnosti zaokrouhlení s plovoucí desetinnou čárkou kódu, když ji vygeneruje a optimalizuje objektový kód pro cílový počítač a dodržuje standardní při zpracování speciálními hodnotami. Kromě toho může program bezpečně přistupovat k nebo upravit s plovoucí desetinnou čárkou prostředí za běhu.

V části **/FP: strict**, kompilátor generuje kód, který umožňuje program bezpečně odmaskování výjimek s plovoucí desetinnou čárkou, číst nebo zapisovat stav s plovoucí desetinnou čárkou registry nebo změnit režimech zaokrouhlení. Zaokrouhlí na přesnost zdrojového kódu na čtyři konkrétní body při vyhodnocení výrazu: v přiřazeních na zaokrouhlovat, když volání funkce je předán jako argument s plovoucí desetinnou čárkou a při hodnotu s plovoucí desetinnou čárkou je vrácená z volání funkce. Zprostředkující výpočty mohou být provedeny v počítači přesnosti. Zaokrouhlovat lze explicitně zaokrouhlit zprostředkující výpočty. Kompilátor neprovádí algebraických transformace výrazů s plovoucí desetinnou čárkou, jako je například opětovné přiřazení nebo distribuce, pokud je zaručeno, že transformace bitový identické výsledkem. Výrazy, které se týkají zvláštní hodnoty (NaN, + nekonečno, - nekonečno,-0.0) se zpracovávají podle specifikace IEEE 754. Například `x != x` vyhodnotí jako **true** Pokud x má NaN. S plovoucí desetinnou čárkou staženiny nejsou generovány v **/FP: strict**.

**/ FP: strict** je výpočetně dražší než **/FP: precise** vzhledem k tomu, že kompilátor musíte vložit další pokyny k zachycení výjimky a povolit programy pro prostředí s plovoucí desetinnou čárkou na upravit nebo přistoupit k modul runtime. Pokud váš kód nepoužívá tato funkce, ale vyžaduje řazení zdrojový kód a zaokrouhlení nebo závisí na zvláštní hodnoty, použijte **/FP: precise**. V opačném případě zvažte použití **Fast**, který může vytvořit rychlejší a menší kód.

#### <a name="fast"></a>Rychlé

**Fast** možnost umožňuje kompilátoru změnit pořadí, kombinovat nebo zjednodušují operace s plovoucí desetinnou čárkou k optimalizaci plovoucí desetinné čárky kód rychlost a místa. Kompilátor může vynechat zaokrouhlení přiřazovací příkazy, zaokrouhlovat nebo volání funkce. Může změnit pořadí operací nebo provádět algebraické transformace, například pomocí asociativních a distributivních zákony, i v případě, že takové transformace za následek viditelně různé chování se zaokrouhlováním. Z důvodu tyto rozšířené optimalizace výsledek některé výpočtů s plovoucí desetinnou čárkou mohou lišit od těch vytvořené pomocí jiných **/FP** možnosti. Zvláštní hodnoty (NaN, + nekonečno, - nekonečno,-0.0) nemusí být rozšířena nebo chovat přesně podle standardu IEEE 754. V části mohou být generovány s plovoucí desetinnou čárkou staženiny **Fast**. Kompilátor je stále vázané základní architektuře v rámci **Fast**, a další optimalizace může být k dispozici prostřednictvím použití [/arch](arch-minimum-cpu-architecture.md) možnost.

V části **Fast**, kompilátor generuje kód určený ke spuštění ve výchozím prostředí s plovoucí desetinnou čárkou a předpokládá, že není prostředí s plovoucí desetinnou čárkou otevřeny nebo upraveny za běhu. To znamená předpokládá, že kód není odmaskování výjimek s plovoucí desetinnou čárkou, číst nebo zapisovat stav s plovoucí desetinnou čárkou registry nebo změnit režimech zaokrouhlení.

**Fast** je určená pro programy, které nevyžadují řazení přísné zdrojový kód a zaokrouhlení výrazů s plovoucí desetinnou čárkou a nespoléhejte na standardní pravidla pro zpracování speciálními hodnotami, jako je například NaN. Pokud váš kód s plovoucí desetinnou čárkou a zachovávání s rozlišením zdrojového kódu, řazení a zaokrouhlení vyžaduje nebo závisí na standardní chování speciálními hodnotami, použijte [/FP: precise](#precise). Pokud váš kód přistupuje k nebo upraví prostředí s plovoucí desetinnou čárkou ke změně režimu zaokrouhlování, odmaskování výjimek s plovoucí desetinnou čárkou, nebo zkontrolujte stav s plovoucí desetinnou čárkou, použijte [/FP: strict](#strict).

#### <a name="except"></a>S výjimkou

**/FP: except** možnost generuje kód, který zajistí, že všechny nemaskované výjimky s plovoucí desetinnou čárkou jsou vyvolány v okamžiku, kdy k nim dojde, a že žádné další výjimky s plovoucí desetinnou čárkou jsou vyvolány. Ve výchozím nastavení **/FP: strict** možnost umožňuje **/FP: s výjimkou**, a **/FP: precise** tak není. **/FP: except** možnost není kompatibilní s **Fast**. Možnost může být explicitně zakázány podle nás z **/FP: except-**.

Všimněte si, že **/FP: except** nepovolí všechny výjimky s plovoucí desetinnou čárkou samostatně, ale je vyžadováno pro programy povolit výjimky plovoucí desetinné čárky. Zobrazit [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) informace o tom, jak povolit výjimky plovoucí desetinné čárky.

## <a name="remarks"></a>Poznámky

Více **/FP** možnosti lze zadat na stejném příkazovém řádku kompilátoru. Pouze jeden z **/FP: strict**, **Fast**, a **/FP: precise** možnosti mohou být v platnosti v čase. Pokud na příkazovém řádku je zadán více než jednu z těchto možností, má přednost před pozdější možnost a kompilátor vygeneruje upozornění. **/FP: strict** a **/FP: except** možnosti nejsou kompatibilní s **/CLR**.

[/Za](za-ze-disable-language-extensions.md) (Kompatibilita s ANSI) možnost není kompatibilní s **/FP**.

### <a name="using-pragmas-to-control-floating-point-behavior"></a>Pomocí direktivy pragma pro řízení chování plovoucí desetinné čárky

Kompilátor poskytuje tři direktivy pragma přepsat chování plovoucí desetinné čárky, který je zadán v příkazovém řádku: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md), a [fp_contract](../../preprocessor/fp-contract.md). Direktivy pragma můžete řídit chování plovoucí desetinné čárky na úrovni funkcí, není ve funkci. Všimněte si, že direktivy pragma neodpovídají přímo **/FP** možnosti. Tato tabulka ukazuje, jak **/FP** možnosti a direktivy pragma se mapují k sobě navzájem. Další informace najdete v dokumentaci pro jednotlivé možnosti a direktivy pragma.

||float_control(Precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|**Fast**|vypnuto|vypnuto|vypnuto|on|
|**/ FP: precise**|on|vypnuto|vypnuto|on|
|**/ FP: strict**|on|on|on|vypnuto|

### <a name="the-default-floating-point-environment"></a>Výchozí prostředí s plovoucí desetinnou čárkou bodu

Při inicializaci procesu *výchozí číslo s plovoucí čárkou bodu prostředí* nastavena. Toto prostředí zakrývá všechny plovoucí výjimky, nastaví režim zaokrouhlit na nejbližší (`FE_TONEAREST`), zachová subnormal (denormal) hodnoty, použije výchozí přesnost mantisy (mantisa) pro **float**, **double**, a **long double** hodnoty a pokud je podporováno, nastaví na výchozí režim nastavená na affine ovládací prvek nekonečno.

### <a name="floating-point-environment-access-and-modification"></a>Přístup k prostředí s plovoucí desetinnou čárkou a úpravy

Modul runtime Microsoft Visual C++ poskytuje několik funkcí pro přístup a úpravy prostředí s plovoucí desetinnou čárkou. Patří mezi ně [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp –](../../c-runtime-library/reference/clear87-clearfp.md), a [_statusfp –](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) a jejich variant. K zajištění chování programu při váš kód přistupuje k nebo upraví s plovoucí desetinnou čárkou prostředí `fenv_access` musí být povolena, buď pomocí **/FP: strict** možnost nebo použije `fenv_access` direktivu pragma pro tyto funkce k Máte žádný efekt. Když `fenv_access` není povolen přístup nebo úpravu prostředí s plovoucí desetinnou čárkou může vést k neočekávanému chování programu: nemusí kód vyhovět požadované změny v prostředí s plovoucí desetinnou čárkou; nemusí hlásit stav s plovoucí desetinnou čárkou registrů aktuální nebo očekávaných výsledků; a neočekávané výjimky s plovoucí desetinnou čárkou může dojít, nebo nelze provádět očekávané výjimky s plovoucí desetinnou čárkou.

Pokud váš kód přistupuje k nebo upraví s plovoucí desetinnou čárkou prostředí, musíte být opatrní při kombinování kódu kde `fenv_access` je povolené s kódem, který nemá `fenv_access` povolena. V kódu kde `fenv_access` není povolené, kompilátor předpokládá, platformu výchozí prostředí s plovoucí desetinnou čárkou je aktivní a že není otevřeny nebo upraveny stav s plovoucí desetinnou čárkou. Doporučujeme uložit a obnovit do výchozího stavu místní prostředí s plovoucí desetinnou čárkou, před ovládací prvek bude převeden na funkci, která nemá `fenv_access` povolena. Tento příklad ukazuje, jak `float_control` – Direktiva pragma je možné nastavit a obnovit:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Zaokrouhlení s plovoucí desetinnou čárkou režimy

V obou **/FP: precise** a **Fast** kompilátor generuje kód určený ke spuštění ve výchozím prostředí s plovoucí desetinnou čárkou a předpokládá, že prostředí není otevřeny nebo upraveny za běhu. To znamená předpokládá, že kód není odmaskování výjimek s plovoucí desetinnou čárkou, číst nebo zapisovat stav s plovoucí desetinnou čárkou registry nebo změnit režimech zaokrouhlení.  Některé programy však zapotřebí změnit prostředí s plovoucí desetinnou čárkou. Tato ukázka například vypočítá hranice chyba s plovoucí desetinnou čárkou násobení změnou zaokrouhlení s plovoucí desetinnou čárkou režimů:

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

Protože kompilátor předpokládá výchozí hodnota s plovoucí desetinnou čárkou bodu prostředí v rámci **Fast** a **/FP: precise** je zdarma pro ignorování volání `_controlfp_s`. Například při kompilaci pomocí **/O2** a **/FP: precise** pro x86 architektury, nejsou vypočítané hranice a vypíše ukázkový program:

```Output
cLower = -inf
cUpper = -inf
```

Při kompilaci s oběma **/O2** a **/FP: strict** pro x86 architektury, ukázkový program výstupy:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Speciální hodnoty s plovoucí desetinnou čárkou

V části **/FP: precise** a **/FP: strict**, výrazy, které se týkají zvláštní hodnoty (NaN, + nekonečno, - nekonečno,-0.0) se chovají podle specifikace IEEE 754. V části **Fast**, chování tyto speciální hodnoty mohou být konzistentní s IEEE 754.

Tento příklad ukazuje různé chování zvláštní hodnoty v rámci **/FP: precise**, **/FP: strict** a **Fast**:

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

Při kompilaci s **/O2** **/FP: precise** nebo **/O2** **/FP: strict** pro x86 architektury, výstupy jsou konzistentní s IEEE 754 specifikace:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Při kompilaci s **/O2** **Fast** pro x86 architektury, výstupy nejsou konzistentní s IEEE 754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>S plovoucí desetinnou čárkou algebraických transformace

V části **/FP: precise** a **/FP: strict**, kompilátor neprovede matematické transformace, pokud je zaručeno, že transformace bitový identické výsledkem. Kompilátor může provádět takové transformace v části **Fast**. Například výraz `a * b + a * c` v ukázkové funkce `algebraic_transformation` může být zkompilovány do `a * (b + c)` pod **Fast**. Takové transformace, neprovedou se v rámci **/FP: precise** nebo **/FP: strict**, a kompilátor generuje `a * b + a * c`.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Bodů s plovoucí desetinnou čárkou explicitní přetypování

V části **/FP: precise** a **/FP: strict**, kompilátor zaokrouhlí na přesnost zdrojového kódu na čtyři konkrétní body při vyhodnocení výrazu: v přiřazeních na zaokrouhlovat při argumentem s plovoucí desetinnou čárkou je předán do volání funkce a volání funkce vrátí hodnotu s plovoucí desetinnou čárkou. Zaokrouhlovat lze explicitně zaokrouhlit zprostředkující výpočty. V části **Fast**, kompilátor negeneruje explicitní přetypování v těchto bodech zaručit přesnost zdrojového kódu. Tento příklad ukazuje chování v rámci různých **/FP** možnosti:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Při kompilaci pomocí **/O2** **/FP: precise** nebo **/O2** **/FP: strict**, uvidíte, že jsou na obou vložen přetypování explicitních typů zadání a na funkce vrátí bod v generovaném kódu pro x64 architektury:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

V části **/O2** **Fast** generovaný kód zjednodušen, protože všechny přetypování typu jsou optimalizovány:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **generování kódu** stránku vlastností.

1. Upravit **Model plovoucí desetinné čárky** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Optimalizace plovoucí bodu MSVC](floating-point-optimization.md)<br/>
