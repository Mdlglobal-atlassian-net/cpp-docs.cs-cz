---
title: Šablony (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 36ada3cc3b933e99e9b29b3b58463f6bc526fc7d
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546403"
---
# <a name="templates-c"></a>Šablony (C++)

Šablony jsou základem pro obecné programování v C++. Jako jazyk silného typu vyžaduje, C++ aby všechny proměnné měly konkrétní typ, buď explicitně deklarované programátorem, nebo odvozený kompilátorem. Mnohé datové struktury a algoritmy ale vypadají stejně bez ohledu na to, na jaký typ pracují. Šablony umožňují definovat operace třídy nebo funkce a uživatel může určit, na jaké typy tyto operace mají pracovat.

## <a name="defining-and-using-templates"></a>Definice a používání šablon

Šablona je konstrukce, která generuje běžný typ nebo funkci v době kompilace na základě argumentů, které uživatel zadá pro parametry šablony. Například můžete definovat šablonu funkce takto:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Výše uvedený kód popisuje šablonu pro obecnou funkci s jediným parametrem typu *T*, jehož návratová hodnota a parametry volání (LHS a zarovnání indirekce RHS) jsou všechny tohoto typu. Parametr typu můžete pojmenovat libovolně, ale podle konvence se nejčastěji používají velká písmena s jedním velkým písmenem. *T* je parametr šablony; klíčové slovo **TypeName** říká, že tento parametr je zástupný symbol pro typ. Když je funkce volána, kompilátor nahradí všechny instance `T` pomocí konkrétního argumentu typu, který je buď zadán uživatelem nebo odvozený kompilátorem. Proces, ve kterém kompilátor generuje třídu nebo funkci ze šablony, je označován jako *vytvoření instance šablony*; `minimum<int>` je instance `minimum<T>`šablony.

Jinde může uživatel deklarovat instanci šablony, která je specializovaná pro int. předpokládá se, že get_a () a get_b () jsou funkce, které vracejí int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Ale protože je to šablonu funkce a kompilátor může odvodit typ `T` z argumentů *a* a *b*, můžete ji volat stejně jako běžné funkce:

```cpp
int i = minimum(a, b);
```

Když kompilátor narazí na tento poslední příkaz, vygeneruje novou funkci, ve které se všechny výskyty *T* v šabloně nahradí řetězcem **int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Pravidla pro způsob, jakým kompilátor provádí odvození typu v šablonách funkcí, jsou založena na pravidlech pro běžné funkce. Další informace naleznete v tématu [řešení přetížení volání šablony funkce](../cpp/overload-resolution-of-function-template-calls.md).

## <a id="type_parameters"></a>Parametry typu

V šabloně `minimum` výše si všimněte, že parametr Type *t* není kvalifikován jakýmkoli způsobem, dokud jej nepoužijete v parametrech volání funkce, kde jsou přidány kvalifikátory const a reference.

Neexistuje žádné praktické omezení počtu parametrů typu. Více parametrů oddělte čárkami:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

**Třída** klíčového slova je ekvivalentní typu **TypeName** v tomto kontextu. Předchozí příklad můžete vyjádřit jako:

```cpp
template <class T, class U, class V> class Foo{};
```

Pomocí operátoru elipsy (...) můžete definovat šablonu, která přebírá libovolný počet nula nebo více parametrů typu:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Libovolný vestavěný nebo uživatelsky definovaný typ lze použít jako argument typu. Například můžete použít [std:: Vector](../standard-library/vector-class.md) ve standardní knihovně pro ukládání proměnných typu **int**, **Double**, [std:: String](../standard-library/basic-string-class.md), `MyClass`, **const** `MyClass`*, `MyClass&`a tak dále. Primární omezení při použití šablon je, že argument typu musí podporovat všechny operace, které jsou použity pro parametry typu. Například, pokud voláme `minimum` pomocí `MyClass` jako v tomto příkladu:

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

Dojde k vygenerování chyby kompilátoru, protože `MyClass` neposkytuje přetížení pro operátor **<** .

Neexistuje žádný podstatný požadavek na to, aby argumenty typu pro konkrétní šablonu patřily do stejné hierarchie objektů, i když můžete definovat šablonu, která toto omezení vynutila. Můžete zkombinovat objektově orientované techniky pomocí šablon; Můžete například uložit odvozené * ve vektorovém\<Base\*>.    Všimněte si, že argumenty musí být ukazatele

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Základní požadavky, které `std::vector` a další kontejnery standardní knihovny, jsou kladeny na prvky `T` je `T` zkopírování a kopírování-constructible.

## <a name="non-type-parameters"></a>Parametry bez typu

Na rozdíl od generických typů v jiných jazycích C# , jako je C++ například a Java, šablony podporují *parametry bez typu*, nazývané také parametry hodnot. Například můžete zadat konstantní celočíselnou hodnotu pro určení délky pole, jako v tomto příkladu, který je podobný třídě [std:: Array](../standard-library/array-class-stl.md) ve standardní knihovně:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Všimněte si syntaxe v deklaraci šablony. Hodnota `size_t` je předána jako argument šablony v době kompilace a musí být **konstantní** nebo výraz **constexpr** . Použijete ji takto:

```cpp
MyArray<MyClass*, 10> arr;
```

Jiné druhy hodnot, včetně ukazatelů a odkazů, mohou být předány jako parametry, které nejsou typu. Například můžete předat ukazatel na objekt funkce nebo funkce pro přizpůsobení některé operace uvnitř kódu šablony.

### <a name="type-deduction-for-non-type-template-parameters"></a>Srážky typu pro parametry šablony bez typu

V aplikaci Visual Studio 2017 a novější v **/std: režim c++ 17** kompilátor odvodí typ netypového argumentu šablony, který je deklarován pomocí **auto**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a id="template_parameters"></a>Šablony jako parametry šablony

Šablona může být parametrem šablony. V tomto příkladu má MyClass2 dva parametry šablony: parametr TypeName *T* a parametr šablony *ARR*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Vzhledem k tomu, že samotný parametr *ARR* nemá žádné tělo, jejich názvy parametrů nejsou potřeba. Ve skutečnosti se jedná o chybu pro odkazování na názvy parametrů nebo třídy v rámci objektu *ARR*z těla `MyClass2`. Z tohoto důvodu mohou být názvy parametrů typu *ARR*vynechány, jak je znázorněno v následujícím příkladu:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Výchozí argumenty šablony

Šablony třídy a funkce mohou mít výchozí argumenty. Pokud má šablona výchozí argument, můžete ji nechat nespecifikovanou, když ji použijete. Například šablona std:: Vector má výchozí argument pro přidělování:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

Ve většině případů je výchozí třída std:: přidělování přijatelná, takže použijete vektor podobný tomuto:

```cpp
vector<int> myInts;
```

V případě potřeby ale můžete zadat vlastní přidělování, například:

```cpp
vector<int, MyAllocator> ints;
```

Pro více argumentů šablony všechny argumenty po prvním výchozím argumentu musí mít výchozí argumenty.

Při použití šablony, jejíž parametry jsou nastavené jako výchozí, použijte prázdné lomené závorky:

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

V některých případech není možné nebo žádoucí, aby šablona definovala přesně stejný kód pro libovolný typ. Můžete například chtít definovat cestu kódu, který má být proveden pouze v případě, že je argumentem typu ukazatel nebo std:: wstring nebo typ odvozený z konkrétní základní třídy.  V takových případech můžete definovat *specializaci* šablony pro tento konkrétní typ. Když uživatel vytvoří instanci šablony s tímto typem, kompilátor použije specializaci k vygenerování třídy a pro všechny ostatní typy kompilátor zvolí obecnější šablonu. Specializace, ve kterých jsou všechny parametry specializované, jsou *kompletní specializace*. Pokud jsou pouze některé parametry specializované, nazývá se *Částečná specializace*.

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

Šablona může mít libovolný počet specializací, pokud je každý parametr specializovaného typu jedinečný. Pouze šablony třídy mohou být částečně specializované. Všechny kompletní a částečné specializace šablony musí být deklarovány ve stejném oboru názvů jako původní šablona.

Další informace naleznete v tématu [specializace šablony](../cpp/template-specialization-cpp.md).