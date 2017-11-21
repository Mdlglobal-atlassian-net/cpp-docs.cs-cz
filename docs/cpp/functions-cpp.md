---
title: Funkce (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e5794cd9ec0eb5afc879507bcf8942d6481ebca4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="functions-c"></a>Funkce (C++)
Funkce je blok kódu, který provádí nějaké operace. Funkce můžete volitelně definovat vstupní parametry, které umožňují volající předání argumentů do funkce. Funkce můžete volitelně vrátit hodnotu jako výstup. Funkce jsou užitečné pro zapouzdření běžných operací v jednom opakovaně použitelné bloku, v ideálním případě s názvem, který jasně popisuje, jaké funkce. Následující funkce přijímá dvě celá čísla od volající a vrátí jejich součet; `a` a `b` jsou *parametry* typu `int`.  
  
```  
int sum(int a, int b)  
{  
    return a + b;  
}  
```  
  
 Může být funkce "vyvolání nebo *názvem*, z různých míst v programu. Hodnoty, které se předávají funkce jsou *argumenty*, jejichž typy musí být kompatibilní s typy parametrů v definici funkce.  
  
```  
int main()  
{  
    int i = sum(10, 32);  
    int j = sum(i, 66);  
    cout << "The value of j is" << j << endl; // 108  
}  
```  
  
 Neexistuje žádné praktické omezení délky funkce, ale pro funkce, které provedení jednoho úkolu dobře definovaný cílem je dobré návrhu. Složité algoritmy by měl být rozdělena na snadno pochopit jednodušší funkce kdykoli je to možné.  
  
 Funkce, které jsou definované na rozsah třídy se nazývají členské funkce. V jazyce C++ na rozdíl od jiných jazyků, funkce lze také definovat v oboru názvů (včetně implicitní globálního oboru názvů). Takové funkce se nazývají *bez funkce* nebo *třetí funkce*; používají se hojně ve standardní knihovně.  
  
## <a name="parts-of-a-function-declaration"></a>Součástí deklaraci – funkce  
 Minimální funkce *deklarace* se skládá z návratový typ, název funkce a seznam parametrů (který může být prázdné), spolu s volitelné klíčová slova, která obsahují další pokyny pro kompilátor. V následujícím příkladu je deklaraci funkce:

 ```cpp
 int sum(int a, int b);
 ```

 Definice funkce se skládá z deklaraci, a *textu*, což je veškerý kód mezi složenými závorkami:
 
 ```cpp
int sum(int a, int b)  
{  
    return a + b;  
}  
```
 Funkce deklarace, za nímž následuje středníkem může zobrazit na více místech v programu. Musí být uveden před volání této funkce v jednotlivých jednotek překlad. Definice této funkce musí být uvedena pouze jednou v programu, podle jednoho pravidla definice (ODR).  
  
 Požadované části deklaraci funkce jsou:  
  
1.  Návratový typ, který určuje typ hodnoty, které funkce vrátí hodnotu, nebo `void` Pokud je vrácena žádná hodnota. V C ++ 11 `auto` je platný návratový typ, který dává pokyn kompilátoru k odvození typu z příkaz return. V C ++ 14 je také povoleno decltype(auto). Další informace najdete v tématu odvození typu vrátit typy.  
  
2.  Název funkce, který musí začínat písmenem nebo podtržítkem a nesmí obsahovat mezery. Obecně platí úvodní podtržítka v názvech funkce standardní knihovny znamenat privátní členské funkce nebo třetí funkce, které nejsou určeny pro použití v kódu. 
  
3.  Seznam parametrů složená závorka, oddělených čárkami sadu středníky nula nebo více parametrů, které určují typ a volitelně místní název, pomocí kterého můžete získat přístup hodnoty uvnitř tělo funkce. 
  
 Volitelné části deklarace funkce patří:  
  
1.  `constexpr`, která označuje, že návratová hodnota funkce je konstantní hodnota můžete vypočítat v době kompilace.  
  
    ```  
    constexpr float exp(float x, int n)  
    {  
        return n == 0 ? 1 :  
            n % 2 == 0 ? exp(x * x, n / 2) :  
            exp(x * x, (n - 1) / 2) * x;  
    };  
    ```  
  
2.  Jeho `linkage` specifikace, `extern` nebo `static`.  
  
    ```  
    Declare printf with C linkage.  
    extern "C" int printf( const char *fmt, ... );  
  
    ```  
  
     Další informace najdete v tématu [Program a propojení](../cpp/program-and-linkage-cpp.md).  
  
3.  `inline`, což dává pokyn kompilátoru nahradit každé volání funkce samotný kód funkce. vložené může vám pomůže zvýšit výkon v situacích, kde funkci rychle provede a opakovaně volána v části důležité pro výkon kódu.  
  
    ```  
    inline double Account::GetBalance()  
    {  
        return balance;  
    }  
    ```  
  
     Další informace najdete v tématu [vložené funkce](../cpp/inline-functions-cpp.md).  
  
4.  A `noexcept` výraz, který určuje, zda funkce může vyvolat výjimku. V následujícím příkladu funkce není vyvolána výjimka, pokud `is_pod` výraz vyhodnocen jako `true`.  
  
    ```  
    #include <type_traits>  
  
    template <typename T>  
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}  
    ```  
  
     Další informace najdete v tématu [noexcept](../cpp/noexcept-cpp.md).  
  
5.  (Jenom členské funkce) Odchylka nákladů kvalifikátory, které určují, jestli je funkce `const` nebo `volatile`.  
  
6.  (Jenom členské funkce) `virtual`, `override`, nebo `final`. `virtual`Určuje, že funkce může být přepsáno v odvozené třídě. `override`znamená, že je funkce v odvozené třídě přepisování virtuální funkce. `final`znamená, funkci nelze přepsat v žádné další odvozené třídy. Další informace najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).  
  
