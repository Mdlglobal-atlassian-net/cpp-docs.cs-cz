---
title: /fp (zadání chování hodnot s plovoucí desetinnou čárkou)
ms.date: 11/04/2016
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
ms.openlocfilehash: 8b948edba3244eb22089b2ef5b4c8131736e1fb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452569"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (zadání chování hodnot s plovoucí desetinnou čárkou)

Určuje chování plovoucí desetinné čárky v souboru zdrojového kódu.

## <a name="syntax"></a>Syntaxe

> **/ FP:**[**přesné** | **s výjimkou**[**-**] | **rychlé** | **striktní**]

### <a name="arguments"></a>Arguments

#### <a name="precise"></a>přesné

Výchozí hodnota **/FP** je **/FP: precise**.

**/FP: precise** příznak vylepšuje konzistenci testů plovoucí desetinné čárky pro rovnost a nerovnost zakázáním optimalizací, které by se mohly změnit přesnost výpočtů s plovoucí desetinnou čárkou. (Zachování určité přesnosti se vyžaduje pro striktní dodržování ANSI.) Ve výchozím nastavení, v kódu pro x86 architektury, pokyny k použití x87 koprocesoru, kompilátor používá 80bitové uživatele 80bitové registry k uložení průběžné výsledky výpočtů s plovoucí desetinnou čárkou. To zvyšuje rychlost programu a snižuje jeho velikost. Protože však výpočty zahrnují datové typy s plovoucí desetinnou čárkou reprezentované v paměti méně než 80 bity, může přenos dodatečných bitů přesnosti (80 bitů minus počet bitů v menším typu s plovoucí desetinnou čárkou) napříč delším výpočtem zapříčinit nekonzistentní výsledky.

S **/FP: precise** na x86 procesory, kompilátor provádí zaokrouhlí proměnné typu `float` na správnou přesnost pro přiřazení, přetypování a předání parametrů funkci. Toto zaokrouhlení zaručuje, že si data nezachovají větší platnost, než je kapacita jejich typu. Program zkompilovaný s **/FP: precise** může být pomalejší a větší než zkompilovaný bez **/FP: precise**. **/ FP: precise** zakazuje vnitřní volání; standardní knihovny run-time se místo toho používají rutiny. Další informace najdete v tématu [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md).

Je povoleno následující chování plovoucí desetinné čárky pomocí **/FP: precise**:

- Zkrácení – použití složené operace, která provede pouze jedno zaokrouhlení na konci a nahrazuje více operací.

- Optimalizace výrazů, které jsou neplatné pro zvláštní hodnoty (NaN, +nekonečno, -nekonečno, +0, -0), nejsou povoleny. Optimalizace x-x = > 0, x * 0 = > 0, x-0 = > x, x + 0 = > x a 0-x = > - x jsou z různých důvodů neplatné. (Viz IEEE 754 a standard C99.)

- Kompilátor správně zpracovává porovnání, která zahrnují hodnotu NaN. Například x! = x vyhodnocen **true** Pokud `x` hodnotu NaN a vyvolávají seřazená porovnání s hodnotou NaN vyvolat výjimku.

- Vyhodnocení výrazů dodržuje metodu FLT_EVAL_METHOD=2 standardu C99 s touto výjimkou: pokud je program určen pro procesory x86, považuje se to za přesnost long-double, protože jednotka FPU je nastavena na 53bitovou přesnost.

- Násobení hodnotou přesně 1,0 se transformuje na použití druhého činitele. x * y\*1,0 se transformuje na x\*y. Obdobně x\*1.0\*y se transformuje na x\*y.

- Dělení hodnotou přesně 1,0 se transformuje na použití dělence. x * y/1.0 se transformuje na x\*y. Obdobně x / 1.0\*y se transformuje na x\*y.

Pomocí **/FP: precise** při [fenv_access](../../preprocessor/fenv-access.md) je na zakáže optimalizace, například vyhodnocení za kompilace výrazů s plovoucí desetinnou čárkou. Například, pokud používáte [_control87 _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) ke změně režimu zaokrouhlování a kompilátor provede výpočet s plovoucí desetinnou čárkou, zadaný režim není ve skutečnosti není-li `fenv_access`nastavená na ON.

**/ FP: precise** nahradí **/Op** – možnost kompilátoru.

#### <a name="fast"></a>Rychlé

