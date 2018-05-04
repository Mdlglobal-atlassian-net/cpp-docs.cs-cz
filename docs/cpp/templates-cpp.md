---
title: Šablony (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- template_cpp
dev_langs:
- C++
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5aa532246054ff0a0b67b9560e40ae704a40fc8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="templates-c"></a>Šablony (C++)
Šablony jsou základem pro obecné programování v jazyce C++. Jako jazyk silného typu vyžaduje C++ všechny proměnné tak, aby měl konkrétního typu buď explicitně deklarovaná programátorů nebo odvodit kompilátorem. Ale mnoha datové struktury a algoritmy vypadají stejně bez ohledu na to, jaký typ jsou provozu na. Povolit šablony vám umožňuje definovat operace třídy nebo funkce a umožňují určit, jaké konkrétní typy tyto operace by měla spolupracovat na.  
  
## <a name="defining-and-using-templates"></a>Definování a používání šablon  
 Šablona je konstruktor, který generuje obyčejnou typ nebo funkci v době kompilace podle argumenty uživatel zadává pro parametry šablony. Můžete například definovat šablonu funkce takto:  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Výše uvedený kód Popisuje šablonu pro obecné funkce s jediný parametr typu `T`, jehož vrátit hodnotu a volání parametry (lhs a rhs) jsou všechny tohoto typu. Parametr typu můžete pojmenovat nic, co je třeba, ale podle konvence jeden velká písmena se běžně používají. `T` je parametr šablony; `typename` – klíčové slovo říká, že tento parametr je zástupný symbol pro typu. Při volání funkce kompilátoru nahradí všechny instance řetězce `T` s argumentem konkrétní typ, který je buď specifikovaných uživatelem nebo odvodit kompilátorem. Proces, ve kterém kompilátor vygeneruje třídu nebo funkce z šablony se označuje jako *vytváření instancí šablon*;   `minimum<int>` je vytvoření instance šablony `minimum<T>`.  
  
 Jinam uživatel může deklarovat instance šablony, která se specializuje na int. Předpokládejme, že get_a() a get_b() jsou funkce, které vrací typ int:  
  
```  
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Ale vzhledem k tomu, že toto je funkce šablony a kompilátor odvodit typ `T` z argumentů `a` a `b`, můžete ji volat stejně jako obyčejnou funkce:  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Po kompilátor narazí tento poslední příkaz, ve které všechny výskyty řetězce vygeneruje novou funkci *T* v šabloně se nahradí `int`:  
  
```  
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Pravidla pro jak kompilátor provede odvození typu v šablonách funkce jsou na základě pravidel pro běžné funkce. Další informace najdete v tématu [přetížení řešení z volání šablony funkce](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a> Parametry typu  
 V `minimum` šablony výše, Všimněte si, že parametr typu `T` není kvalifikován žádným způsobem, dokud se v parametrech volání funkce používá, kde jsou přidány const a kvalifikátory odkaz.  
  
 Neexistuje žádné praktické omezení počtu parametrů typu. Několik parametrů oddělte čárkami:  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 Klíčové slovo `class` je ekvivalentní `typename` v tomto kontextu. Lze vyjádřit jako v předchozím příkladu:  
  
```  
template <class T, class U, class V> class Foo{};   
```  
  
 Operátor výpustky (...) můžete použít k definování šablonu, která přebírá libovolný počet nula nebo více parametrů typu:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 Žádný typ předdefinovaných nebo uživatelsky definovaných můžete použít jako argument typu. Například můžete použít std::vector v knihovně standardní k uložení proměnné ints, hodnoty Double, řetězce, MyClass, const MyClass *, MyClass &. Primární omezení při použití šablony je, že argument typu musí podporovat žádné operace, které se použijí pro parametry typu. Například, pokud říkáme minimální pomocí MyClass jako v následujícím příkladu:  
  
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
  
 Chyba kompilátoru se budou generovat, protože MyClass neposkytuje přetížení pro < operátor.  
  
 I když můžete definovat šablonu, která vynucuje toto omezení se nevyžaduje vyplývajících, že argumenty typu pro všechny konkrétní šablonu všechny patřit do stejné hierarchie objektů. Objektově orientované techniky můžete kombinovat s šablonami; Například můžete uložit odvozené * v vektor\<základní\*>.    Všimněte si, že argumenty, které musí být ukazatele  
  
```  
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Základní požadavky, které vektoru a jiné standardní knihovna kontejnery kladou na elementy `T` je, že `T` kopie přiřadit a kopírování zkonstruovatelný.  
  
## <a name="non-type-parameters"></a>Parametry bez typu  
 Na rozdíl od obecné typy v jiných jazycích, například C# a Java C++ šablony podporují bez typu parametry, označované taky jako parametry s hodnotou. Můžete například zadat integrální konstanta zadat délku pole, stejně jako u tohoto příkladu, který je podobný std::array třídy ve standardní knihovně:  
  
```  
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 Všimněte si syntaxe v deklaraci šablony. Size_t – hodnota je předána jako argument šablony v době kompilace a musí být konstanta, nebo výraz constexpr. Použít takto:  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Ostatní typy hodnot, včetně ukazatelů a odkazů na lze předat ve jako parametry bez typu. Můžete například předat v ukazatel do funkce nebo funkce objekt, který chcete přizpůsobit některé operace uvnitř kód šablony.  
  
## <a id="template_parameters"></a> Šablony jako parametry šablony  
 Šablony může být parametr šablony. V tomto příkladu MyClass2 má dva parametry šablony: Parametr typename `T` a parametr šablony `Arr`:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 Protože `Arr` parametr sám nemá žádné body, nejsou potřeba jeho názvy parametrů. Ve skutečnosti, jedná se o chybu, který bude odkazovat na `Arr`na typename nebo třída názvy parametrů z v hlavní `MyClass2`. Z tohoto důvodu `Arr`na názvy parametrů typu lze vynechat, jak je uvedeno v následujícím příkladu:  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Výchozí šablony argumenty  
 Šablony třídy a funkce může mít výchozí argumenty. Pokud šablona má výchozí argument, který můžete nechat neurčené při použití. Například šablona std::vector má výchozí argument pro přidělujícího modulu:  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 Ve většině případů je přijatelné, výchozí std::allocator třídy, který použít vektoru takto:  
  
```cpp  
vector<int> myInts;  
```  
  
 Ale pokud potřeby můžete zadat vlastní allocator podobné výjimky:  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 Pro více argumentů šablonu musí mít všechny argumenty po prvním argumentem výchozí výchozí argumenty.  
  
 Pokud používáte šablonu, jejíž parametry jsou všechny uvedena, použijte prázdný lomené závorky:  
  
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
  
## <a name="template-specialization"></a>Specializace šablony  
 V některých případech není možná nebo žádoucí pro šablonu definovat stejný kód pro libovolného typu. Například si přejete definovat provést jenom v případě argument typu je ukazatel nebo std::wstring nebo z určité základní třídy odvozený typ. cesta ke kódu.  V takových případech můžete definovat *specializace* šablony pro daný typ. Když uživatel vytvoří šablona s daným typem, kompilátor používá ke generování třídy specializace a pro všechny ostatní typy kompilátor zvolí další Obecné šablony. Specializací, ve kterých se specializují všechny parametry jsou *dokončení specializací*. Pokud jenom některé z parametrů se specializují, se nazývá *částečná specializace*.  
  
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
  
 Šablona může mít libovolný počet specializací tak dlouho, dokud každý parametr speciálním typem je jedinečný.   Může být částečně specializované pouze šablony třídy. Všechny úplné a částečné specializací šablony musí být deklarován v oboru názvů stejné jako původní šablonu.  
  
 Další informace najdete v tématu [specializace šablony](../cpp/template-specialization-cpp.md).