7.  (jenom členské funkce) `static` použít na člena, funkce znamená, že funkce není spojen s všechny instance objektů třídy.  
  
8.  (Jenom nestatické členské funkce) Ref – kvalifikátor, který určuje kompilátoru, které přetížení funkce, která se vybrat, kdy parametr implicitní objektu (* to) je odkaz rvalue oproti odkazu lvalue.  
  
 Následující obrázek znázorňuje části definici funkce. Podbarvené oblasti je tělo funkce.  
  
 ![Součástí definice funkce](../cpp/media/vc38ru1.gif "vc38RU1")  
Součástí definice funkce  
  
## <a name="function-definitions"></a>Definice funkcí  
 Proměnných deklarovaných v těle se označují jako místní proměnné nebo místní hodnoty. Se dostala mimo rozsah při ukončení funkce; Funkce, proto by měla vrátit nikdy odkaz na místní!  
  
## <a name="function-templates"></a>Šablony funkcí  
 Šablonu funkce je podobná šablona třídy; vygeneruje konkrétní funkce založené na šabloně argumenty. V mnoha případech je schopen odvodit argumenty typu šablony a proto není nutné explicitně zadávat.  
  
```  
template<typename Lhs, typename Rhs>  
auto Add2(const Lhs& lhs, const Rhs& rhs)  
{  
    return lhs + rhs;  
}  
  
auto a = Add2(3.13, 2.895); // a is a double  
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string  
```  
  
 Další informace najdete v tématu [šablony funkcí](../cpp/function-templates.md)  
  
## <a name="function-parameters-and-arguments"></a>Funkční parametry a argumenty  
 Funkce obsahuje parametr textový soubor s oddělovači seznam nula nebo více typů, z nichž každá má název, podle kterého byla přístupná uvnitř tělo funkce. Šablonu funkce může zadání dalších parametrů typu nebo hodnota. Volající předá argumenty, které jsou konkrétní hodnoty, jejichž typy jsou kompatibilní s seznam parametrů.  
  
 Ve výchozím nastavení jsou argumenty předaný funkci podle hodnoty, což znamená, že funkce obdrží kopii objekt předávány. Pro velké objekty, vytvoření kopie může být nákladné a je vždy nezbytné. Aby argumenty předávané odkazem (konkrétně odkazu lvalue), přidejte quaitifer odkaz na parametr:  
  
```  
void DoSomething(std::string& input){...}  
```  
  
 Pokud funkci upraví argument, který je předán odkazem, upraví původní objekt není místní kopii. Abyste zabránili úprava takové argument funkce, kvalifikaci parametr jako const &:  
  
```  
void DoSomething(const std::string& input){...}  
```  
  
 **C++ 11:** explicitně zpracování argumenty předávané deklarátor odkazu nebo odkazu lvalue, použijte dvojitou hodnotu ampersand na parametru určíte universal odkaz:  
  
```  
void DoSomething(const std::string&& input){...}  
```  
  
 Funkce deklarovat s jeden – klíčové slovo `void` v parametru deklarace seznamu nezadávaly žádné argumenty, stejně dlouho jako klíčové slovo `void` je první a je pouze členem deklarace seznam argumentů. Argumenty typu `void` jinde v seznamu způsobí chyby. Příklad:  
  
