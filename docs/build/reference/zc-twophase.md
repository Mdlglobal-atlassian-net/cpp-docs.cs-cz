---
title: /Zc:twoPhase- (zakázání dvoufázového vyhledávání názvů)
description: 'Vysvětluje, jak/Zc: twoPhase-vypne vyhledávání názvů se dvěma fázemi, pokud je zadaná/Permissive-.'
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: a2ede9f0875bf718d63361201cf8923666078f7a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856953"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase- (zakázání dvoufázového vyhledávání názvů)

Parametr **/Zc: twoPhase-** Option v rámci **/Permissive-** instruuje kompilátor, aby používal původní, nevyhovující chování kompilátoru společnosti Microsoft C++ pro analýzu a vytvoření instance šablon tříd a šablon funkcí.

## <a name="syntax"></a>Syntaxe

> **/Zc:twoPhase-**

## <a name="remarks"></a>Poznámky

Visual Studio 2017 verze 15,3 a novější: v části [/Permissive-](permissive-standards-conformance.md)kompilátor používá pro překlad názvu šablony dvoufázové vyhledávání názvů. Pokud zadáte také parametr **/Zc: twoPhase-** , kompilátor vrátí na předchozí šablonu třídy, která není v souladu s nevyhovujícím způsobem, a rozlišení názvu šablony funkce a chování při nahrazování. Pokud není zadán parametr **/Permissive-** , jedná se o výchozí chování, které nevyhovuje.

Soubory hlaviček Windows SDK ve verzi 10.0.15063.0 (Creators Update nebo RS2) a starší nefungují v režimu shody. Parametr **/Zc: twoPhase-** je vyžadován pro zkompilování kódu pro tyto verze sady SDK při použití **/Permissive-** . Verze Windows SDK počínaje verzí 10.0.15254.0 (v případě, že jsou Creators Update nebo RS3) fungují správně v režimu shody. Nevyžadují parametr **/Zc: twoPhase-** Option.

Použijte parametr **/Zc: twoPhase –** Pokud váš kód vyžaduje správné kompilování starého chování. Důrazně zvažte aktualizaci kódu tak, aby odpovídal standardu.

### <a name="compiler-behavior-under-zctwophase-"></a>Chování kompilátoru v rámci/Zc: twoPhase-

Ve výchozím nastavení nebo v aplikaci Visual Studio 2017 verze 15,3 a novější, pokud zadáte obě **/Permissive-** a **/Zc: twoPhase –** kompilátor použije toto chování:

- Analyzuje pouze deklaraci šablony, záhlaví třídy a seznam základních tříd. Tělo šablony je zachyceno jako datový proud tokenu. Nejsou analyzovány žádné tělo funkce, inicializátory, výchozí argumenty nebo s výjimkou argumentů. Šablona třídy je pseudo instance pro nezávazně typu pro ověření, že deklarace v šabloně třídy jsou správné. Zvažte tuto šablonu třídy:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Deklarace šablony, `template <typename T>`, hlavní `class Derived`třídy a `public Base<T>` seznamu základní třídy jsou analyzovány, ale tělo šablony je zachyceno jako datový proud tokenu.

- Při analýze šablony funkce kompilátor analyzuje pouze signaturu funkce. Tělo funkce se nikdy neanalyzuje. Místo toho je zachycena jako datový proud tokenu.

V důsledku toho, pokud tělo šablony obsahuje syntaktické chyby, ale šablona nikdy nezíská instanci, kompilátor nediagnostikuje chyby.

Další vliv tohoto chování je v řešení přetížení. K nestandardnímu chování dochází z důvodu způsobu, jakým je datový proud tokenu rozšířen v lokalitě instance. Symboly, které nebyly viditelné v deklaraci šablony, mohou být viditelné v okamžiku vytvoření instance. To znamená, že se můžou zúčastnit řešení přetížení. Můžete najít chování šablon na základě kódu, který není viditelný v definici šablony, v rozporu se standardem.

Podívejte se například na tento kód:

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

Zde je výstup, když použijete výchozí režim, režim shody a režim souladu s parametrem **/Zc: twoPhase-** Compiler:

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

Při kompilaci v režimu zobrazení v **/Permissive-** tento program vytiskne "`Standard two-phase`", protože druhé přetížení `func` není viditelné, když kompilátor dosáhne šablony. Pokud přidáte parametr **/Zc: twoPhase-** , program vytiskne "`Microsoft one-phase`". Výstup je stejný, jako když nezadáte **/Permissive-** .

*Závislé názvy* jsou názvy, které jsou závislé na parametru šablony. Tyto názvy mají chování vyhledávání, které se také liší v části **/Zc: twoPhase-** . V režimu shody nejsou závislé názvy vázány na místo definice šablony. Místo toho je kompilátor při vytváření instance šablony vyhledává. U volání funkcí s názvem závislé funkce se název bude vázat na funkce viditelné na webu volání v definici šablony. Další přetížení z vyhledávání závislého na argumentu jsou přidána v místě definice šablony a v bodě vytvoření instance šablony.

