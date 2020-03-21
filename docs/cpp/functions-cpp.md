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
ms.openlocfilehash: fbc8b108ea958f526156e7f81a75a2918a0a8903
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076162"
---
# <a name="functions-c"></a>Funkce (C++)

Funkce je blok kódu, který provádí určitou operaci. Funkce může volitelně definovat vstupní parametry, které umožňují volajícím předat argumenty do funkce. Funkce může volitelně vracet hodnotu jako výstup. Funkce jsou užitečné pro zapouzdření běžných operací v jednom opakovaně použitelném bloku, v ideálním případě s názvem, který jasně popisuje, co funkce dělá. Následující funkce přijímá dvě celá čísla od volajícího a vrací jejich součet; *a* a *b* jsou *parametry* typu **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Funkci lze vyvolat nebo *volat*z libovolného počtu míst v programu. Hodnoty, které jsou předány funkci, jsou *argumenty*, jejichž typy musí být kompatibilní s typy parametrů v definici funkce.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Neexistují žádné praktické omezení na délku funkce, ale dobrý návrh pro funkce, které provádějí jednu dobře definovanou úlohu. Složité algoritmy by se měly rozdělit na snadnou pochopení jednodušších funkcí, kdykoli to bude možné.

Funkce, které jsou definovány v oboru třídy, se nazývají členské funkce. V C++na rozdíl od jiných jazyků lze funkci také definovat v oboru oboru názvů (včetně implicitního globálního oboru názvů). Tyto funkce se nazývají *bezplatné funkce* nebo *nečlenské funkce*; používají se rozsáhle ve standardní knihovně.

Funkce mohou být *přetíženy*, což znamená, že různé verze funkce mohou sdílet stejný název, pokud se liší podle počtu nebo typu formálních parametrů. Další informace naleznete v tématu [přetížení funkce](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Části deklarace funkce

Minimální *deklarace* funkce se skládá z návratového typu, názvu funkce a seznamu parametrů (který může být prázdný), spolu s nepovinnými klíčovými slovy, které poskytují další pokyny pro kompilátor. Následující příklad je deklarace funkce:

```cpp
int sum(int a, int b);
```

Definice funkce se skládá z deklarace a *textu*, který je celý kód mezi složenými závorkami:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Deklarace funkce následovaná středníkem se může zobrazit na více místech programu. Musí se objevit před jakýmkoli voláním této funkce v každé jednotce překladu. Definice funkce se musí v programu objevit jenom jednou podle pravidla definice (ODR).

Požadované části deklarace funkce jsou:

1. Návratový typ, který určuje typ hodnoty vrácené funkcí nebo **void** , pokud není vrácena žádná hodnota. V jazyce C++ 11 je **automaticky** platný návratový typ, který instruuje kompilátor, aby odvodí typ z příkazu return. V jazyce C++ 14 je také povoleno decltype (auto). Další informace naleznete v části typ srážky v návratových typech níže.

1. Název funkce, která musí začínat písmenem nebo podtržítkem a nesmí obsahovat mezery. Obecně platí, že přední podtržítka v názvech funkcí standardních knihoven označují soukromé členské funkce nebo nečlenské funkce, které nejsou určeny pro použití ve vašem kódu.

1. Seznam parametrů, oddělený čárkami, sada nula nebo více parametrů, které určují typ a volitelně místní název, pomocí kterého lze k hodnotám přicházet uvnitř těla funkce.

Volitelné části deklarace funkce jsou:

1. `constexpr`, která označuje, že návratová hodnota funkce je konstantní hodnota může být počítána v době kompilace.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Její specifikace propojení, **extern** nebo **static**.

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Další informace naleznete v tématu [jednotky překladu a propojení](../cpp/program-and-linkage-cpp.md).

1. **inline**, který instruuje kompilátor, aby nahradil každé volání funkce samotným kódem funkce. vkládání může pomáhat s výkonem ve scénářích, kdy se funkce spouští rychle a je vyvolána opakovaně v části s kritickým výkonem kódu.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Další informace najdete v tématu [vložené funkce](../cpp/inline-functions-cpp.md).

1. Výraz `noexcept`, který určuje, zda funkce může vyvolat výjimku. V následujícím příkladu funkce nevyvolá výjimku, pokud je výraz `is_pod` vyhodnocen jako **true**.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Další informace najdete v tématu [s výjimkou](../cpp/noexcept-cpp.md).

1. (Jenom členské funkce) Kvalifikátory CV, které určují, zda je funkce **const** nebo **volatile**.

1. (Jenom členské funkce) **Virtual**, `override`nebo `final`. **Virtual** určuje, že funkci lze přepsat v odvozené třídě. `override` znamená, že funkce v odvozené třídě Přepisuje virtuální funkci. `final` znamená, že funkci nelze přepsat v žádné další odvozené třídě. Další informace najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).