```  
  
// OK same as GetTickCount()  
long GetTickCount( void );   
```  
  
 Ačkoli je neplatné zadat argument typu `void` s výjimkou uvedenou zde, mohou se typy odvozené z typu `void` (například ukazatele na typ `void` a pole typu `void`) objevit kdekoli v seznamu deklarace argumentů.  
  
### <a name="default-arguments"></a>Výchozí argumenty  
 Poslední parametr nebo parametry v podpis funkce může být přiřazen argument výchozí, což znamená, že volající může vynechte argument při volání funkce, pokud se chcete zadat jinou hodnotu.  
  
```  
int DoSomething(int num,   
    string str,   
    Allocator& alloc = defaultAllocator)  
{ ... }  
  
// OK both parameters are at end  
int DoSomethingElse(int num,   
    string str = string{ "Working" },   
    Allocator& alloc = defaultAllocator)  
{ ... }  
  
// C2548: 'DoMore': missing default parameter for parameter 2  
int DoMore(int num = 5, // Not a trailing parameter!  
    string str,  
    Allocator& = defaultAllocator)  
{...}  
```  
  
 Další informace najdete v tématu [výchozí argumenty](../cpp/default-arguments.md).  
  
## <a name="function-return-types"></a>Návratové typy funkcí  
 Funkce nemusí vracet jinou funkci nebo integrované pole; ale může vracet ukazatele na tyto typy nebo *lambda*, který vytvoří objekt funkce. Kromě těchto případech funkce může vrátit hodnotu žádný typ, který je v oboru, nebo může vrátit žádná hodnota, v takovém případě návratový typ je `void`.  
  
### <a name="trailing-return-types"></a>Koncové návratové typy  
 "Běžný" návratový typ se nachází na levé straně podpis funkce. A *koncové návratový typ* se nachází na pravé straně většina podpisu a předchází -> – operátor. Koncové návratové typy jsou užitečné zejména v šablonách funkce, když typ vrácené hodnoty, závisí na parametry šablony.  
  
```  
template<typename Lhs, typename Rhs>  
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)  
{  
    return lhs + rhs;   
}  
```  
  
 Když `auto` se používá ve spojení s návratovým typem koncové právě slouží jako zástupný symbol pro výraz decltype – ať vytváří a nemá sám provádět odvození typu.  

   
## <a name="function-local-variables"></a>Lokální proměnné – funkce  
 Proměnné, která je deklarovaná uvnitř tělo funkce je volána *místní proměnné* nebo jednoduše *místní*. Místní hodnoty – nestatické viditelné pouze uvnitř tělo funkce a pokud jsou deklarovány v zásobníku se dostala mimo rozsah při ukončení funkce. Vytvořit místní proměnné a vrátí hodnotu, můžete kompilátor obvykle provádět optimalizace návratovou hodnotu předejdete operace kopírování zbytečné. Pokud vrátíte místní proměnné odkazem, kompilátor vás upozorní, protože na tento odkaz používat pokusy volající dojde po místní byl zničen.  
  
 Místní statické objekty jsou při ukončení zrušeny pomocí `atexit`. Nebyl-li statický objekt vytvořen, protože průběh řízení aplikace obešel jeho deklaraci, není proveden žádný pokus o zrušení objektu.  
  
### <a name="static-local-variables"></a>Statické místní proměnné  
 V jazyce C++ místní proměnné může deklarovat jako statické. Proměnná je viditelná jen v rámci tělo funkce, ale pro všechny instance funkce existuje jenom jedna kopie proměnné.  
  
###  <a name="type_deduction"></a>Odvození typu v návratové typy (C ++ 14)  
 V C ++ 14, můžete použít `auto` kompilátoru odvodit návratový typ funkce subjektem, aniž byste museli zadat koncové návratový typ. Všimněte si, že `auto` vždy deduces na vrátit podle-hodnotu. Použití `auto&&` kompilátoru odvodit odkaz.  
  
 V tomto příkladu `auto` bude odvodit jako kopii součet lhs a rhs bez const hodnotu.  
  
```  
template<typename Lhs, typename Rhs>  
auto Add2(const Lhs& lhs, const Rhs& rhs)  
{  
    return lhs + rhs; //returns a non-const object by value  
}  
```  
  
 Všimněte si, že `auto` nezachovává const obchodní typu ho deduces. Pro předávání funkce, jejíž návratovou hodnotu musí zachovat const obchodní nebo ref obchodní argumentů, můžete použít `decltype(auto)` – klíčové slovo, které používá `decltype` odvození typu pravidla a se zachovají všechny informace o typu. `decltype(auto)`slouží jako obyčejnou návratovou hodnotu na levé straně, nebo jako koncové návratovou hodnotu.  
  
 Následující příklad (na základě kódu z [N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html)), znázorňuje `decltype(auto)` používaný k povolení ideální předávání argumenty funkce v návratový typ, který není znám, dokud je vytvořena instance šablony.  
  
