---
title: /Zc:twoPhase-(zakázání dvoufázového vyhledávání názvů)
ms.date: 03/06/2018
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: 5f990181fd1e606cf9d7dd33242752bed33aa456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315797"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(zakázání dvoufázového vyhledávání názvů)

Když **/Zc:twoPhase-** je zadána možnost, kompilátor analyzuje a vytvoří instanci třídy šablony a funkce nonkonformní stejně jako verze sady Visual Studio před Visual Studio 2017 verze 15.3.

## <a name="syntax"></a>Syntaxe

> **/Zc:twoPhase-**

## <a name="remarks"></a>Poznámky

V sadě Visual Studio 2017 verze 15.3 nebo novější, ve výchozím nastavení používá kompilátor dvoufázové vyhledávání názvů pro překlad názvů šablony. Pokud **/Zc:twoPhase-** není zadán, kompilátor přejde do jeho předchozí nonkonformní třídy šablony a funkce šablony řešení a náhradní chování.

**/Zc:twoPhase-** není ve výchozím nastavení nastavená možnost povolit nonkonformní chování. [/ Permissive-](permissive-standards-conformance.md) možnost implicitně nastaví vyhovující chování kompilátoru dvoufázového vyhledávání, ale lze přepsat pomocí **/Zc:twoPhase-**.

Soubory hlaviček sady Windows SDK ve verzi 10.0.15063.0 (Creators Update nebo Redstone 2) a předchozími verzemi nefungují správně v režim přizpůsobení. Je nutné použít **/Zc:twoPhase-** ke kompilaci kódu pro tyto verze sady SDK při použití sady Visual Studio 2017 verze 15.3 a novějších verzích. Verze sady SDK Windows od verze 10.0.15254.0 (Redstone 3 nebo Fall Creators Update) fungovat správně v režim přizpůsobení a nevyžadují, aby **/Zc:twoPhase-** možnost.

Použití **/Zc:twoPhase-** Pokud váš kód vyžaduje staré chování pro správnou kompilaci. Důkladně zvážit možnost aktualizaci kódu tak, aby odpovídal standardu.

### <a name="compiler-behavior-under-zctwophase-"></a>Chování kompilátoru pod /Zc:twoPhase-

Ve verzích sady Visual Studio 2017 verze 15.3, kompilátor a kdy **/Zc:twoPhase-** není zadán, kompilátor používá toto chování:

- Analyzuje pouze deklarace šablony, hlavní třídy a seznam základních tříd. Šablona textu zaznamená v podobě token datového proudu. Žádné těla funkcí, inicializátory, výchozí argumenty nebo argumenty noexcept jsou analyzovány. Šablona třídy je vytvořena instance pseudo nezávazně typu ověření, že deklarace v šabloně třídy jsou správné. Vezměte v úvahu tuto šablonu třídy:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Deklarace šablony `template <typename T`>, hlavní třída `class Derived`a seznamu základní třídy `public Base<T>` jsou analyzovány, ale text šablony zaznamená v podobě token datového proudu.

- Při analýze šablony funkce, kompilátor analyzuje pouze signatura funkce. Tělo funkce se nikdy analyzovat. Místo toho jsou zachyceny jako token datového proudu.

V důsledku toho pokud text šablony obsahuje chyby syntaxe a nikdy vytvořena instance šablona, chyby se nikdy zjistit.

Jiný vliv tohoto chování je v řešení přetížení. Kvůli způsobu, jakým token datového proudu rozbalen v lokalitě vytváření instancí symboly, které nebyly viditelné v deklaraci šablony mohou být viditelné při vytváření instance a součástí řešení přetížení. To může vést k šablonám, které mění chování v závislosti na kód, který nebyl viditelný, při definování šablony, na rozdíl od standardu.

