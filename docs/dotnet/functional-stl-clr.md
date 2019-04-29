---
title: functional (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
ms.openlocfilehash: f4a99ea972c6d2ea9b9721664cc75dec257fd7b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393750"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

Zahrnout záhlaví STL/CLR `<cliext/functional>` definovat počet šablony třídy a delegáti související šablony a funkce.

## <a name="syntax"></a>Syntaxe

```
#include <functional>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / funkční >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Delegát|Popis|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|Delegát dvěma argumenty.|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Dvěma argumenty delegáta vrací **void**.|
|[unary_delegate (STL/CLR)](#unary_delegate)|Jednoargumentové delegáta.|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|Jednoargumentové delegáta vrací **void**.|

|Třída|Popis|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|Funktor, který se má negovat funktor dvěma argumenty.|
|[binder1st (STL/CLR)](#binder1st)|Funktor k vytvoření vazby prvního argumentu funktor dvěma argumenty.|
|[binder2nd (STL/CLR)](#binder2nd)|Funktor k vytvoření vazby druhého argumentu funktor dvěma argumenty.|
|[divides (STL/CLR)](#divides)|Rozdělte funktor.|
|[equal_to (STL/CLR)](#equal_to)|Porovnání rovna funktor.|
|[greater (STL/CLR)](#greater)|Větší porovnání funktor.|
|[greater_equal (STL/CLR)](#greater_equal)|Porovnání větší nebo rovna funktor.|
|[less (STL/CLR)](#less)|Méně porovnání funktor.|
|[less_equal (STL/CLR)](#less_equal)|Menší než nebo rovné porovnání funktor.|
|[logical_and (STL/CLR)](#logical_and)|Logické a funktor.|
|[logical_not (STL/CLR)](#logical_not)|Logické ne funktor.|
|[logical_or (STL/CLR)](#logical_or)|Logický OR funktor.|
|[minus (STL/CLR)](#minus)|Odečte funktor.|
|[modulus (STL/CLR)](#modulus)|MODULUS funktor.|
|[multiplies (STL/CLR)](#multiplies)|Vynásobte funktor.|
|[negate (STL/CLR)](#negate)|Funktor vrátit argument negovat.|
|[not_equal_to (STL/CLR)](#not_equal_to)|Není rovno porovnání funktor.|
|[plus (STL/CLR)](#plus)|Přidáte funktor.|
|[unary_negate (STL/CLR)](#unary_negate)|Funktor, který se má negovat funktor jedním argumentem.|

|Funkce|Popis|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|Generuje binder1st – argument a funktor.|
|[bind2nd (STL/CLR)](#bind2nd)|Generuje binder2nd – argument a funktor.|
|[not1 (STL/CLR)](#not1)|Generuje unary_negate – pro funktor.|
|[not2 (STL/CLR)](#not2)|Generuje binary_negate – pro funktor.|

## <a name="members"></a>Členové

## <a name="binary_delegate"></a> binary_delegate – (STL/CLR)

Třída genereic popisuje dvěma argumenty delegáta. Můžete ji použít delegátu, co se týče její argument a návratovým typem.

### <a name="syntax"></a>Syntaxe

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parametry

*arg1*<br/>
Typ prvního argumentu.

*arg2*<br/>
Typ druhého argumentu.

*výsledek*<br/>
Návratový typ.

### <a name="remarks"></a>Poznámky

Delegát genereic popisuje funkci se dvěma argumenty.

Všimněte si, že pro:

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

typy `Fun1` a `Fun2` jsou synonyma, zatímco pro:

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

nejsou stejného typu.

### <a name="example"></a>Příklad

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn – (STL/CLR)

Třída genereic popisuje dvěma argumenty delegáta, který vrátí **void**. Můžete ji použít delegátu, co se týče svého argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>Parametry

*arg1*<br/>
Typ prvního argumentu.

*arg2*<br/>
Typ druhého argumentu.

### <a name="remarks"></a>Poznámky

Popisuje dvěma argumenty funkci, která vrací delegáta genereic **void**.

Všimněte si, že pro:

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

typy `Fun1` a `Fun2` jsou synonyma, zatímco pro:

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

nejsou stejného typu.

### <a name="example"></a>Příklad

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate"></a> binary_negate – (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí logické ne z jeho uložených funktor dvěma argumenty. Můžete ji použít, zadejte objekt funkce z hlediska jeho uložené funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zábava*<br/>
Typ uložené funktor.

## <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|
|stored_function_type|Typ funktor.|

|Člen|Popis|
|------------|-----------------|
|binary_negate|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^()|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje dvěma argumenty funktor, který ukládá další funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí logické nejsou uložené funktor volat se dvěma argumenty.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st"></a> bind1st – (STL/CLR)

Generuje `binder1st` argument a funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>Parametry šablony

*arg*<br/>
Typ argumentu.

*Zábava*<br/>
Typ funktor.

#### <a name="function-parameters"></a>Parametry funkce

*funktor*<br/>
Funktor zabalit.

*doleva*<br/>
První argument zabalit.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [binder1st – (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Můžete použít jako pohodlný způsob, jak zabalit funktor dvěma argumenty a svůj první argument v jednoargumentové funktor, který ji volá jako druhý argument.

### <a name="example"></a>Příklad

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd"></a> bind2nd – (STL/CLR)

Generuje `binder2nd` argument a funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>Parametry šablony

*arg*<br/>
Typ argumentu.

*Zábava*<br/>
Typ funktor.

#### <a name="function-parameters"></a>Parametry funkce

*funktor*<br/>
Funktor zabalit.

*doprava*<br/>
Druhý argument zabalit.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [binder2nd – (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Můžete použít jako pohodlný způsob, jak zabalit funktor dvěma argumenty a druhý argument do jednoargumentové funktor, který zavolá se první argument.

### <a name="example"></a>Příklad

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st"></a> binder1st – (STL/CLR)

Třída šablony popisuje jednoargumentové funktor, který po zavolání vrátí jeho uložené funktor dvěma argumenty volat uloženou první argument a druhý zadaný argument. Můžete ji použít, zadejte objekt funkce z hlediska jeho uložené funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zábava*<br/>
Typ uložené funktor.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|
|stored_function_type|Typ funktor.|

|Člen|Popis|
|------------|-----------------|
|binder1st|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^()|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje jednoargumentové funktor, který ukládá funktor dvěma argumenty a jako první argument. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí výsledek volání uložené funktor uložené první argument a druhý zadaný argument.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd"></a> binder2nd – (STL/CLR)

Třída šablony popisuje jednoargumentové funktor, který po zavolání vrátí jeho uložené funktor dvěma argumenty volat s první zadaný argument a jeho uložené druhý argument. Můžete ji použít, zadejte objekt funkce z hlediska jeho uložené funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zábava*<br/>
Typ uložené funktor.

## <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|
|stored_function_type|Typ funktor.|

|Člen|Popis|
|------------|-----------------|
|binder2nd|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^()|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje jednoargumentové funktor, který ukládá funktor dvěma argumenty a druhý argument. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí výsledek volání uložené funktor zadaný první argument a uložené druhý argument.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides"></a> vydělí (STL/CLR)

Třída šablony popisuje funktor, který, při volání vrátí hodnotu prvního argumentu děleného po sekundách. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů a vrácené hodnoty.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|divides|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^()|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí prvního argumentu děleného po sekundách.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to"></a> equal_to – (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true pouze v případě, že první argument je roven druhému. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|equal_to|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^()|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud první argument je roven druhému.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater"></a> větší (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true, pouze pokud je první argument větší než druhý. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|greater|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud je první argument větší než druhý.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal"></a> greater_equal – (STL/CLR)

Třída šablony popisuje funktor, který, při volání, vrací hodnotu true, pouze pokud je první argument větší než nebo roven druhému. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|greater_equal|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud je první argument větší než nebo roven druhému.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less"></a> menší (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true, pouze pokud je první argument menší než druhý. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|less|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud je první argument menší než druhý.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal"></a> less_equal – (STL/CLR)

Třída šablony popisuje funktor, který, při volání, vrací hodnotu true, pouze pokud je první argument menší než druhý. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|less_equal|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud je první argument menší než druhý.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and"></a> logical_and – (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true pouze v případě, že první argument a druhý test jako true. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|logical_and|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud první argument a druhý test jako true.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not"></a> logical_not – (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true, pouze pokud její argument testuje hodnotu false. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|argument_type|Typ argumentu funktor.|
|delegate_type|Typ obecného delegátu.|
|result_type|Typ výsledku funktor.|

|Člen|Popis|
|------------|-----------------|
|logical_not|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor jedním argumentem. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud její argument testuje hodnotu false.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or"></a> logical_or – (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true pouze v případě, že argument první nebo druhé testy jako true. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|logical_or|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud první argument nebo druhý testy jako true.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus"></a> minus (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí první argument minus druhé. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů a vrácené hodnoty.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|minus|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí první argument minus druhé.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus"></a> modulo (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí první argument modulo druhé. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů a vrácené hodnoty.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|modulus|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí první argument modulo druhé.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies"></a> Vynásobí (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí první argument doby druhé. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů a vrácené hodnoty.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|multiplies|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí první argument doby druhé.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate"></a> negate – (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí svůj argument negovat. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|argument_type|Typ argumentu funktor.|
|delegate_type|Typ obecného delegátu.|
|result_type|Typ výsledku funktor.|

|Člen|Popis|
|------------|-----------------|
|negate|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor jedním argumentem. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí svůj argument negovat.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to"></a> not_equal_to – (STL/CLR)

Třída šablony popisuje funktor, že při volání vrátí hodnotu true, pouze pokud první argument není roven druhému. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|not_equal_to|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí hodnotu true pouze pokud první argument není roven druhému.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1"></a> not1 – (STL/CLR)

Generuje `unary_negate` pro funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>Parametry šablony

*Zábava*<br/>
Typ funktor.

#### <a name="function-parameters"></a>Parametry funkce

*funktor*<br/>
Funktor zabalit.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [unary_negate – (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`. Můžete použít jako pohodlný způsob, jak zabalit funktor jedním argumentem v funktor, který zajišťuje jeho logický operátor NOT.

### <a name="example"></a>Příklad

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2"></a> not2 – (STL/CLR)

Generuje `binary_negate` pro funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>Parametry šablony

*Zábava*<br/>
Typ funktor.

#### <a name="function-parameters"></a>Parametry funkce

*funktor*<br/>
Funktor zabalit.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [binary_negate – (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`. Můžete použít jako pohodlný způsob, jak zabalit funktor dvěma argumenty v funktor, který zajišťuje jeho logický operátor NOT.

### <a name="example"></a>Příklad

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus"></a> plus (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí první argument a druhý. Můžete ji použít, zadejte objekt funkce z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentů a vrácené hodnoty.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|delegate_type|Typ obecného delegátu.|
|first_argument_type|Typ prvního argumentu funktor.|
|result_type|Typ výsledku funktor.|
|second_argument_type|Typ druhého argumentu funktor.|

|Člen|Popis|
|------------|-----------------|
|plus|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|operator delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje funktor dvěma argumenty. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí první argument a druhý.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate"></a> unary_delegate – (STL/CLR)

Třída genereic popisuje jeden argument delegáta. Můžete ji použít delegátu, co se týče její argument a návratovým typem.

### <a name="syntax"></a>Syntaxe

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentu.

*výsledek*<br/>
Návratový typ.

### <a name="remarks"></a>Poznámky

Delegát genereic popisuje funkci jedním argumentem.

Všimněte si, že pro:

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

typy `Fun1` a `Fun2` jsou synonyma, zatímco pro:

`delegate int Fun1(int);`

`delegate int Fun2(int);`

nejsou stejného typu.

### <a name="example"></a>Příklad

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn – (STL/CLR)

Třída genereic popisuje jeden argument delegáta, který vrátí **void**. Můžete ji použít delegátu, z hlediska jeho typ argumentu.

### <a name="syntax"></a>Syntaxe

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>Parametry

*arg*<br/>
Typ argumentu.

### <a name="remarks"></a>Poznámky

Popisuje jedním argumentem funkce, která vrací delegáta genereic **void**.

Všimněte si, že pro:

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

typy `Fun1` a `Fun2` jsou synonyma, zatímco pro:

`delegate void Fun1(int);`

`delegate void Fun2(int);`

nejsou stejného typu.

### <a name="example"></a>Příklad

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate"></a> unary_negate – (STL/CLR)

Třída šablony popisuje funktor, který po zavolání vrátí logické ne z jeho uložených funktor jedním argumentem. Můžete ji použít, zadejte objekt funkce z hlediska jeho uložené funktor.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>Parametry

*Zábava*<br/>
Typ uložené funktor.

### <a name="member-functions"></a>Členské funkce

|Definice typu|Popis|
|---------------------|-----------------|
|argument_type|Typ argumentu funktor.|
|delegate_type|Typ obecného delegátu.|
|result_type|Typ výsledku funktor.|

|Člen|Popis|
|------------|-----------------|
|unary_negate|Sestaví funktor.|

|Operátor|Popis|
|--------------|-----------------|
|operator()|Vypočítá požadované funkce.|
|delegate_type^|Přetypování funktor na delegáta.|

### <a name="remarks"></a>Poznámky

Třída šablony popisuje jednoargumentové funktor, který ukládá další funktor jedním argumentem. Definuje členský operátor `operator()` tak, aby při objektu je volána jako funkce, vrátí logické ne z uložené funktor volána s argumentem.

Objekt můžete také předat jako argument funkce, jejíž typ je `delegate_type^` a budou převedeny správně.

### <a name="example"></a>Příklad

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```