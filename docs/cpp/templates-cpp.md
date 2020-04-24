---
title: Šablony (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032340"
---
# <a name="templates-c"></a>Šablony (C++)

Šablony jsou základem pro obecné programování v jazyce C++. Jako jazyk silného typu C++ vyžaduje, aby všechny proměnné měly určitý typ, buď explicitně deklarovaný programátorem nebo odvozené kompilátorem. Mnoho datových struktur a algoritmů však vypadá stejně bez ohledu na to, na jakém typu pracují. Šablony umožňují definovat operace třídy nebo funkce a umožnit uživateli určit, jaké konkrétní typy by tyto operace měly pracovat.

## <a name="defining-and-using-templates"></a>Definování a používání šablon

Šablona je konstrukce, která generuje běžný typ nebo funkci v době kompilace na základě argumentů, které uživatel poskytuje pro parametry šablony. Můžete například definovat šablonu funkce, jako je tato:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Výše uvedený kód popisuje šablonu pro obecnou funkci s parametrem t jednoho typu *,* jehož parametry návratové hodnoty a volání (lhs a rhs) jsou všechny tohoto typu. Můžete pojmenovat parametr typu, co se vám líbí, ale podle konvence se nejčastěji používají jednotlivá velká písmena. *T* je parametr šablony; klíčové slovo **typename** říká, že tento parametr je zástupný symbol pro typ. Při volání funkce kompilátor nahradí každou `T` instanci s argumentem konkrétní typ, který je určen uživatelem nebo odvozen kompilátorem. Proces, ve kterém kompilátor generuje třídu nebo funkci ze šablony, se označuje jako *instanování šablony*; `minimum<int>` je vytvoření instance šablony `minimum<T>`.

Jinde může uživatel deklarovat instanci šablony, která se specializuje na int. Předpokládejme, že get_a() a get_b() jsou funkce, které vracejí int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Však protože se jedná o šablonu funkce a kompilátor může odvodit typ z `T` argumentů *a* a *b*, můžete volat stejně jako běžné funkce:

```cpp
int i = minimum(a, b);
```

Když kompilátor narazí na poslední příkaz, vygeneruje novou funkci, ve které je každý výskyt *T* v šabloně nahrazen **int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Pravidla pro provádění kompilátoru provádí odpočet typu v šablonách funkcí jsou založeny na pravidlech pro běžné funkce. Další informace naleznete v [tématu Řešení přetížení volání šablony funkce](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Parametry typu

Ve `minimum` výše uvedené šabloně si všimněte, že parametr typu *T* není žádným způsobem kvalifikován, dokud není použit v parametrech volání funkce, kde jsou přidány kvalifikátory const a reference.

Neexistuje žádné praktické omezení počtu parametrů typu. Oddělte více parametrů čárky:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

**Třída** klíčového slova je ekvivalentní **typename** v tomto kontextu. Předchozí příklad můžete vyjádřit takto:

```cpp
template <class T, class U, class V> class Foo{};
```

Pomocí operátoru tři tečky (...) můžete definovat šablonu, která přebírá libovolný počet parametrů typu nula nebo více:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Jako typ typu lze použít libovolný předdefinovaný nebo uživatelem definovaný typ. Můžete například použít [std::vector](../standard-library/vector-class.md) ve standardní knihovně k ukládání proměnných typu **int** `MyClass`, **double**, [std::string](../standard-library/basic-string-class.md), , **const** `MyClass`*, `MyClass&`, a tak dále. Primární omezení při použití šablon je, že argument typu musí podporovat všechny operace, které jsou použity pro parametry typu. Například pokud `minimum` voláme `MyClass` using as v tomto příkladu:

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

Bude generována chyba kompilátoru, protože `MyClass` neposkytuje přetížení pro **<** operátor.

Neexistuje žádný vlastní požadavek, že argumenty typu pro konkrétní šablonu všechny patří do stejné hierarchie objektů, i když můžete definovat šablonu, která vynucuje takové omezení. Objektově orientované techniky můžete kombinovat se šablonami. Například můžete uložit Odvozené * ve\<\* vektorové základní>.    Všimněte si, že argumenty musí být ukazatele

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Základní požadavky, `std::vector` které a další standardní `T` kontejnery `T` knihovny uložit na prvky je, které jsou kopírovat přiřaditelné a kopie constructible.

## <a name="non-type-parameters"></a>Netypové parametry

Na rozdíl od obecných typů v jiných jazycích, jako je C# a Java, šablony Jazyka C++ podporují *parametry bez typu*, nazývané také parametry hodnoty. Můžete například zadat konstantní integrální hodnotu pro určení délky pole, jako v tomto příkladu, který je podobný třídě [std::array](../standard-library/array-class-stl.md) ve standardní knihovně:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Poznamenejte si syntaxi v deklaraci šablony. Hodnota `size_t` je předána jako argument šablony v době kompilace a musí být **const** nebo **constexpr** výraz. Používáte ji takto:

```cpp
MyArray<MyClass*, 10> arr;
```

Jiné druhy hodnot včetně ukazatelů a odkazů mohou být předány jako parametry bez typu. Můžete například předat ukazatel na funkci nebo objekt funkce přizpůsobit některé operace uvnitř kódu šablony.

### <a name="type-deduction-for-non-type-template-parameters"></a>Typ odpočtu pro parametry netextové šablony

V sadě Visual Studio 2017 a novějšív režimu **/std:c++17** kompilátor odvodí typ argumentu netypové šablony, který je deklarován s **automatickým**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Šablony jako parametry šablony

Šablona může být parametršablony. V tomto příkladu má MyClass2 dva parametry šablony: parametr typename *T* a parametr šablony *Arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Vzhledem k tomu, že samotný parametr *Arr* nemá žádné tělo, jeho názvy parametrů nejsou potřeba. Ve skutečnosti je chyba odkazovat na *Arr*'s typename nebo název `MyClass2`parametru třídy z v těle . Z tohoto důvodu lze vynechat názvy parametrů typu *Arr,* jak je znázorněno v tomto příkladu:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Výchozí argumenty šablony

Šablony tříd a funkcí mohou mít výchozí argumenty. Pokud má šablona výchozí argument, můžete ji při použití ponechat neurčenou. Například šablona std::vector má výchozí argument pro alokátor:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

Ve většině případů je přijatelná výchozí třída std::alokátor, takže použijete vektor, jako je tento:

```cpp
vector<int> myInts;
```

Ale v případě potřeby můžete zadat vlastní přidělování, jako je tento:

```cpp
vector<int, MyAllocator> ints;
```

Pro více argumentů šablony musí mít všechny argumenty za prvním výchozím argumentem výchozí argumenty.

Při použití šablony, jejíž parametry jsou všechny výchozí, použijte prázdné úhlové závorky:

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>Specializace šablon

V některých případech není možné nebo žádoucí, aby šablona definovala přesně stejný kód pro libovolný typ. Například můžete chtít definovat cestu kódu, která má být spuštěna pouze v případě, že argument em i argument typu je ukazatel nebo std::wstring nebo typ odvozený z určité základní třídy.  V takových případech můžete definovat *specializaci* šablony pro daný typ. Když uživatel vytvoří konkretizaci šablony s tímto typem, kompilátor použije specializaci ke generování třídy a pro všechny ostatní typy kompilátor zvolí obecnější šablonu. Specializace, ve kterých jsou všechny parametry specializované, jsou *kompletní specializace*. Pokud jsou specializované pouze některé parametry, nazývá se *částečná specializace*.

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

Šablona může mít libovolný počet specializací, pokud je každý parametr specializovaného typu jedinečný. Pouze šablony tříd mohou být částečně specializované. Všechny úplné a částečné specializace šablony musí být deklarovány ve stejném oboru názvů jako původní šablona.

Další informace naleznete v tématu [Specializace šablony](../cpp/template-specialization-cpp.md).