```  
template<typename F, typename Tuple = tuple<T...>, int... I>  
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)   
{  
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);  
}  
  
template<typename F, typename Tuple = tuple<T...>,  
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>  
   decltype( auto)  
    apply(F&& f, Tuple&& args)      
{  
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());  
}  
}  
```  
## <a name="returning-multiple-values-from-a-function"></a>Vrátí více hodnot z funkce
Existují různé způsoby, jak vrátit více než jednu hodnotu z funkce:

1. Zapouzdření hodnoty v objektu s názvem třídě nebo struktuře. Vyžaduje definici třídě nebo struktuře být viditelná pro volající:

```cpp
#include <string>
#include <iostream>

using namespace std;

struct S
{
    string name;
    int num;
};

S g()
{
    string t{ "hello" };
    int u{ 42 };
    return { t, u };
}

int main()
{
    S s = g();
    cout << s.name << " " << s.num << endl;
    return 0;
}
```

2. Vrátí objekt std::tuple nebo std::pair:

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;


tuple<int, string, double> f()
{
    int i{ 108 };
    string s{ "Some text" };
    double d{ .01 };
    return { i,s,d };
}

int main()
{
    auto t = f();
    cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;
    
    // --or--

    int myval;
    string myname;
    double mydecimal;
    tie(myval, myname, mydecimal) = f();
    cout << myval << " " << myname << " " << mydecimal << endl;

    return 0;
}
```

3. **Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): použití strukturovaná vazby. Výhodou strukturovaných vazby je, že proměnné, které ukládají vrácené hodnoty jsou inicializovány ve stejnou dobu, které jsou deklarovány, což v některých případech může být výrazně efektivnější. V tomto prohlášení –`auto[x, y, z] = f();`– hranatých závorkách zavádět a inicializujte názvy, které jsou v oboru pro celý funkce blok.  

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;

tuple<int, string, double> f()
{
    int i{ 108 };
    string s{ "Some text" };
    double d{ .01 };
    return { i,s,d };
}
struct S
{
    string name;
    int num;
};

S g()
{
    string t{ "hello" };
    int u{ 42 };
    return { t, u };
}

int main()
{
    auto[x, y, z] = f(); // init from tuple
    cout << x << " " << y << " " << z << endl;

    auto[a, b] = g(); // init from POD struct
    cout << a << " " << b << endl;
    return 0;
}
```

4. Kromě používání návratovou hodnotu sám sebe, můžete "vrátit" hodnoty tak, že definujete libovolný počet parametrů k dispozici průchodu odkazem, takže můžete upravit nebo inicializovat hodnoty objekty, které poskytuje volající funkce. Další informace najdete v tématu [argumenty funkce typu odkazu](reference-type-function-arguments.md).
  
## <a name="function-pointers"></a>Ukazatele na funkce  
 C++ podporuje ukazatelů na funkce stejným způsobem jako jazyk C. Nicméně alternativní typově bezpečný je obvykle použít objekt funkce.  
  
 Deklarujete-li funkci vracející typ ukazatele na funkci, je doporučeno deklarovat pro typ ukazatele na funkci alias pomocí direktivy `typedef`.  Příklad  
  
```  
typedef int (*fp)(int);  
fp myFunction(char* s); // function returning function pointer  
```  
  
 Není-li toto provedeno, lze patřičnou syntaxi deklarace funkce odvodit ze syntaxe deklarátoru ukazatele na funkci nahrazením identifikátoru (`fp` v příkladu výše) názvem funkce a seznamem argumentů takto:  
  
```  
int (*myFunction(char* s))(int);  
```  
  
 Předchozí deklarace je ekvivalentem deklarace pomocí direktivy typedef výše.  
  
## <a name="see-also"></a>Viz také  
 [Přetížení funkce](../cpp/function-overloading.md)   
 [Funkce se seznamem argumentů proměnných](../cpp/functions-with-variable-argument-lists-cpp.md)   
 [Explicitně přednastavené a odstraněné funkce](../cpp/explicitly-defaulted-and-deleted-functions.md)   
 [Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)   
 [Výchozí argumenty](../cpp/default-arguments.md)   
 [Vložené funkce](../cpp/inline-functions-cpp.md)