**Fast** možnost vytvoří nejrychlejší kód zmírněním pravidel pro optimalizaci operací s plovoucí desetinnou čárkou ve většině případů. To umožňuje, aby kompilátor optimalizoval kód výpočtů s plovoucí desetinnou čárkou na rychlost na úkor přesnosti a správnosti. Když **Fast** není zadán, kompilátor nemusí správně zaokrouhlovat přiřazovací příkazy, zaokrouhlovat nebo volání funkcí a nemusí provádět zaokrouhlování přechodných výrazů. Kompilátor může změnit pořadí operací nebo provádět algebraické transformace – například dodržováním asociativních a distributivních pravidel – bez ohledu na vliv na konečnou přesnost výsledků. Kompilátor může operace a operandy změnit na jednoduchou přesnost a nemusí dodržovat pravidla povyšování typů jazyka C++. Optimalizace plovoucí desetinnou konkrétní zkracování jsou vždy povoleny ([fp_contract](../../preprocessor/fp-contract.md) nastavená na ON). Výjimky plovoucí desetinné čárky a přístup k prostředí FPU jsou zakázány (**/FP: except-** předpokládá a [fenv_access](../../preprocessor/fenv-access.md) je VYPNUTÝ).

**Fast** nelze použít s **/FP: strict** nebo **/FP: precise**. Použije se poslední parametr zadaný na příkazovém řádku. Zadání **Fast** a **/FP: except** vygeneruje chybu kompilátoru.

Určení [/Za, /Ze (zakázat jazyková rozšíření)](../../build/reference/za-ze-disable-language-extensions.md) (Kompatibilita s ANSI) a **Fast** může způsobit neočekávané chování. Například operace s plovoucí desetinnou čárkou s jednoduchou přesností nemusejí být zaokrouhleny na jednoduchou přesnost.

#### <a name="except"></a>S výjimkou

**/FP: except** možnost povolí modelu reliable výjimky s plovoucí desetinnou čárkou. Výjimky jsou vyvolány okamžitě po aktivaci. Tento parametr je standardně vypnutý. Připojením znaménka minus možnosti (**/FP: except-**) explicitně zakáže.

#### <a name="strict"></a>přísné

**/FP: strict** možnost povolí nejpřísnější model plovoucí desetinné čárky. **/ FP: strict** způsobí, že [fp_contract](../../preprocessor/fp-contract.md) na vypnuto a [fenv_access](../../preprocessor/fenv-access.md) na zapnuto. **/ FP: except** předpokládá se lze zakázat explicitním zadáním **/FP: except-**. Při použití s **/FP: except-**, **/FP: strict** Vynutí striktní sémantiku plovoucí desetinné čárky, ale bez respektování výjimečných událostí.

## <a name="remarks"></a>Poznámky

Více **/FP** možnosti lze zadat ve stejné kompilaci.

Řízení chování plovoucí desetinné čárky pomocí funkce, najdete v článku [float_control](../../preprocessor/float-control.md) direktivy pragma. Přepíše se tím požadavek **/FP** nastavení kompilátoru. Podle osvědčené technické praxe doporučujeme uložit a obnovit místní chování výpočtů s plovoucí desetinnou čárkou:

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

Většina optimalizací plovoucí desetinné čárky související s **/FP: strict**, **/FP: except** (a jejich odpovídajících pragmat) a `fp_contract` – Direktiva pragma jsou závislé na počítači. **/ FP: strict** a **/FP: except** nejsou kompatibilní s **/CLR**.

**/ FP: precise** by měl řešit většinu požadavků aplikace s plovoucí desetinnou čárkou. Můžete použít **/FP: except** a **/FP: strict**, ale může být určitému snížení výkonu. Pokud je nejdůležitější výkon, zvažte, jestli se má použít **Fast**.

**/ FP: strict**, **Fast**, a **/FP: precise** jsou režimy přesnosti (správnosti). Současně může být aktivní pouze jeden. Pokud mají oba **/FP: strict** a **/FP: precise** nejsou zadány, kterou kompilátor používá ten, který je zpracován jako poslední. Obě **/FP: strict** a **Fast** nelze zadat.

Další informace najdete v tématu [Microsoft Visual C++ optimalizace plovoucí desetinné čárky](floating-point-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** > **C/C++** > **generování kódu** stránku vlastností.

1. Upravit **Model plovoucí desetinné čárky** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru](compiler-options.md)
- [Nastavení možností kompilátoru](setting-compiler-options.md)
- [Microsoft Visual C++ optimalizace plovoucí desetinné čárky](floating-point-optimization.md)