1. (jenom členské funkce) **statické** použití na členskou funkci znamená, že funkce není přidružena k žádné instanci objektu třídy.

1. (Jenom nestatické členské funkce) Kvalifikátor ref, který určuje kompilátor, který má být vybrán, když implicitní parametr objektu (\*this) je odkaz rvalue a odkaz na lvalue. Další informace naleznete v tématu [přetížení funkce](function-overloading.md#ref-qualifiers).

Následující obrázek ukazuje části definice funkce. Šedivá oblast je tělo funkce.

![Části definice funkce](../cpp/media/vc38ru1.gif "Části definice funkce") <br/>
Části definice funkce

## <a name="function-definitions"></a>Definice funkcí

*Definice funkce* se skládá z deklarace a těla funkce uzavřené ve složených závorkách, které obsahují deklarace proměnných, příkazy a výrazy. Následující příklad ukazuje úplnou definici funkce:

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

Proměnné deklarované uvnitř těla jsou označovány jako lokální proměnné nebo místní. Po ukončení funkce přestanou být v rozsahu. Proto by funkce neměla nikdy vracet odkaz na místní!

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>funkce const a constexpr

Můžete deklarovat členskou funkci jako **const** k určení, že funkce nemá povoleno změnit hodnoty jakýchkoli datových členů ve třídě. Deklarováním členské funkce jako **const**pomůžete kompilátoru vynutili *konstantní správnost*. Pokud se někdo omylem pokusí změnit objekt pomocí funkce deklarované jako **const**, dojde k chybě kompilátoru. Další informace naleznete v tématu [const](const-cpp.md).

Deklarujete funkci jako `constexpr`, když hodnota, kterou vytváří, může být určena v době kompilace. Funkce constexpr obecně provádí rychlejší než normální funkce. Další informace naleznete v tématu [constexpr](constexpr-cpp.md).

## <a name="function-templates"></a>Šablony funkcí

Šablona funkce je podobná šabloně třídy; vygeneruje konkrétní funkce založené na argumentech šablony. V mnoha případech šablona dokáže odvodit argumenty typu, a proto není nutné je explicitně zadat.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Další informace najdete v tématu [šablony funkcí](../cpp/function-templates.md) .

## <a name="function-parameters-and-arguments"></a>Parametry funkce a argumenty

Funkce má seznam parametrů oddělených čárkami nula nebo více typů, z nichž každý má název, ke kterému lze přistupovat uvnitř těla funkce. Šablona funkce může určovat další parametry typu nebo hodnoty. Volající předává argumenty, které jsou konkrétními hodnotami, jejichž typy jsou kompatibilní se seznamem parametrů.

Ve výchozím nastavení jsou argumenty předány funkci podle hodnoty, což znamená, že funkce obdrží kopii předávaného objektu. V případě rozsáhlých objektů může být kopie náročná a není vždy nutná. Chcete-li způsobit předání argumentů odkazem (konkrétně odkaz lvalue), přidejte do parametru kvantifikátor odkazu:

```cpp
void DoSomething(std::string& input){...}
```

Když funkce upraví argument, který je předán odkazem, změní původní objekt, nikoli místní kopii. Chcete-li zabránit funkci v úpravách takového argumentu, kvalifikovat parametr jako typ const &:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Aby bylo možné explicitně zpracovat argumenty, které jsou předány odkazem rvalue-reference nebo lvalue-reference, použijte k označení univerzálního odkazu v parametru operátor Double:

```cpp
void DoSomething(const std::string&& input){...}
```

Funkce deklarovaná s jedním klíčovým slovem **void** v seznamu deklarací parametrů nepřijímá žádné argumenty, pokud klíčové slovo **void** je první a jediný člen seznamu deklarace argumentů. Argumenty typu **void** jinde v seznamu způsobují chyby. Příklad:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Všimněte si, že v případě, že je neplatné zadat argument **void** s výjimkou zde uvedené, typy odvozené z typu **void** (například ukazatelé na typ **void** a pole typu **void**) mohou být uvedeny kdekoli v seznamu deklarace argumentů.

### <a name="default-arguments"></a>Výchozí argumenty

K poslednímu parametru nebo parametrům v podpisu funkce lze přiřadit výchozí argument, což znamená, že volající může při volání funkce opustit argument, pokud nechtějí zadat jinou hodnotu.

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

Funkce nesmí vracet jinou funkci ani předdefinované pole; může však vracet ukazatele na tyto typy nebo *lambda*, který vytváří objekt funkce. S výjimkou těchto případů může funkce vracet hodnotu jakéhokoli typu, který je v oboru, nebo nemůže vracet žádnou hodnotu. v takovém případě návratový typ je **void**.

### <a name="trailing-return-types"></a>Koncové návratové typy

"Běžný" návratový typ se nachází na levé straně podpisu funkce. *Koncový návratový typ* je umístěn na pravé straně podpisu a předchází operátor->. Koncové návratové typy jsou obzvláště užitečné v šablonách funkcí, když typ návratové hodnoty závisí na parametrech šablony.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Pokud se používá **automaticky** ve spojení s koncovým návratovým typem, slouží pouze jako zástupný symbol pro jakékoli vytvoření výrazu decltype a sám neprovede odpočet typů.

## <a name="function-local-variables"></a>Místní proměnné funkce

Proměnná, která je deklarována uvnitř těla funkce, se nazývá *místní proměnná* nebo pouze *místní*. Nestatické lokální hodnoty jsou viditelné pouze uvnitř těla funkce a pokud jsou deklarovány v zásobníku, přecházejí mimo rozsah, když funkce skončí. Když vytvoříte místní proměnnou a vrátíte ji podle hodnoty, kompilátor může obvykle provést *optimalizaci pojmenované návratové hodnoty* , aby se předešlo zbytečným operacím kopírování. Pokud vrátíte místní proměnnou odkazem, kompilátor vydá upozornění, protože všechny pokusy volajícího k použití tohoto odkazu budou provedeny po zničení místní proměnné.

C++ Místní proměnná může být deklarována jako statická. Proměnná je viditelná pouze uvnitř těla funkce, ale jedna kopie proměnné existuje pro všechny instance funkce. Místní statické objekty jsou při ukončení zrušeny pomocí `atexit`. Nebyl-li statický objekt vytvořen, protože průběh řízení aplikace obešel jeho deklaraci, není proveden žádný pokus o zrušení objektu.

##  <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Srážky typu v návratových typech (C++ 14)

V C++ 14 můžete použít **auto** k instruování kompilátoru, aby odvodit návratový typ z těla funkce bez nutnosti zadat koncový návratový typ. Všimněte si, že **auto** vždy se odvodit na hodnotu vrácení podle hodnoty. Použijte `auto&&` k instruování kompilátoru, aby odvodit odkaz.

V tomto příkladu bude **automaticky** odvozena jako nekonstantní kopie hodnoty součtu LHS a zarovnání indirekce rhs.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Všimněte si, že **auto** nezachovává const-Ness typu, který se odvodit. Pro předávání funkcí, jejichž návratová hodnota musí zachovat const-Ness nebo ref-Ness svých argumentů, lze použít klíčové slovo **decltype (auto)** , které používá pravidla odvození typu **decltype** a uchovává všechny informace o typu. **decltype (auto)** se dá použít jako obvyklá návratová hodnota na levé straně nebo jako koncová návratová hodnota.

Následující příklad (založený na kódu z [N3493](https://wg21.link/n3493)) zobrazuje **decltype (auto)** , který se používá k umožnění dokonalého předávání argumentů funkce v návratovém typu, který není znám, dokud není vytvořena instance šablony.

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

1. Zapouzdřuje hodnoty v pojmenované třídě nebo objektu struktury. Vyžaduje, aby byla definice třídy nebo struktury viditelná pro volajícího:

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

1. Vrátí std:: Tuple nebo std::p Air objekt:

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

1. **Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): Používejte strukturované vazby. Výhodou strukturovaných vazeb je, že proměnné, které ukládají vrácené hodnoty, jsou inicializovány ve stejnou dobu, kdy jsou deklarovány, což v některých případech může být výrazně efektivnější. V tomto příkazu--`auto[x, y, z] = f();`-závorky zavádí a inicializuje názvy, které jsou v oboru pro celý blok funkce.

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

1. Kromě použití samotné návratové hodnoty můžete "vracet" hodnoty definováním libovolného počtu parametrů pro použití předávacího odkazu, aby funkce mohla upravovat nebo inicializovat hodnoty objektů, které poskytuje volající. Další informace naleznete v tématu [argumenty funkce typu odkazu](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Ukazatele na funkce

C++podporuje ukazatele na funkce stejným způsobem jako jazyk C. Nicméně další typově bezpečná alternativa obvykle používá objekt funkce.

Doporučuje se, aby se **definice typedef** použila k deklarování aliasu pro typ ukazatele na funkci, pokud deklarujete funkci, která vrací typ ukazatele na funkci.  Například

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