Dvoufázové vyhledávání se skládá ze dvou částí: vyhledávání nezávislých názvů během definice šablony a vyhledávání závislých názvů během vytváření instance šablony. V části **/Zc: twoPhase –** kompilátor nepoužívá vyhledávání závislé na argumentech nezávisle na nekvalifikovaném vyhledávání. To znamená, že neprovádí dvoustupňové vyhledávání, takže výsledky Rozlišení přetěžování se mohou lišit.

Tady je další příklad:

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

Při kompilaci bez **/Permissive-** se tento kód vytiskne:

```Output
func(int)
NS::func(NS::S)
```

Při kompilaci s **/Permissive-** , ale bez **/Zc: twoPhase –** tento kód vytiskne:

```Output
func(long)
NS::func(NS::S)
```

Při kompilaci s oběma **/Permissive-** a **/Zc: twoPhase –** tento kód vytiskne:

```Output
func(int)
NS::func(NS::S)
```

V režimu shoda v rámci **/Permissive-** volání `tfunc(1729)` překládá na `void func(long)` přetížení. Nedokáže překládat na přetížení `void func(int)`, jak je uvedeno v části **/Zc: twoPhase-** . Důvodem je, že nekvalifikované `func(int)` jsou deklarovány po definici šablony a nejsou nalezeny prostřednictvím vyhledávání závislého na argumentech. Ale `void func(S)` se účastní vyhledávání závislého na argumentech, takže se přidá do sady přetížení pro volání `tfunc(s)`, a to i v případě, že je deklarována po funkci šablony.

### <a name="update-your-code-for-two-phase-conformance"></a>Aktualizace kódu pro oboustrannou shodu

Starší verze kompilátoru nevyžadují klíčová slova `template` a `typename` všude, C++ kde je standard vyžaduje. Tato klíčová slova jsou potřebná v některých pozicích, aby bylo možné určit, jak by měly kompilátory během první fáze vyhledávání analyzovat závislé názvy. Příklad:

`T::Foo<a || b>(c);`

Vyhovující kompilátor analyzuje `Foo` jako proměnnou v rozsahu `T`, což znamená, že tento kód je logický výraz or s `T::foo < a` jako levý operand a `b > (c)` jako pravý operand. Pokud máte v úmyslu použít `Foo` jako šablonu funkce, je nutné určit, že se jedná o šablonu přidáním klíčového slova `template`:

`T::template Foo<a || b>(c);`

Ve verzích Visual Studio 2017 verze 15,3 a novější, pokud jsou zadány **/Permissive-** a **/Zc: twoPhase-** , kompilátor povolí tento kód bez klíčového slova `template`. Interpretuje kód jako volání šablony funkce s argumentem `a || b`, protože pouze analyzuje šablony pouze omezeným způsobem. Výše uvedený kód není v první fázi analyzován vůbec. Během druhé fáze je dostatek kontextu pro sdělení, že `T::Foo` je šablonou spíše než proměnnou, takže kompilátor vynutil použití klíčového slova.

Toto chování lze také zobrazit odstraněním klíčového slova `typename` před názvy v části těla šablony funkce, inicializátory, výchozí argumenty a s výjimkou argumentů. Příklad:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Pokud nepoužijete klíčové slovo `typename` v těle funkce, tento kód se zkompiluje v rámci **/Permissive-/Zc: twoPhase-** , ale ne pouze v **/Permissive-** . Klíčové slovo `typename` je požadováno k označení toho, že je `TYPE` závislý. Vzhledem k tomu, že text není analyzován v rámci **/Zc: twoPhase-** , kompilátor does't vyžaduje klíčové slovo. V režimu **/Permissive-** , kód bez klíčového slova `typename` generuje chyby. Chcete-li migrovat kód do shody v aplikaci Visual Studio 2017 verze 15,3 a novější, vložte klíčové slovo `typename` tam, kde chybí.

Podobně zvažte tuto ukázku kódu:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

V části **/Permissive-/Zc: twoPhase-** a ve starších kompilátorech vyžaduje kompilátor pouze klíčové slovo `template` na řádku 2. V režimu shody kompilátor nyní také vyžaduje klíčové slovo `template` na řádku 4, aby označoval, že `T::X<T>` je šablona. Vyhledejte kód, u kterého chybí toto klíčové slovo, a poskytněte mu, aby kód odpovídal standardu.

Další informace o problémech shody naleznete v tématu [ C++ vylepšení shody v aplikaci Visual Studio](../../overview/cpp-conformance-improvements.md) a [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **příkazového řádku** **jazyka C/C++**  > .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala parametr **/Zc: twoPhase-** a pak klikněte na **tlačítko OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
