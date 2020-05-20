---
title: Vítejte zpátky do C++ – moderní C++
description: Popisuje nové programové idiomy v moderním jazyce C++ a jejich racionální.
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 76ac17e71368cdeee669b98505778838ef0dfee7
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550794"
---
# <a name="welcome-back-to-c---modern-c"></a>Vítejte zpátky do C++ – moderní C++

Od jejího vytvoření se C++ stane jedním z nejčastěji používaných programovacích jazyků na světě. Dobře napsané programy C++ jsou rychlé a efektivní. Jazyk je flexibilnější než jiné jazyky: může pracovat na nejvyšší úrovni abstrakce a snížit úroveň na úrovni silikonu. Jazyk C++ poskytuje vysoce optimalizované standardní knihovny. Umožňuje přístup k hardwarovým funkcím nižší úrovně, aby se maximalizovala rychlost a minimalizovala nároky na paměť. Pomocí jazyka C++ můžete vytvořit široké spektrum aplikací. Hry, ovladače zařízení a vysoce výkonný vědecký software. Vložené programy. Klientské aplikace pro Windows. I knihovny a kompilátory pro jiné programovací jazyky se napíší v jazyce C++.

Jeden z původních požadavků pro C++ byl zpětně kompatibilní s jazykem C. V důsledku toho jazyk C++ vždy povolil programování ve stylu jazyka C s nezpracovanými ukazateli, poli, řetězci znaků zakončenými hodnotou null a dalšími funkcemi. Můžou umožňovat skvělý výkon, ale můžou taky zamezit chyby a složitost. Vývoj v jazyce C++ obsahuje zvýrazněné funkce, které významně omezují nutnost použití idiomy ve stylu jazyka C. Stará zařízení pro programování v jazyce C jsou tam, kde je potřebujete, ale s moderním kódem jazyka C++ byste je měli potřebovat méně a méně. Moderní kód C++ je jednodušší, bezpečnější, pružnější a stále stejně rychle.

Následující části obsahují přehled hlavních funkcí moderního C++. Pokud není uvedeno jinak, funkce uvedené zde jsou k dispozici v jazyce C++ 11 a novějším. V kompilátoru jazyka Microsoft C++ můžete nastavit [`/std`](../build/reference/std-specify-language-standard-version.md) možnost kompilátoru a určit tak verzi standardu, která má být použita pro váš projekt.

## <a name="resources-and-smart-pointers"></a>Prostředky a inteligentní ukazatele

Jedna z hlavních tříd chyb v programování ve stylu jazyka C je *nevracení paměti*. Nevracení jsou často způsobena selháním volání **`delete`** paměti, která byla přidělena pomocí **`new`** . Moderní jazyk C++ zvýrazňuje princip *získání prostředků je inicializace* (RAII). Nápad je jednoduchý. Prostředky (paměť haldy, popisovače souborů, sokety atd.) by měly být *vlastněny* objektem. Tento objekt vytvoří nebo přijme nově přidělený prostředek ve svém konstruktoru a odstraní ho v jeho destruktoru. Princip RAII zaručuje, že všechny prostředky se správně vrátí do operačního systému, když se vlastnící objekt dostane mimo rozsah.

Pro podporu snadného přijetí principů RAII poskytuje standardní knihovna C++ tři typy inteligentních ukazatelů: [`std::unique_ptr`](../standard-library/unique-ptr-class.md) , [`std::shared_ptr`](../standard-library/shared-ptr-class.md) a [`std::weak_ptr`](../standard-library/weak-ptr-class.md) . Inteligentní ukazatel zpracovává přidělování a odstraňování paměti, kterou vlastní. Následující příklad ukazuje třídu s členem pole, který je přidělen na haldě v volání `make_unique()` . Volání **`new`** a **`delete`** jsou zapouzdřena `unique_ptr` třídou. Když dojde k `widget` přemístění objektu mimo rozsah, vyvolá se destruktor unique_ptr a uvolní se paměť, která byla přidělena poli.  

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

