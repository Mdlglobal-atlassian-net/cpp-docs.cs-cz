---
title: Vítejte zpět v C++ - Moderní C++
description: Popisuje nové programovací idiomy v moderním jazyce C++ a jejich zdůvodnění.
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369492"
---
# <a name="welcome-back-to-c---modern-c"></a>Vítejte zpět v C++ - Moderní C++

Od svého vzniku se C++ stal jedním z nejpoužívanějších programovacích jazyků na světě. Dobře napsané programy C++ jsou rychlé a efektivní. Jazyk je flexibilnější než jiné jazyky: Může pracovat na nejvyššíúrovni abstrakce, a dolů na úrovni křemíku. C++ poskytuje vysoce optimalizované standardní knihovny. Umožňuje přístup k nízkoúrovňovým hardwarovým funkcím, maximalizuje rychlost a minimalizuje požadavky na paměť. Pomocí jazyka C++ můžete vytvořit širokou škálu aplikací. Hry, ovladače zařízení a vysoce výkonný vědecký software. Vložené programy. Klientské aplikace pro Windows. Dokonce i knihovny a kompilátory pro jiné programovací jazyky se napíší v jazyce C++.

Jedním z původních požadavků pro C++ byla zpětná kompatibilita s jazykem C. V důsledku toho C++ má vždy povoleno programování ve stylu C, s nezpracovaná ukazatele, pole, null ukončené řetězce znaků a další funkce. Mohou umožnit skvělý výkon, ale mohou také vyvolat chyby a složitost. Vývoj jazyka C++ zdůraznil funkce, které výrazně snižují potřebu používat idiomy ve stylu C. Staré C-programovací zařízení jsou tam, když je potřebujete, ale s moderním kódem C++ byste je měli potřebovat méně a méně. Moderní kód C++ je jednodušší, bezpečnější, elegantnější a stále stejně rychlý jako vždy.

Následující části poskytují přehled hlavních funkcí moderního jazyka C++. Pokud není uvedeno jinak, zde uvedené funkce jsou k dispozici v jazyce C ++ 11 a novějším. V kompilátoru Microsoft C++ můžete nastavit možnost kompilátoru [/std](../build/reference/std-specify-language-standard-version.md) a určit, kterou verzi standardu použít pro váš projekt.

## <a name="resources-and-smart-pointers"></a>Zdroje a inteligentní ukazatele

Jednou z hlavních tříd chyb v programování ve stylu Jazyka C je *nevracení paměti*. Nevracení jsou často způsobeny selhání volání **odstranit** paměť, která byla přidělena s **new**. Moderní C++ zdůrazňuje princip *získávání prostředků je inicializace* (RAII). Myšlenka je jednoduchá. Prostředky (haldy paměti, popisovače souborů, sokety a tak dále) by měly být *vlastněny* objektem. Tento objekt vytvoří nebo přijme nově přidělený prostředek v jeho konstruktoru a odstraní jej v jeho destruktoru. Princip RAII zaručuje, že všechny prostředky získat správně vráceny do operačního systému, když vlastnící objekt přejde mimo rozsah.

Pro podporu snadného přijetí principů RAII poskytuje standardní knihovna jazyka C++tři typy inteligentních ukazatelů: [std::unique_ptr](../standard-library/unique-ptr-class.md), [std::shared_ptr](../standard-library/shared-ptr-class.md)a [std::weak_ptr](../standard-library/weak-ptr-class.md). Inteligentní ukazatel zpracovává přidělení a odstranění paměti, kterou vlastní. Následující příklad ukazuje třídu s členem pole, který je přidělen `make_unique()`na haldě ve volání . Volání **new** a **delete** jsou zapouzdřeny třídou. `unique_ptr` Když `widget` objekt přejde mimo rozsah, unique_ptr destruktoru bude vyvolána a uvolní paměť, která byla přidělena pro pole.  

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Kdykoli je to možné, použijte inteligentní ukazatel při přidělování paměti haldy. Pokud je nutné použít nové a odstranit operátory explicitně, postupujte podle zásady RAII. Další informace naleznete v [tématu Životnost objektu a správa prostředků (RAII).](object-lifetime-and-resource-management-modern-cpp.md)

## <a name="stdstring-and-stdstring_view"></a>std::řetězec a std::string_view

