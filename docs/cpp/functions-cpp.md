---
title: Funkce (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25172bc44c21fcb11ec3f7c77224d3214e21c5f2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404607"
---
# <a name="functions-c"></a>Funkce (C++)

Funkce je blok kódu, který provádí nějaké operace. Funkce Volitelně můžete definovat vstupní parametry, které umožňují volajícím předat argumenty do funkce. Funkce může volitelně vrátit hodnotu jako výstup. Funkce jsou užitečné pro zapouzdření běžných operací v jediné opakovaně použitelné bloku, v ideálním případě s názvem, který jasně popisuje, co funkce dělá. Následující funkce přijímá dvou celých čísel od volajícího a vrátí jejich součet; *a* a *b* jsou *parametry* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Funkci lze vyvolat, nebo *volá*, z různých míst v aplikaci. Hodnoty, které jsou předány do funkce jsou *argumenty*, jejichž typy musí být kompatibilní s typy parametrů v definici funkce.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Neexistuje žádné praktické omezení na délku funkce, ale dobrý návrh cíle na funkce, které provádějí jediné dobře definované úlohy. Složité algoritmy by měl být rozdělit do snadno pochopitelné jednodušší funkce kdykoli je to možné.

Funkce, které jsou definovány v oboru třídy jsou volány členské funkce. V jazyce C++ na rozdíl od jiných jazyků, funkce lze také definovat v oboru názvů (včetně implicitní globální obor názvů). Tyto funkce jsou volány *bezplatné funkce* nebo *nečlenské funkce*; se hojně používají ve standardní knihovně.

Funkce mohou mít *přetížené*, což znamená, že různé verze funkce může sdílet se stejným názvem, pokud se liší podle číslo nebo typ formálních parametrů. Další informace najdete v tématu [přetížení funkce](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Části deklarace funkce

Minimální funkce *deklarace* obsahuje návratový typ, název funkce a seznam parametrů (který může být prázdné), spolu s volitelné klíčová slova, které obsahují další pokyny pro kompilátor. V následujícím příkladu je deklarace funkce:

```cpp
int sum(int a, int b);
```

Definice funkce obsahuje deklarace, plus *tělo*, což je veškerý kód ve složených závorkách:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklarace funkce, za nímž následuje středníkem se můžou objevit na více místech v programu. Musí být uvedena před všechna volání této funkce v každé jednotce překladu. Definice funkce musí být uvedena pouze jednou v programu, podle jednoho pravidla definice (ODR).

Požadované části deklarace funkce jsou:

1. Návratový typ, který určuje typ, který funkce vrátí hodnotu, nebo **void** Pokud není vrácena žádná hodnota. V C ++ 11 **automaticky** platný návratový typ, který instruuje kompilátor, aby se odvodit typ z návratový příkaz. V C ++ 14 je také povolena položka decltype(auto). Další informace najdete v tématu odvození typu v Return Types.

1. Název funkce, které musí začínat písmenem nebo podtržítkem a nemůže obsahovat mezery. Obecně platí úvodní podtržítka v názvech funkce standardní knihovny označení private členské funkce nebo funkce bez členů, které nejsou určeny pro použití ve vašem kódu.

1. Seznam parametrů složenou závorku, oddělené čárkami sadu středníky nula nebo více parametrů, které určují typ a volitelně místní název, podle kterého hodnoty lze získat přístup uvnitř těla funkce.

Volitelné části deklarace funkce jsou:

1. `constexpr`, což znamená, že návratová hodnota funkce je konstantní hodnotu nelze vypočítat v době kompilace.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Specifikace propojení **extern** nebo **statické**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

     Další informace najdete v tématu [Program a propojení](../cpp/program-and-linkage-cpp.md).

1. **vložené**, který instruuje kompilátor, aby každé volání funkce nahraďte samotný kód funkce. vkládání může vám pomůže zvýšit výkon v situacích, kdy funkce rychle spustí a je vyvolána opakovaně v kritickém pro výkon část kódu.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

     Další informace najdete v tématu [vložené funkce](../cpp/inline-functions-cpp.md).

1. A `noexcept` výraz, který určuje, zda funkce může vyvolat výjimku. V následujícím příkladu se funkce nevyvolá výjimku pokud `is_pod` výraz vyhodnocen jako **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

     Další informace najdete v tématu [noexcept](../cpp/noexcept-cpp.md).

1. (Pouze pro členské funkce) Kvalifikátory cv, které určují, jestli je funkce **const** nebo **volatile**.

1. (Pouze pro členské funkce) **virtuální**, `override`, nebo `final`. **virtuální** Určuje, že funkci můžete přepsat v odvozené třídě. `override` znamená to, že je funkce v odvozené třídě přepisování virtuální funkce. `final` znamená, že funkce nelze přepsat v libovolné další odvozené třídy. Další informace najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).

1. (pouze pro členské funkce) **statické** použít na člen funkce znamená, že funkce není přidružené žádné instance objektů třídy.

1. (Pouze nestatických členských funkcí) Ref – kvalifikátor, který určuje kompilátoru, které přetížení dané funkci, kterou chcete vybrat, kdy se parametr implicitní objektu (\*to) je odkaz rvalue nebo odkaz na lvalue. Další informace najdete v tématu [přetížení funkce](function-overloading.md#ref-qualifiers).

Následující obrázek ukazuje části definice funkce. Vystínovaná oblast představuje tělo funkce.

 ![Části definice funkce](../cpp/media/vc38ru1.gif "vc38RU1") části definice funkce

## <a name="function-definitions"></a>Definice funkcí

A *funkce definice* obsahuje prohlášení a tělo funkce, ve složených závorkách, která obsahuje deklarace proměnných, příkazy a výrazy. Následující příklad ukazuje definici kompletní funkce:

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

Proměnné deklarované uvnitř těla označují jako lokální proměnné nebo místních hodnot. Dostanou mimo rozsah při ukončení funkce; funkce by měla vrátit proto nikdy odkaz na místní!

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>Funkce const nebo constexpr.

Můžete deklarovat členské funkce jako **const** k určení, že funkce nejsou povolené ke změně hodnot žádné datové členy třídy. Deklarováním jako členskou funkci **const**, pomáhají kompilátoru vynutit *správnost const*. Pokud někdo omylem pokusí úpravy objektu pomocí funkce deklarovaná jako **const**, vyvolá chybu kompilátoru. Další informace najdete v tématu [const](const-cpp.md).

Deklarování funkce jako `constexpr` když hodnota vytvoří pravděpodobně se dá určit v době kompilace. Funkce constexpr obecně je vyhodnocen rychleji než normální funkce. Další informace najdete v tématu [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Šablony funkcí

Šablonu funkce je podobný šablony třídy; generuje konkrétní funkce založený na argumentech šablony. V mnoha případech je možné odvodit argumenty typu šablony a proto není nutné explicitně zadávat.

```cpp
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

Funkce má seznam čárkami oddělených parametrů nula nebo více typů, z nichž každá má název, pomocí kterého byla přístupná uvnitř těla funkce. Šablona funkce může zadání dalších parametrů typem nebo hodnotou. Volající předá argumenty, které jsou konkrétní hodnoty, jejichž typy jsou kompatibilní se seznamem parametrů.

Výchozí argumenty jsou předány funkci podle hodnoty, což znamená, že funkce přijímá kopii objektu předávána. Pro velké objekty, vytvoření kopie může být nákladné a není vždy nutné. Způsobí argumenty, které mají být předány podle odkazu (konkrétně odkaz l-hodnota), přidejte odkaz kvantifikátor parametru:

```cpp
void DoSomething(std::string& input){...}
```

Pokud funkce upraví argument, který se předá odkazem, upraví původní objekt místní kopii. Chcete-li zabránit ve změně těchto argumentů funkce, kvalifikovat parametr jako const &:

```cpp
void DoSomething(const std::string& input){...}
```

 **Jazyk C++ 11:** explicitně zpracování argumentů, které jsou předávány odkaz rvalue nebo odkaz na lvalue, pomocí double-ampersand u parametru určíte univerzální odkaz:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkce deklarovaná pomocí jednoho klíčového slova **void** v deklaraci parametru seznamu nepřijímá žádné argumenty, pokud je klíčové slovo **void** je prvním a jediným členem seznamu deklarace argumentů. Argumenty typu **void** jinde v seznamu způsobí chyby. Příklad:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Všimněte si, že i když je neplatné zadat **void** argument s výjimkou uvedenou zde, typy odvozené z typu **void** (například ukazatele na **void** a pole **void**) se může objevit kdekoli v seznamu deklarace argumentů.

### <a name="default-arguments"></a>Výchozí argumenty

Poslední parametrem nebo parametry v signatuře funkce může být přiřazen výchozí argument, což znamená, že volající může vynechat argument při volání funkce, pokud se chcete zadat jinou hodnotu.

```cpp
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

Funkce nesmí vracet jiné funkci nebo předdefinované pole. však může vrátit odkazy na tyto typy nebo *lambda*, která vytvoří objekt funkce. Kromě těchto případech funkce může vrátit hodnotu typu, který je v oboru nebo ji může vracet žádnou hodnotu, v takovém případě návratový typ je **void**.

### <a name="trailing-return-types"></a>Koncové návratové typy

"Běžné" návratový typ je umístěná na levé straně signatura funkce. A *koncovým návratovým typem* se nachází na pravé straně většina podpisu a předchází -> – operátor. Koncové návratové typy jsou zvláště užitečné v rámci šablony funkce, když typ vrácené hodnoty, závisí na parametry šablony.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Když **automaticky** se používá ve spojení s koncovým návratovým typem, stačí slouží jako zástupný symbol pro libovolné decltype výraz vytvoří a sám není provádí odvození typu.


## <a name="function-local-variables"></a>Lokální proměnné – funkce

Proměnná, která je deklarována uvnitř těla funkce se volá *lokální proměnná* nebo jednoduše *místní*. Místní hodnoty nestatických viditelné pouze uvnitř těla funkce a pokud jsou deklarovány v zásobníku dostanou mimo rozsah při ukončení funkce. Při vytvoření místní proměnné a vrácení podle hodnoty, kompilátor může obvykle provádět optimalizaci návratovou hodnotu, aby operace zbytečnému kopírování. Pokud vrátíte lokální proměnná podle odkazu, kompilátor vygeneruje upozornění, protože jakýkoliv pokus o volajícím použít tento odkaz dojde po zlikvidování místní.

V jazyce C++ mohou být deklarovány místní proměnné jako statické. Proměnná je viditelná jen v uvnitř těla funkce, ale pro všechny instance funkce existuje jedna kopie proměnné. Místní statické objekty jsou při ukončení zrušeny pomocí `atexit`. Nebyl-li statický objekt vytvořen, protože průběh řízení aplikace obešel jeho deklaraci, není proveden žádný pokus o zrušení objektu.

##  <a name="type_deduction"></a> Odvození typu v návratové typy (C ++ 14)

V C ++ 14, můžete použít **automaticky** abyste instruovali kompilátor odvodit návratový typ z těla funkce bez zadání koncovým návratovým typem. Všimněte si, že **automaticky** vždy odvodí k vrácení podle hodnot. Použití `auto&&` abyste instruovali kompilátor k odvození odkaz.

V tomto příkladu **automaticky** jako kopii nekonstantní hodnotu Součet lhs a zarovnání indirekce rhs se dá odvodit.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Všimněte si, že **automaticky** const-ness typu odvodí se nezachová. Pro předávání, vrácená hodnota je potřeba zachovat const-ness nebo ref-ness z jejích argumentů funkce, můžete použít **decltype(auto)** – klíčové slovo, které používá **decltype** zadejte pravidla odvozování a uchovává všechny informace o typu. **Položka decltype(Auto)** může sloužit jako běžný návratovou hodnotu na levé straně, nebo jako koncové návratové hodnoty.

Následující příklad (na základě kódu z [N3493](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2013/n3493.html)), zobrazí **decltype(auto)** používá k umožnění dokonalé předávání argumentů funkce v návratovém typu, který není znám, dokud se šablony vytvořit instanci.

```cpp
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

1. Zapouzdření hodnoty v objektu s názvem třídy nebo struktury. Vyžaduje definici třídy nebo struktury viditelný pro volající:

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
    
1. Vrátí objekt std::tuple nebo std::pair:

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

1. **Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): použijte strukturované vazby. Výhodou strukturované vazby je, že proměnné, které ukládají vrácené hodnoty jsou inicializovány ve stejnou dobu, které jsou deklarovány, což v některých případech může být mnohem efektivnější. V tomto prohlášení –`auto[x, y, z] = f();`--závorky představují a inicializována názvy, které jsou v oboru pro daný blok celou funkci.

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
    
1. Kromě použití samotnou návratovou hodnotu, můžete "vrátit" hodnoty tak, že definujete libovolný počet parametry se mají použít pass-by-reference, takže můžete upravit nebo inicializace hodnoty objekty, které poskytuje volající funkci. Další informace najdete v tématu [argumenty funkce typu odkazu](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Ukazatele na funkce

Jazyk C++ podporuje stejným způsobem jako jazyk C ukazatelů na funkce. Ale více typově bezpečné alternativou je obvykle použití objektu funkce.

Dále je doporučeno **typedef** použít k deklarování aliasu pro typ ukazatele na funkci, pokud deklarace funkce vracející typ ukazatele funkce.  Příklad

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Není-li toto provedeno, lze patřičnou syntaxi deklarace funkce odvodit ze syntaxe deklarátoru ukazatele na funkci nahrazením identifikátoru (`fp` v příkladu výše) názvem funkce a seznamem argumentů takto:

```cpp
int (*myFunction(char* s))(int);
```

Předchozí deklarace je ekvivalentem deklarace pomocí direktivy typedef výše.

## <a name="see-also"></a>Viz také:
 [Přetížení funkce](../cpp/function-overloading.md)  
 [Funkce se seznamy argumentů proměnných](../cpp/functions-with-variable-argument-lists-cpp.md)  
 [Explicitně přednastavené a odstraněné funkce](../cpp/explicitly-defaulted-and-deleted-functions.md)  
 [Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)  
 [Výchozí argumenty](../cpp/default-arguments.md)  
 [Vložené funkce](../cpp/inline-functions-cpp.md)
