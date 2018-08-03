---
title: Šablony (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: c5a9aa15839169de846439c73af1df92d7342358
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463925"
---
# <a name="templates-c"></a>Šablony (C++)
Šablony jsou základem pro obecné programování v jazyce C++. Jako silně typovaný jazyk C++ vyžaduje všechny proměnné konkrétního typu, explicitně deklarován s programátor nebo kompilátor odvodit. Nicméně mnoho datových struktur a algoritmů vypadají stejně bez ohledu na to, jaký typ jsou nasazeny na. Šablony umožňují definovat operace třídy nebo funkce a nechat uživatele, určete, jaké konkrétní typy tyto operace by měla fungovat na.  
  
## <a name="defining-and-using-templates"></a>Definování a používání šablon  
 Šablona je konstrukce, která generuje běžný typ nebo funkce v době kompilace podle argumenty uživatel zadává parametrů šablony. Můžete například definovat šablony funkce takto:  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Výše uvedený kód Popisuje šablonu pro obecnou funkci s parametrem jednoho typu *T*, jejichž vrácení hodnoty a parametry (lhs a zarovnání indirekce rhs) volání jsou všechny tohoto typu. Parametr typu můžete pojmenovat všechno, co je třeba, ale podle konvence jeden velká písmena se běžně používají. *T* je parametr šablony; **typename** – klíčové slovo říká, že tento parametr je zástupný symbol pro typ. Pokud funkce je volána, kompilátor nahradí všechny instance `T` s konkrétní typ argumentu, který je zadán uživatel nebo odvodit kompilátorem. Proces, ve kterém kompilátor vygeneruje třídu nebo funkci ze šablony se označuje jako *vytváření instancí šablon*; `minimum<int>` je instance šablony `minimum<T>`.  
  
 Jinde uživatel může deklarovat instanci šablony, která se specializuje na int. Předpokládejme, že get_a() a get_b() jsou funkce, které vrací celé číslo:  
  
```cpp 
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Ale protože je to šablonu funkce a kompilátor může odvodit typ `T` z argumentů *a* a *b*, můžete ji volat stejně jako běžné funkce:  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Když kompilátor narazí, který tento poslední příkaz, ve které všechny výskyty generuje novou funkci *T* v šabloně je nahrazen **int**:  
  
```cpp   
int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Pravidla pro způsob kompilátor provede odvození typu v rámci šablony funkce jsou na základě pravidel pro běžné funkce. Další informace najdete v tématu [přetížení řešení z volání šablony funkce](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a> Parametry typu  
 V `minimum` šabloně výše, Všimněte si, že parametr typu *T* není kvalifikován žádným způsobem, dokud se používá v parametry volání funkce, kde jsou přidány const a kvalifikátory odkaz.  
  
 Neexistuje žádný praktický limit pro počet parametrů typu. Více parametrů oddělte čárkami:  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
```  
  
 Klíčové slovo **třídy** je ekvivalentní **typename** v tomto kontextu. Můžete vyjádřit jako v předchozím příkladu:  
  
```cpp 
template <class T, class U, class V> class Foo{};   
```  
  
 Operátor tří teček (...) můžete použít k definování šablony, která přijímá libovolný počet nula nebo více parametrů typu:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 Jakýkoli vestavěný nebo uživatelem definovaný typ může sloužit jako argument typu. Například můžete použít std::vector ve standardní knihovně pro ukládání hodnot datového typu Double celá čísla, řetězce, MyClass, MyClass const *, MyClass &. Primární omezení při použití šablony je, že argument typu musí podporovat všechny operace, které se použijí pro parametry typu. Například, pokud označujeme je jako minimální pomocí MyClass jako v následujícím příkladu:  
  
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
  
 Chyba kompilátoru se vygeneruje, protože MyClass neposkytuje přetížení pro < – operátor.  
  
 Přestože můžete definovat šablony, která vynucuje toto omezení se nevyžaduje vlastní, že argumenty typu pro jakékoli konkrétní šablonu všechny patřit do stejné hierarchie objektů. Objektově orientované techniky můžete zkombinovat s šablony. Například můžete ukládat Derived * ve vektoru\<Base\*>.    Všimněte si, že argumenty musí být ukazateli  
  
```cpp 
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Základní požadavky, které vektoru a ostatní kontejnery standardní knihovny kladou na prvky `T` je, že `T` být přiřaditelný kopírování a constructible kopírování.  
  
## <a name="non-type-parameters"></a>Parametry bez typu  
 Na rozdíl od obecné typy v jiných jazycích, jako je C# nebo Java C++ šablony podporují parametry bez typu, také označované jako parametry hodnotu. Můžete například poskytnout konstantní celočíselnou hodnotu k určení délky pole, stejně jako v tomto příkladu, který je podobný třídě std::array ve standardní knihovně:  
  
```cpp 
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
```  
  
 Všimněte si syntaxi v deklaraci šablony. Hodnota size_t je předán jako argument šablony v době kompilace a musí být konstantní nebo výraz constexpr. Použijete ho následujícím způsobem:  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Jiné typy hodnot včetně ukazatele a reference, je možné předat v jako parametry bez typu. Například můžete předat ukazatel na funkci nebo objektu funkce přizpůsobit některé operace uvnitř kód šablony.  
  
## <a id="template_parameters"></a> Šablony jako parametry šablony  
 Parametr šablony může být šablonou. V tomto příkladu MyClass2 má dva parametry šablony: Parametr typename *T* a parametr šablony *směrování žádostí na aplikace*:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 Vzhledem k tomu, *směrování žádostí na aplikace* parametr sám nemá žádný text, jeho názvy parametrů nejsou potřeba. Ve skutečnosti, jedná se o chybu k odkazování na *směrování žádostí na aplikace*společnosti typename nebo třída názvy parametrů z těla `MyClass2`. Z tohoto důvodu *směrování žádostí na aplikace*názvy parametrů typů lze vynechat, jak je znázorněno v tomto příkladu:  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Výchozí argumenty šablony  
 Šablony třídy a funkce mohou mít výchozí argumenty. Když šablony má výchozí argument, který můžete nechat neurčené, když ji použijete. Například šablona std::vector má výchozí argument pro přidělujícího modulu:  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 Ve většině případů je výchozí třídu std::allocator přijatelné, proto použijete vektor takto:  
  
```cpp  
vector<int> myInts;  
```  
  
 Ale pokud potřeby můžete zadat vlastní Alokátor tímto způsobem:  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 Všechny argumenty za první argument výchozí více argumentů šablony, musí mít výchozí argumenty.  
  
 Při použití šablony, jejíž parametry jsou všechny použita jako výchozí, použijte prázdný ostrých závorek:  
  
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
 V některých případech není možná nebo žádoucí pro šablonu definovat přesně stejný kód libovolného typu. Například budete chtít definovat cesta kódu, který se spustí jenom v případě, že je argument typu ukazatel nebo std::wstring nebo typ odvozený od určité základní třídy.  V takových případech můžete definovat *specializace* šablony pro daný typ. Když uživatel vytvoří šablonu instanci daného typu, kompilátor specializace používá ke generování třídy a pro všechny ostatní typy kompilátor zvolí další Obecné šablony. Specializace, ve kterých jsou specializované všechny parametry jsou *dokončení specializace*. Pokud jen některé parametry jsou specializované, je volána *částečná specializace*.  
  
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
  
 Šablona může obsahovat libovolný počet specializace, za předpokladu, každý parametr speciálním typem je jedinečný. Pouze šablony třídy mohou být částečně specializovaná. Všechny úplné a částečné specializace šablony musí být deklarovány v oboru názvů stejný jako původní šablony.  
  
 Další informace najdete v tématu [specializace šablony](../cpp/template-specialization-cpp.md).