Řetězce ve stylu C jsou dalším hlavním zdrojem chyb. Pomocí [std::string a std::wstring](../standard-library/basic-string-class.md)můžete eliminovat prakticky všechny chyby spojené s řetězci stylu C. Můžete také získat výhodu členských funkcí pro vyhledávání, připojení, prepending, a tak dále. Oba jsou vysoce optimalizovány pro rychlost. Při předávání řetězce funkci, která vyžaduje pouze přístup jen pro čtení, v jazyce C++ 17 můžete použít [std::string_view](../standard-library/basic-string-view-class.md) pro ještě vyšší výkon.

## <a name="stdvector-and-other-standard-library-containers"></a>std::vektorové a jiné kontejnery standardní knihovny

Standardní knihovna kontejnery všechny postupujte podle principu RAII. Poskytují iterátory pro bezpečné procházení prvků. A jsou vysoce optimalizované pro výkon a byly důkladně testovány na správnost. Pomocí těchto kontejnerů eliminujete potenciál pro chyby nebo neefektivity, které mohou být zavedeny ve vlastních datových strukturách. Místo nezpracovaných polí použijte [vektor](../standard-library/vector-class.md) jako sekvenční kontejner v jazyce C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Jako [map](../standard-library/map-class.md) výchozí `unordered_map`asociativní kontejner použijte mapu (ne). Pro degenerovaný a více případů použijte [sadu](../standard-library/set-class.md), [multimapu](../standard-library/multimap-class.md)a [multiset.](../standard-library/multiset-class.md)

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Pokud je potřeba optimalizace výkonu, zvažte použití:

- Typ [pole](../standard-library/array-class-stl.md) při vkládání je důležité, například jako člen třídy.

- Neuspořádané asociativní kontejnery, například [unordered_map](../standard-library/unordered-map-class.md). Ty mají nižší režii na prvek a vyhledávání v konstantním čase, ale může být obtížnější správně a efektivně používat.

- Seřazeno `vector`. Další informace naleznete v [tématu Algoritmy](../cpp/algorithms-modern-cpp.md).