Pokud je to možné, při přidělování paměti haldy použijte inteligentní ukazatel. Pokud je nutné použít operátory New a DELETE explicitně, postupujte podle principu RAII. Další informace najdete v tématu [životnost objektů a Správa prostředků (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>`std::string` a `std::string_view`

Řetězce ve stylu C jsou další hlavní zdrojem chyb. Pomocí [ `std::string` a `std::wstring` ](../standard-library/basic-string-class.md)můžete eliminovat prakticky všechny chyby spojené s řetězci ve stylu jazyka C. Získáte také výhody členských funkcí pro hledání, připojení, předčekání a tak dále. Obě jsou vysoce optimalizované pro rychlost. Při předávání řetězce do funkce, která vyžaduje pouze přístup jen pro čtení, v C++ 17 můžete použít [`std::string_view`](../standard-library/basic-string-view-class.md) pro ještě vyšší výhody výkonu.

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector`a další kontejnery standardní knihovny

Všechny standardní kontejnery knihovny se řídí principem RAII. Poskytují iterátory pro bezpečný průchod prvků. A jsou vysoce optimalizované pro výkon a byly důkladně testovány na správnost. Pomocí těchto kontejnerů Eliminujte potenciální chyby nebo neefektivitu, které mohou být zavedeny ve vlastních datových strukturách. Místo nezpracovaných polí použijte [`vector`](../standard-library/vector-class.md) jako sekvenční kontejner v jazyce C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Použijte [`map`](../standard-library/map-class.md) (ne `unordered_map` ) jako výchozí asociativní kontejner. Použijte [`set`](../standard-library/set-class.md) , [`multimap`](../standard-library/multimap-class.md) a [`multiset`](../standard-library/multiset-class.md) pro vygenerování a více případů.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Když je potřeba optimalizace výkonu, zvažte použití:

- [`array`](../standard-library/array-class-stl.md)Typ, pokud je vkládání důležité, například jako člen třídy.

- Neuspořádané asociativní kontejnery, například [`unordered_map`](../standard-library/unordered-map-class.md) . Ty mají nižší režijní náklady na prvky a vyhledávání v čase, ale mohou být těžší používat správně a efektivně.

- Seřazeno `vector` . Další informace najdete v tématu [algoritmy](../cpp/algorithms-modern-cpp.md).

Nepoužívejte pole ve stylu jazyka C. U starších rozhraní API, která potřebují přímý přístup k datům, použijte místo toho přístupové metody, jako je například `f(vec.data(), vec.size());` . Další informace o kontejnerech naleznete v tématu [kontejnery knihovny Standard C++](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Standardní algoritmy knihovny

Než se rozhodnete, že pro svůj program potřebujete napsat vlastní algoritmus, nejdříve si přečtěte standardní [algoritmy](../standard-library/algorithm.md)knihovny C++. Standardní knihovna obsahuje stále rostoucí sortiment algoritmů pro mnoho běžných operací, jako je hledání, řazení, filtrování a náhodné provádění. Knihovna Math je rozsáhlá. Počínaje C++ 17 jsou k dispozici paralelní verze mnoha algoritmů.

Tady jsou některé důležité příklady:

- `for_each`, výchozí přenosový algoritmus (spolu s cykly založenými na rozsahu `for` ).

- `transform`, pro nemístní úpravu prvků kontejneru

- `find_if`, výchozí algoritmus pro hledání.

- `sort`, `lower_bound` a ostatní výchozí algoritmy pro řazení a vyhledávání.

Chcete-li napsat komparátor, použijte striktní **`<`** a použijte *pojmenované výrazy lambda* , když můžete.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>`auto`místo explicitních typů názvů

Jazyk c++ 11 představil [`auto`](auto-cpp.md) klíčové slovo pro použití v deklaracích proměnných, funkcí a šablon. **`auto`** instruuje kompilátor, aby odvodit typ objektu, takže nemusíte ho explicitně zadávat. **`auto`** je zvláště užitečné, pokud je odvozený typ vnořenou šablonou:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Cykly založené na rozsahu `for`

Iterace ve stylu jazyka C nad poli a kontejnery je náchylná k chybám indexování a je také únavné na typ. Chcete-li odstranit tyto chyby a čitelnější kód, použijte cykly založené na rozsahu `for` se standardními kontejnery knihoven a nezpracovanými poli. Další informace naleznete v tématu [ `for` příkaz založený na rozsahu](../cpp/range-based-for-statement-cpp.md).

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

## <a name="constexpr-expressions-instead-of-macros"></a>`constexpr`výrazy namísto maker

Makra v jazyce C a C++ jsou tokeny, které preprocesor zpracovává před kompilací. Každá instance tokenu makra je nahrazena definovanou hodnotou nebo výrazem před zkompilováním souboru. Makra jsou běžně používána v programování ve stylu jazyka C k definování konstantních hodnot doby kompilace. Makra jsou ale náchylná k chybám a je obtížné je ladit. V moderním jazyce C++ byste měli preferovat [`constexpr`](constexpr-cpp.md) proměnné pro konstanty v době kompilace:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Jednotná inicializace

V moderním jazyce C++ lze použít inicializaci složené závorky pro libovolný typ. Tato forma inicializace je obzvláště užitečná při inicializaci polí, vektorů nebo jiných kontejnerů. V následujícím příkladu `v2` je inicializován se třemi instancemi `S` . `v3`je inicializován se třemi instancemi `S` , které jsou samy inicializovány pomocí složených závorek. Kompilátor odvodí typ každého prvku na základě deklarovaného typu `v3` .

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

Další informace naleznete v tématu [inicializace složené závorky](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Přesunout sémantiky

Moderní jazyk C++ poskytuje *sémantiku přesunutí*, která umožňuje eliminovat zbytečné kopie paměti. V dřívějších verzích jazyka byly kopie v určitých situacích nenevyhnutelné. Operace *přesunu* převede vlastnictví prostředku z jednoho objektu na další bez vytvoření kopie. Některé třídy vlastní prostředky, jako je například paměť haldy, popisovače souborů a tak dále. Při implementaci třídy vlastnící prostředky můžete definovat *konstruktor přesunutí* a *operátor přiřazení přesunutí* . Kompilátor zvolí tyto speciální členy během řešení přetížení v situacích, kdy není kopie nutná. Standardní typy kontejnerů knihovny vyvolávají konstruktor Move pro objekty, pokud je definována. Další informace najdete v tématech [Přesun konstruktorů a operátory přiřazení přesunutí (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Výrazy lambda

V programování ve stylu jazyka C může být funkce předána do jiné funkce pomocí ukazatele na *funkci*. Ukazatele na funkce jsou nepohodlné, aby je bylo možné udržovat a pochopit. Funkce, na kterou se odkazuje, mohou být definovány jinde ve zdrojovém kódu, od okamžiku, kdy se vyvolala. Nejedná se také o typově bezpečný. Moderní jazyk C++ poskytuje *objekty funkce*, třídy, které přepisují [`operator()`](function-call-operator-parens.md) operátor, což umožňuje jejich volání jako funkce. Nejpohodlnější způsob, jak vytvořit objekty funkce, je pomocí vložených [výrazů lambda](../cpp/lambda-expressions-in-cpp.md). Následující příklad ukazuje, jak použít výraz lambda k předání objektu funkce, který `for_each` funkce vyvolá u každého prvku ve vektoru:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Výraz lambda `[=](int i) { return i > x && i < y; }` lze číst jako funkci, která přijímá jeden argument typu `int` a vrací logickou hodnotu, která označuje, zda je argument větší než `x` a menší než `y` . " Všimněte si, že proměnné `x` a `y` z okolního kontextu lze použít ve výrazu lambda. `[=]`Určuje, že tyto proměnné jsou *zachyceny* hodnotou; jinými slovy, výraz lambda má své vlastní kopie těchto hodnot.

## <a name="exceptions"></a>Výjimky

Moderní jazyk C++ zvýrazňuje výjimky spíše než chybové kódy jako nejlepší způsob, jak hlásit a zpracovávat chybové stavy. Další informace najdete v tématu [moderní osvědčené postupy jazyka C++ pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md).

## `std::atomic`

Použijte strukturu standardní knihovny jazyka C++ [`std::atomic`](../standard-library/atomic-structure.md) a související typy pro komunikační mechanismy mezi vlákny.

## <a name="stdvariant-c17"></a>`std::variant`(C++ 17)

Sjednocení jsou běžně používána v programování ve stylu jazyka C k úspoře paměti tím, že umožňují členům různých typů zabírat stejné umístění v paměti. Sjednocení však nejsou typově bezpečná a jsou náchylná k chybám programování. C++ 17 zavádí [`std::variant`](../standard-library/variant-class.md) třídu jako robustnější a bezpečnou alternativu pro sjednocení. [`std::visit`](../standard-library/variant-functions.md#visit)Funkci lze použít pro přístup k členům `variant` typu typově bezpečným způsobem.

## <a name="see-also"></a>Viz také

[Reference jazyka C++](../cpp/cpp-language-reference.md)\
[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)\
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)\
[Tabulka shody jazyka Microsoft C++](../overview/visual-cpp-language-conformance.md)
