---
title: C++ vás vítá zpět (moderní verze jazyka C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 2739da77fbfa973ca716abc6d8fa4920b81095d9
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303331"
---
# <a name="welcome-back-to-c-modern-c"></a>C++ vás vítá zpět (moderní verze jazyka C++)

Za posledních 25 let C++ byl jedním z nejčastěji používaných programovacích jazyků na světě. Dobře zapsané C++ programy jsou rychlé a efektivní. Jazyk je flexibilnější než ostatní jazyky, protože umožňuje přístup k hardwarovým funkcím nižší úrovně, aby se maximalizovala rychlost a minimalizovala nároky na paměť. Můžete ji použít k vytvoření široké škály aplikací – od her, k vysoce výkonnému vědeckému softwaru, ovladačů zařízení, integrovaných programů, knihoven a kompilátorů pro jiné programovací jazyky, klientské aplikace pro Windows a spoustu dalších.

Jeden z původních požadavků pro C++ byl zpětně kompatibilní s jazykem C. V důsledku toho C++ bylo vždy povoleno programování ve stylu jazyka C s nezpracovanými ukazateli, poli, řetězci znaků zakončenými hodnotou null, vlastními datovými strukturami a dalšími funkcemi, které mohou umožňovat skvělý výkon, ale mohou také začínat chyby a složitost. Vývoj nástroje C++ má zdůrazněné funkce, které významně omezují nutnost použití idiomy ve stylu jazyka C. Stará zařízení pro programování v jazyce C jsou tam, kde je potřebujete, ale s C++ moderním kódem byste je měli potřebovat méně a méně. Moderní C++ kód je jednodušší, bezpečnější, pružnější a stále tak rychle jako dřív.

V následujících částech najdete přehled hlavních funkcí moderní C++aplikace. Pokud není uvedeno jinak, funkce uvedené zde jsou k dispozici v jazyce C++ 11 a novějším. V kompilátoru společnosti C++ Microsoft můžete nastavit možnost kompilátoru [/STD](../build/reference/std-specify-language-standard-version.md) a určit tak verzi standardu, která má být použita pro váš projekt.

## <a name="raii-and-smart-pointers"></a>RAII a inteligentní ukazatele

Jedna z hlavních tříd chyb v programování ve stylu jazyka C je *nevracení paměti* z důvodu neúspěšného volání metody **Delete** pro paměť, která byla přidělena **novému**. Moderní C++ zdůraznění principu *získání prostředků je inicializace* , která uvádí, že jakýkoli prostředek (paměť haldy, popisovače souborů, sokety atd.) by měl být *vlastněn* objektem, který vytvoří nebo obdrží nově přidělený prostředek v konstruktoru a odstraní ho v jeho destruktoru. Dodržováním principu RAII zaručujete, že všechny prostředky budou správně vráceny do operačního systému, pokud vlastnící objekt skončí mimo rozsah. Pro podporu snadného přijetí RAIIch principů C++ nabízí standardní knihovna tři typy inteligentních ukazatelů: [std:: unique_ptr](../standard-library/unique-ptr-class.md), [std:: shared_ptr](../standard-library/shared-ptr-class.md)a [std:: weak_ptr](../standard-library/weak-ptr-class.md). Inteligentní ukazatel zpracovává přidělování a odstraňování paměti, kterou vlastní. Následující příklad ukazuje třídu s členem pole, který je přidělena haldě v volání `make_unique()`. Volání **New** a **Delete** jsou zapouzdřena třídou `unique_ptr`. Když se objekt `widget` z oboru, vyvolá se unique_ptr destruktor a uvolní paměť, která byla přidělena poli.  

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

## <a name="stdstring-and-stdstring_view"></a>std:: String a std:: string_view

Řetězce ve stylu C jsou další hlavní zdrojem chyb. Pomocí [std:: String a std:: wstring](../standard-library/basic-string-class.md) můžete eliminovat prakticky všechny chyby spojené s řetězci ve stylu jazyka C a získat výhody členských funkcí pro hledání, připojení, předčekání a tak dále. Obě jsou vysoce optimalizované pro rychlost. Při předávání řetězce do funkce, která vyžaduje pouze přístup jen pro čtení, v (C++ 17) můžete použít [std:: string_view](../standard-library/basic-string-view-class.md) pro ještě vyšší výhody výkonu.

## <a name="stdvector-and-other-standard-library-containers"></a>std:: Vector a jiné standardní kontejnery knihovny

Standardní kontejnery knihovny jsou všechny podle principu RAII, poskytují iterátory pro bezpečný průchod prvků, jsou vysoce optimalizované pro výkon a byly důkladně testovány na správnost. Pokud je to možné, Eliminujte případné chyby nebo neefektivitu, které by mohly být zavedeny ve vlastních datových strukturách, pomocí těchto kontejnerů. Ve výchozím nastavení použijte [Vector](../standard-library/vector-class.md) jako preferovaný sekvenční kontejner v C++. Jedná se o ekvivalent `List<T>` v jazycích .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Použijte [mapu](../standard-library/map-class.md) (ne `unordered_map`) jako výchozí asociativní kontejner. Použijte [set](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md)a [multiset](../standard-library/multiset-class.md) pro regeneraci a více případů.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Když je potřeba optimalizace výkonu, zvažte použití:

- Typ [pole](../standard-library/array-class-stl.md) , když je vkládání důležité, například jako člen třídy.

- Neuspořádané asociativní kontejnery, například [unordered_map](../standard-library/unordered-map-class.md). Ty mají nižší režijní náklady na prvky a vyhledávání v čase, ale mohou být těžší používat správně a efektivně.

- Seřazené `vector`. Další informace najdete v tématu [algoritmy](../cpp/algorithms-modern-cpp.md).

Nepoužívejte pole ve stylu jazyka C. U starších rozhraní API, která potřebují přímý přístup k datům, použijte místo toho přístupové metody, jako je `f(vec.data(), vec.size());`. Další informace o kontejnerech naleznete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Standardní algoritmy knihovny

Než se rozhodnete, že pro svůj program potřebujete napsat vlastní algoritmus, nejprve si přečtěte C++ standardní [algoritmy](../standard-library/algorithm.md)knihovny. Standardní knihovna obsahuje stále rostoucí sortiment algoritmů pro mnoho běžných operací, jako je hledání, řazení, filtrování a náhodné provádění. Knihovna Math je rozsáhlá. Počínaje C++ 17 jsou k dispozici paralelní verze mnoha algoritmů.

Tady jsou některé důležité příklady:

- **for_each**výchozí průchozí algoritmus (spolu s rozsahem pro smyčky). 

- **transformace**, pro nemístní úpravu prvků kontejneru

- **find_if**výchozí algoritmus pro hledání.

- **řazení**, **lower_bound**a ostatní výchozí algoritmy pro řazení a vyhledávání.

Chcete-li napsat komparátor, použijte striktní **<** a použijte *pojmenované výrazy lambda* , když můžete.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>automaticky namísto explicitních typů názvů

C++ 11 zavádí klíčové slovo [auto](auto-cpp.md) pro použití v deklaracích proměnných, funkcí a šablon. **automaticky** instruuje kompilátor, aby odvodit typ objektu, takže ho nemusíte explicitně zadávat. **auto** je zvlášť užitečné, pokud je odvozený typ vnořenou šablonou:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Smyčky for na základě rozsahu

Iterace ve stylu jazyka C nad poli a kontejnery je náchylná k chybám indexování a je také únavné na typ. Chcete-li tyto chyby odstranit a zvýšit čitelnost kódu, použijte pro smyčky se standardními kontejnery knihoven a také nezpracovaná pole založená na rozsahu. Další informace naleznete v tématu [Range-based for Statement](../cpp/range-based-for-statement-cpp.md).

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

## <a name="constexpr-expressions-instead-of-macros"></a>výrazy constexpr namísto maker

Makra v jazyce C C++ a jsou tokeny, které preprocesor zpracovává před kompilací. Každá instance tokenu makra je nahrazena definovanou hodnotou nebo výrazem před zkompilováním souboru. Makra jsou běžně používána v programování ve stylu jazyka C k definování konstantních hodnot doby kompilace. Makra jsou ale náchylná k chybám a je obtížné je ladit. V moderním C++případě byste měli upřednostnit proměnné [constexpr](constexpr-cpp.md) pro konstanty v době kompilace:

```cpp
#define SIZE 10 / C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Jednotná inicializace

V moderním C++případě můžete použít inicializaci složené závorky pro libovolný typ. Tato forma inicializace je obzvláště užitečná při inicializaci polí, vektorů nebo jiných kontejnerů. V následujícím příkladu je `v2` inicializován se 3 instancemi `S`. `v3` se inicializuje se 3 instancemi `S`, které jsou samy inicializovány pomocí složených závorek. Kompilátor odvodí typ každého prvku na základě deklarovaného typu `v3`.

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

Moderní C++ přináší *sémantiku přesunutí* , která umožňuje eliminovat zbytečné kopie paměti, které v dřívějších verzích jazyka byly v některých situacích nenevyhnutelné. Operace *přesunu* převede vlastnictví prostředku z jednoho objektu na další bez vytvoření kopie. Při implementaci třídy, která vlastní prostředek, jako je například paměť haldy, popisovače souborů a tak dále, můžete pro něj definovat *konstruktor přesunu* a *operátor přiřazení přesunutí* . Kompilátor zvolí tyto speciální členy během řešení přetížení v situacích, kdy není kopie nutná. Standardní typy kontejnerů knihovny vyvolávají konstruktor Move pro objekty, pokud je definována. Další informace naleznete v tématu [třídy přesunu a operátory přiřazení přesunuC++()](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Výrazy lambda

V programování ve stylu jazyka C může být funkce předána jiné funkci prostřednictvím *ukazatele na funkci*. Ukazatele na funkce jsou nepohodlné, aby bylo možné zachovat a pochopit, protože funkce, na které odkazují, mohou být definovány jinde ve zdrojovém kódu, a to daleko od okamžiku, kdy je vyvolána. Také nejsou typově bezpečné. Moderní C++ poskytuje objekty funkce, třídy, které přepíší operátor [()](function-call-operator-parens.md) , který umožňuje jejich volání jako funkce. Nejpohodlnější způsob, jak vytvořit objekty funkce, je pomocí vložených [výrazů lambda](../cpp/lambda-expressions-in-cpp.md). Následující příklad ukazuje, jak použít výraz lambda k předání objektu funkce, který funkce `for_each` vyvolá u každého prvku ve vektoru:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Výraz lambda `[=](int i) { return i > x && i < y; }` lze číst jako funkci, která přijímá jeden argument typu `int` a vrací logickou hodnotu, která označuje, zda je výraz pravdivý. Všimněte si, že proměnné `x` a `y` z okolního kontextu lze použít ve výrazu lambda. `[=]` určuje, zda jsou tyto proměnné *zachyceny* hodnotou; Jinými slovy, výraz lambda má své vlastní kopie těchto hodnot.

## <a name="exceptions"></a>Výjimky

Jako obecné pravidlo moderní C++ zvýrazňuje výjimky spíše než chybové kódy jako nejlepší způsob, jak ohlásit a zpracovávat chybové stavy. Další informace najdete v tématu [moderní C++ osvědčené postupy pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std:: Atomic

Pro komunikační C++ mechanismy mezi vlákny použijte standardní knihovnu [std:: atomická](../standard-library/atomic-structure.md) struktura a související typy.

## <a name="stdvariant-c17"></a>std:: variant (C++ 17)

Sjednocení jsou běžně používána v programování ve stylu jazyka C k úspoře paměti tím, že umožňují členům různých typů zabírat stejné umístění v paměti. Sjednocení však nejsou typově bezpečná a jsou náchylná k chybám programování. C++ 17 zavádí třídu [std:: variant](../standard-library/variant-class.md) jako robustnější a bezpečnou alternativu pro sjednocení. Funkce [std:: navštíví](../standard-library/variant-functions.md#visit) se dá použít pro přístup k členům `variant` typu bezpečným způsobem.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Tabulka C++ shody jazyka Microsoft](../overview/visual-cpp-language-conformance.md)