Nepoužívejte pole ve stylu C. Pro starší rozhraní API, která potřebují přímý přístup k `f(vec.data(), vec.size());` datům, použijte přistupující metody, jako je například místo. Další informace o kontejnerech naleznete v [tématu Kontejnery standardní knihovny jazyka C++](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Standardní algoritmy knihovny

Než budete předpokládat, že je třeba napsat vlastní algoritmus pro váš program, nejprve zkontrolujte algoritmy standardní [knihovny](../standard-library/algorithm.md)C++ . Standardní knihovna obsahuje stále rostoucí sortiment algoritmů pro mnoho běžných operací, jako je vyhledávání, řazení, filtrování a randomizace. Matematická knihovna je rozsáhlá. Počínaje C++ 17 jsou k dispozici paralelní verze mnoha algoritmů.

Zde jsou některé důležité příklady:

- **for_each**, výchozí algoritmus průchodu (spolu s rozsahem založené pro smyčky).

- **transformace**, pro ne-in-place modifikace kontejnerových prvků

- **find_if**, výchozí vyhledávací algoritmus.

- **řazení**, **lower_bound**a další výchozí algoritmy řazení a vyhledávání.

Chcete-li napsat komparátor, použijte přísné **<** a používat pojmenované *lambdas,* když je to možné.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>auto místo explicitních názvů typů

C++ 11 představil [automatické](auto-cpp.md) klíčové slovo pro použití v deklaracích proměnných, funkcí a šablon. **auto** říká kompilátoru odvodit typ objektu, takže není nutné jej explicitně zadávat. **auto** je užitečné zejména v případě, že odvozený typ je vnořená šablona:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Na základě rozsahu smyček

C-style iterace přes pole a kontejnery je náchylný k chybám indexování a je také únavné psát. Chcete-li odstranit tyto chyby a váš kód čitelnější, použijte rozsah na základě smyčky s kontejnery standardní knihovny a nezpracovaná pole. Další informace naleznete v [tématu Range-based for statement](../cpp/range-based-for-statement-cpp.md).

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>constexpr výrazy místo maker

Makra v jazyce C a C++ jsou tokeny, které jsou zpracovány preprocesorem před kompilací. Každá instance tokenu makra je před kompilací souboru nahrazena definovanou hodnotou nebo výrazem. Makra se běžně používají v programování ve stylu Jazyka C k definování konstantních hodnot v době kompilace. Makra jsou však náchylné k chybám a obtížně ladit. V moderním jazyce C++ byste měli upřednostňovat proměnné [constexpr](constexpr-cpp.md) pro konstanty v době kompilace:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Jednotná inicializace

V moderním jazyce C++ můžete použít inicializaci závorky pro libovolný typ. Tato forma inicializace je zvláště vhodná při inicializaci polí, vektorů nebo jiných kontejnerů. V následujícím příkladu `v2` je inicializován `S`se třemi instancemi . `v3`je inicializován se `S` třemi instancemi, které jsou samy inicializovány pomocí závorek. Kompilátor odvodí typ každého prvku na `v3`základě deklarovaného typu .

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

Další informace naleznete v tématu [Inicializace závorky](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Přesunutí sémantiky

Moderní C++ poskytuje *přesunout sémantiku*, které umožňují eliminovat zbytečné paměti kopií. V dřívějších verzích jazyka byly kopie v určitých situacích nevyhnutelné. Operace *přesunutí* převede vlastnictví prostředku z jednoho objektu na druhý bez vytvoření kopie. Při implementaci třídy, která vlastní prostředek (například haldy paměti, popisovače souborů a tak dále), můžete definovat *konstruktor přesunutí* a *přesunout operátor přiřazení* pro něj. Kompilátor zvolí tyto speciální členy během řešení přetížení v situacích, kdy není potřeba kopie. Typy kontejnerů standardní knihovny vyvolávají konstruktor move na objektech, pokud je definován. Další informace naleznete v tématu [Přesunutí konstruktorů a operátorů přiřazení přesunutí (C++).](move-constructors-and-move-assignment-operators-cpp.md)

## <a name="lambda-expressions"></a>Výrazy lambda

V programování ve stylu Jazyka C může být funkce předána jiné funkci pomocí *ukazatele funkce*. Ukazatele funkce jsou nepohodlné udržovat a pochopit. Funkce, na kterou odkazují, může být definována jinde ve zdrojovém kódu, daleko od bodu, ve kterém je vyvolána. A taky nejsou typově bezpečné. Moderní C++ poskytuje *objekty funkce*, třídy, které přepsat [()](function-call-operator-parens.md) operátor, který umožňuje jejich volání jako funkce. Nejpohodlnější způsob, jak vytvořit objekty funkce je s vřádkovými [výrazy lambda](../cpp/lambda-expressions-in-cpp.md). Následující příklad ukazuje, jak použít výraz lambda předat objekt `for_each` funkce, že funkce vyvolá na každý prvek ve vektoru:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Výraz `[=](int i) { return i > x && i < y; }` lambda lze číst jako "funkce, která `int` přebírá jeden argument typu a vrací logickou hodnotu, která označuje, zda je argument větší než `x` a menší než `y`." Všimněte si, `x` `y` že proměnné a z okolního kontextu lze použít v lambda. Určuje, `[=]` že tyto proměnné jsou *zachyceny* hodnotou; jinými slovy, výraz lambda má své vlastní kopie těchto hodnot.

## <a name="exceptions"></a>Výjimky

Moderní C++ zdůrazňuje výjimky spíše než chybové kódy jako nejlepší způsob, jak hlásit a zpracovávat chybové stavy. Další informace naleznete v [tématu Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std::atomic

Použijte standardní knihovnu [C++std::atomic](../standard-library/atomic-structure.md) struct a související typy pro mechanismy komunikace mezi vlákny.

## <a name="stdvariant-c17"></a>std::varianta (C++17)

Sjednocení se běžně používají v programování ve stylu Jazyka C k úspoře paměti tím, že umožňuje členům různých typů obsadit stejné umístění paměti. Sjednocení však nejsou typově bezpečné a jsou náchylné k chybám programování. C++ 17 představuje [třídu std::variant](../standard-library/variant-class.md) jako robustnější a bezpečnější alternativu k sjednocení. [Std::visit](../standard-library/variant-functions.md#visit) funkce lze použít pro přístup `variant` k členy typu způsobem bezpečné.

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)\
[Lambda výrazy](../cpp/lambda-expressions-in-cpp.md)\
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)\
[Tabulka shody jazyků Microsoft C++](../overview/visual-cpp-language-conformance.md)