Podívejte se například na tento kód:

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main()
{
    g(3.14);
}
```

Při kompilaci v rámci **/Zc:twoPhase-**, tento program zobrazí "volání překládá na celé číslo". V režimu shoda v rámci **/ permissive-**, tento program zobrazí "volání přeloží na void *", protože druhé přetížení `func` není viditelný, když kompilátor narazí šablonu.

*Názvy závislých prvků*, názvy, které jsou závislé na parametru šablony mají chování při vyhledávání, které se také liší podle **/Zc:twoPhase-**. V režimu přizpůsobení závislé názvy nejsou vázány Přejme během definice šablony. Místo toho tyto názvy jsou vyhledány při vytváření instance šablony. Pro volání funkce s názvem závislé funkce název je vázán na sadu funkcí, které jsou viditelné v místě volání v definici šablony, jak je uvedeno výše. Další přetížení z vyhledávání závislého na argumentech přidají v bodě definice šablony a místa, ve kterém je vytvořena instance šablony. Dvě fáze dvoufázového vyhledávání vyhledávání pro nezávislé názvy jsou v době definice šablony a vyhledávání nezávislých názvů v době vytváření instancí šablon. V části **/Zc:twoPhase-**, kompilátor neprovádí vyhledávání závislého na argumentech samostatně z běžných, nekvalifikované vyhledávání (to znamená, neumí dvoufázového vyhledávání), takže výsledky řešení přetížení může být jiný.

Tady je další příklad:

```cpp
// zctwophase1.cpp
// Compile by using
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

Při kompilaci bez **/Zc:twoPhase-**, to vytiskne

```Output
func(long)
NS::func(NS::S)
```

Při kompilaci s **/Zc:twoPhase-**, to vytiskne

```Output
func(int)
NS::func(NS::S)
```

V režimu shoda v rámci **/ permissive-**, volání `tfunc(1729)` přeloží na `void func(long)` přetížení není `void func(int)` přetížení podle **/Zc:twoPhase-**, protože neúplný `func(int)` se deklaroval po definici šablony a pomocí vyhledávání závislého na argumentu nebyl nalezen. Ale `void func(S)` účastnit vyhledávání závislého na argumentech, takže se přidá do nastavení pro volání přetížení `tfunc(s)` i v případě, že je deklarována za šablony funkcí.

### <a name="update-your-code-for-two-phase-conformance"></a>Aktualizujte svůj kód pro dvoufázové shody

Starší verze kompilátoru nevyžadují klíčová slova `template` a `typename` všude, kde je vyžaduje Standard jazyka C++. Tato klíčová slova jsou potřeba v některých položek k rozlišení, jak by se měly kompilátory analyzovat závislé jméno během první fáze vyhledávání. Příklad:

`T::Foo<a || b>(c);`

Vyhovující kompilátor analyzuje `Foo` jako proměnné v oboru `T`, takže tento kód je logické- nebo výraz s `T::foo < a` jako levý operand a `b > (c)` jako pravý operand. Pokud jste v úmyslu použít `Foo` jako šablony funkce, je třeba určit, že se jedná šablonu tak, že přidáte `template` – klíčové slovo:

`T::template Foo<a || b>(c);`

Ve verzích před Visual Studio 2017 verze 15.3 a kdy **/Zc:twoPhase-** není zadán, kompilátor umožňuje tento kód bez `template` – klíčové slovo a interpretuje jako volání šablony funkce s argumentem `a || b`, protože analyzuje šablony velmi omezená způsobem. Výše uvedený kód není vůbec analyzovat v první fázi. Ve druhé fázi je dostatečný kontext, který říct `T::Foo` je šablonu, nikoli proměnné, kompilátor nevynucuje použití klíčového slova.

Toto chování je možné také prohlížet odstraněním klíčové slovo `typename` před názvy v těla funkcí šablony, inicializátory, výchozí argumenty a argumenty noexcept. Příklad:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Pokud použijete klíčové slovo `typename` v těle funkce tento kód zkompiluje podle **/Zc:twoPhase-**, ale není v **/ permissive-**. `typename` – Klíčové slovo se vyžaduje k označení, že `TYPE` závisí. Protože obsah není analyzovat podle **/Zc:twoPhase-**, položka hierarchyinfoguid kompilátoru vyžadují klíčového slova. V **/ permissive-** režim přizpůsobení, kód bez `typename` – klíčové slovo generuje chyby. Migrace na Visual Studio 2017 verze 15.3 kódu a dalších fázích můžete využít, Vložit `typename` – klíčové slovo, ve kterém chybí.

Dále doporučujeme, abyste tato ukázka kódu:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

V části **/Zc:twoPhase-** a ve starších kompilátory, kompilátor vyžaduje pouze `template` – klíčové slovo na řádku 2. Ve výchozím nastavení a režim přizpůsobení, kompilátor nyní také vyžaduje `template` – klíčové slovo na řádku 4, která označuje, že `T::X<T>` je šablona. Vyhledejte kód, který neobsahuje toto klíčové slovo a zadat ho tak, aby váš kód se řídí standardem.

Další informace o problémech přizpůsobení najdete v tématu [vylepšení shody C++ v sadě Visual Studio](../../overview/cpp-conformance-improvements.md) a [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc:twoPhase-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
