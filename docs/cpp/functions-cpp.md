---
title: Funkce (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 1425ddebffc150158e88e44b1d2c22e3f85e5a31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375741"
---
# <a name="functions-c"></a>Funkce (C++)

Funkce je blok kódu, který provádí některé operace. Funkce může volitelně definovat vstupní parametry, které umožňují volajícím předat argumenty do funkce. Funkce může volitelně vrátit hodnotu jako výstup. Funkce jsou užitečné pro zapouzdření běžných operací do jednoho opakovaně použitelného bloku, ideálně s názvem, který jasně popisuje, co funkce dělá. Následující funkce přijme dvě celá čísla od volajícího a vrátí jejich součet; *a* a *b* jsou *parametry* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Funkce může být vyvolána nebo *volána*z libovolného počtu míst v programu. Hodnoty, které jsou předány funkci jsou *argumenty*, jejichž typy musí být kompatibilní s typy parametrů v definici funkce.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Neexistuje žádné praktické omezení délky funkce, ale dobrý návrh se zaměřuje na funkce, které provádějí jeden dobře definovaný úkol. Složité algoritmy by měly být rozděleny do snadno pochopit jednodušší funkce, kdykoli je to možné.

Funkce, které jsou definovány v oboru třídy se nazývají členské funkce. V jazyce C++ lze na rozdíl od jiných jazyků definovat funkci také v oboru oboru názvů (včetně implicitního globálního oboru názvů). Tyto funkce se nazývají *volné funkce* nebo *nečlenské funkce*; jsou široce používány ve standardní knihovně.

Funkce mohou být *přetíženy*, což znamená, že různé verze funkce mohou sdílet stejný název, pokud se liší počtem nebo typem formálních parametrů. Další informace naleznete v [tématu Přetížení funkce](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Části prohlášení o funkci

Minimální *deklarace* funkce se skládá z návratového typu, názvu funkce a seznamu parametrů (který může být prázdný) spolu s volitelnými klíčovými slovy, které poskytují kompilátoru další pokyny. Následující příklad je deklarace funkce:

```cpp
int sum(int a, int b);
```

Definice funkce se skládá z deklarace plus *tělo*, což je veškerý kód mezi složenými závorkami:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklarace funkce následovaná středníkem se může v programu objevit na více místech. Musí se objevit před voláním této funkce v každé jednotce překladu. Definice funkce se musí v programu objevit pouze jednou podle pravidla jedné definice (ODR).

Požadované části deklarace funkce jsou:

1. Návratový typ, který určuje typ hodnoty, kterou funkce vrátí, nebo **void,** pokud není vrácena žádná hodnota. V jazyce C++ 11 **auto** je platný návratový typ, který instruuje kompilátor odvodit typ z příkazu return. V jazyce C++14 decltype(auto) je také povoleno. Další informace naleznete v tématu Typ odpočet v návratové typy níže.

1. Název funkce, který musí začínat písmenem nebo podtržítkem a nesmí obsahovat mezery. Obecně platí, že úvodní podtržítka v názvech funkcí standardní knihovny označují soukromé členské funkce nebo nečlenské funkce, které nejsou určeny pro použití vaším kódem.

1. Seznam parametrů, složená závorka oddělená, sada nula nebo více parametrů oddělených čárkami, které určují typ a volitelně místní název, podle kterého mohou být hodnoty přístupné uvnitř těla funkce.

Nepovinné části deklarace funkce jsou:

1. `constexpr`, což znamená, že vrácená hodnota funkce je konstantní hodnota může být vypočítána v době kompilace.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Jeho propojení specifikace, **extern** nebo **statické**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Další informace naleznete v [tématu Překlad jednotek a propojení](../cpp/program-and-linkage-cpp.md).

1. **inline**, který instruuje kompilátor, aby nahradil každé volání funkce samotným kódem funkce. vkládání může pomoci výkon ve scénářích, kde funkce se spustí rychle a je vyvolána opakovaně v části kódu kritické pro výkon.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Další informace naleznete [v tématu Inline Functions](../cpp/inline-functions-cpp.md).

1. Výraz, `noexcept` který určuje, zda funkce může vyvolat výjimku. V následujícím příkladu funkce nevyvolá výjimku, pokud `is_pod` výraz vyhodnotí na **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Další informace naleznete v [tématu noexcept](../cpp/noexcept-cpp.md).

1. (Pouze členské funkce) Cv-qualifiers, které určují, zda je funkce **const** nebo **volatile**.

1. (Pouze členské funkce) **virtuální** `override`, `final`nebo . **virtual** určuje, že funkci lze přepsat v odvozené třídě. `override`znamená, že funkce v odvozené třídě přepíše virtuální funkci. `final`znamená, že funkci nelze přepsat v žádné další odvozené třídě. Další informace naleznete v [tématu Virtuální funkce](../cpp/virtual-functions.md).

1. (pouze členské funkce) **static applied** to a member function znamená, že funkce není přidružena k žádným instancím objektu třídy.

1. (Pouze nestatické členské funkce) Ref-qualifier, který určuje kompilátoru, které přetížení funkce zvolit, když\*implicitní parametr objektu (to) je rvalue odkaz vs lvalue odkaz. Další informace naleznete v [tématu Přetížení funkce](function-overloading.md#ref-qualifiers).

Následující obrázek znázorňuje části definice funkce. Stínovaná oblast je tělo funkce.

![Části definice funkce](../cpp/media/vc38ru1.gif "Části definice funkce") <br/>
Části definice funkce

## <a name="function-definitions"></a>Definice funkcí

*Definice funkce* se skládá z deklarace a tělo funkce, uzavřené ve složených závorkách, který obsahuje deklarace proměnných, příkazy a výrazy. Následující příklad ukazuje úplnou definici funkce:

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

Proměnné deklarované uvnitř těla se nazývají místní proměnné nebo místní. Jdou mimo rozsah při ukončení funkce; proto funkce by nikdy vrátit odkaz na místní!

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>const a constexpr funkce

Můžete deklarovat členská funkce jako **const** určit, že funkce není povoleno měnit hodnoty všech datových členů ve třídě. Deklarováním členské funkce jako **const**pomůžete kompilátoru vynutit *správnost const*. Pokud se někdo omylem pokusí upravit objekt pomocí funkce deklarované jako **const**, je vyvolána chyba kompilátoru. Další informace naleznete [v tématu const](const-cpp.md).

Deklarovat `constexpr` funkci, jako když hodnota, kterou vytváří lze případně určit v době kompilace. Funkce constexpr se obvykle provádí rychleji než běžná funkce. Další informace naleznete [v tématu constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Šablony funkcí

Šablona funkce je podobná šabloně třídy; generuje konkrétní funkce založené na argumentech šablony. V mnoha případech je šablona schopna odvodit argumenty typu, a proto není nutné je explicitně specifikovat.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Další informace naleznete v [tématu Šablony funkcí](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Parametry a argumenty funkce

Funkce má seznam parametrů oddělených čárkami nula nebo více typů, z nichž každý má název, podle kterého je přístupný uvnitř těla funkce. Šablona funkce může určit další parametry typu nebo hodnoty. Volající předá argumenty, které jsou konkrétní hodnoty, jejichž typy jsou kompatibilní se seznamem parametrů.

Ve výchozím nastavení jsou argumenty předány funkci hodnotou, což znamená, že funkce obdrží kopii předávaného objektu. U velkých objektů může být vytvoření kopie nákladné a není vždy nutné. Chcete-li způsobit, že argumenty mají být předány odkazem (konkrétně odkaz lvalue), přidejte k parametru referenční kvantifikátor:

```cpp
void DoSomething(std::string& input){...}
```

Když funkce upraví argument, který je předán odkazem, změní původní objekt, nikoli místní kopii. Chcete-li funkci zabránit v úpravě takového argumentu, kvalifikujte parametr jako const&:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Chcete-li explicitně zpracovat argumenty, které jsou předány rvalue-reference nebo lvalue-reference, použijte double-ampersand na parametr k označení univerzální odkaz:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkce deklarovaná s jediným klíčovým slovem **void** v seznamu deklarací parametrů nepřijímá žádné argumenty, pokud je klíčové slovo **void** prvním a jediným členem seznamu deklarací argumentů. Argumenty typu **void** jinde v seznamu vytvářejí chyby. Příklad:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Všimněte si, že i když je nezákonné zadat **argument void** s výjimkou, jak je zde uvedeno, typy odvozené z typu **void** (například ukazatele **void** a pole **void**) se mohou objevit kdekoli v seznamu deklarace argumentu.

### <a name="default-arguments"></a>Výchozí argumenty

Poslední parametr nebo parametry v podpisu funkce může být přiřazen výchozí argument, což znamená, že volající může vynechat argument při volání funkce, pokud chcete zadat jinou hodnotu.

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

Další informace naleznete [v tématu Výchozí argumenty](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Návratové typy funkcí

Funkce nemusí vrátit jinou funkci nebo vestavěné pole; však může vrátit ukazatele na tyto typy nebo *lambda*, který vytváří objekt funkce. S výjimkou těchto případů funkce může vrátit hodnotu libovolného typu, který je v oboru, nebo může vrátit žádnou hodnotu, v takovém případě je **návratový**typ void .

### <a name="trailing-return-types"></a>Koncové návratové typy

"Obyčejný" návratový typ je umístěn na levé straně podpisu funkce. Koncový *návratový typ* je umístěn na pravé straně podpisu a předchází operátor ->. Koncové návratové typy jsou užitečné zejména v šablonách funkcí, když typ vrácené hodnoty závisí na parametrech šablony.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Při **auto** se používá ve spojení s koncové návratový typ, slouží pouze jako zástupný symbol pro bez ohledu decltype výraz produkuje a neprovádí odpočet typu.

## <a name="function-local-variables"></a>Funkce místníproměnné

Proměnná, která je deklarována uvnitř těla funkce, se nazývá *místní proměnná* nebo jednoduše *místní*. Nestatické locals jsou viditelné pouze uvnitř těla funkce a pokud jsou deklarovány v zásobníku přejít mimo rozsah při ukončení funkce. Když vytvoříte místní proměnnou a vrátíte ji podle hodnoty, kompilátor může obvykle provést *optimalizaci pojmenované vrácené hodnoty,* aby se zabránilo zbytečným operacím kopírování. Pokud vrátíte místní proměnnou odkazem, kompilátor vydá upozornění, protože jakýkoli pokus volajícího o použití tohoto odkazu nastane po místní byl zničen.

V jazyce C++ může být místní proměnná deklarována jako statická. Proměnná je viditelná pouze uvnitř těla funkce, ale pro všechny instance funkce existuje jedna kopie proměnné. Místní statické objekty jsou při ukončení zrušeny pomocí `atexit`. Nebyl-li statický objekt vytvořen, protože průběh řízení aplikace obešel jeho deklaraci, není proveden žádný pokus o zrušení objektu.

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Odpočet typu v návratových typech (C++14)

V jazyce C++ 14 můžete použít **auto** pokyn kompilátor odvodit návratový typ z těla funkce bez nutnosti poskytnout koncový návratový typ. Všimněte si, že **auto** vždy odvodí na return-by-value. Slouží `auto&&` k pokynu kompilátoru, aby odvodil odkaz.

V tomto příkladu bude **auto** odvozeno jako kopie neconst hodnoty součtu lhs a rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Všimněte si, že **auto** nezachová const-ness typu, který odvodí. Pro předávání funkcí, jejichž vrácená hodnota potřebuje zachovat const-ness nebo ref-ness jeho argumentů, můžete použít **decltype(auto)** klíčové slovo, které používá **deklartyp typu** odvození pravidla a zachová všechny informace o typu. **decltype(auto)** lze použít jako běžnou vrácenou hodnotu na levé straně nebo jako koncové vrácené hodnoty.

Následující příklad (na základě kódu z [N3493](https://wg21.link/n3493)), ukazuje **decltype(auto)** se používá k povolení dokonalé předávání argumentů funkce v návratový typ, který není znám, dokud je vytvořena instance šablony.

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
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>Vrácení více hodnot z funkce

Existují různé způsoby, jak vrátit více než jednu hodnotu z funkce:

1. Zapouzdřit hodnoty v pojmenované třídě nebo struktuře objektu. Vyžaduje, aby definice třídy nebo struktury byla viditelná volajícímu:

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

1. Vrátí std::n-tice nebo std::pair objekt:

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

1. **Visual Studio 2017 verze 15.3 a novější** (k dispozici s [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Použití strukturovaných vazeb. Výhodou strukturovaných vazeb je, že proměnné, které ukládají vrácené hodnoty, jsou inicializovány současně s jejich deklarací, což může být v některých případech výrazně efektivnější. V tomto`auto[x, y, z] = f();`příkazu -- -- závorky zavést a inicializovat názvy, které jsou v oboru pro celý blok funkce.

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

1. Kromě použití samotné vrácené hodnoty můžete "vrátit" hodnoty definováním libovolného počtu parametrů, které mají být používány pass-by-reference tak, aby funkce můžete upravit nebo inicializovat hodnoty objektů, které volající poskytuje. Další informace naleznete [v tématu Reference-Type Function Arguments](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Ukazatele funkcí

C++ podporuje ukazatele funkce stejným způsobem jako jazyk C. Alternativou, která je bezpečnější jako typ, je však obvykle použití objektu funkce.

Doporučuje se, aby **typedef** použít k deklarování alias pro typ ukazatele funkce, pokud deklaruje funkci, která vrací typ ukazatele funkce.  Například

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Není-li toto provedeno, lze patřičnou syntaxi deklarace funkce odvodit ze syntaxe deklarátoru ukazatele na funkci nahrazením identifikátoru (`fp` v příkladu výše) názvem funkce a seznamem argumentů takto:

```cpp
int (*myFunction(char* s))(int);
```

Předchozí deklarace je ekvivalentem deklarace pomocí direktivy typedef výše.

## <a name="see-also"></a>Viz také

[Přetížení funkce](../cpp/function-overloading.md)<br/>
[Funkce se seznamy argumentů proměnných](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[Explicitně přednastavené a odstraněné funkce](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[Výchozí argumenty](../cpp/default-arguments.md)<br/>
[Vložené funkce](../cpp/inline-functions-cpp.md)
