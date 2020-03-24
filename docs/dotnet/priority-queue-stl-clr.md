---
title: priority_queue (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::priority_queue
- cliext::priority_queue::assign
- cliext::priority_queue::const_reference
- cliext::priority_queue::container_type
- cliext::priority_queue::difference_type
- cliext::priority_queue::empty
- cliext::priority_queue::generic_container
- cliext::priority_queue::generic_value
- cliext::priority_queue::get_container
- cliext::priority_queue::operator=
- cliext::priority_queue::pop
- cliext::priority_queue::priority_queue
- cliext::priority_queue::push
- cliext::priority_queue::reference
- cliext::priority_queue::size
- cliext::priority_queue::size_type
- cliext::priority_queue::to_array
- cliext::priority_queue::top
- cliext::priority_queue::top_item
- cliext::priority_queue::value_comp
- cliext::priority_queue::value_compare
- cliext::priority_queue::value_type
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- priority_queue member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
ms.openlocfilehash: e21e7ba4dc3a4ed270548506ac1a9e37a2c1a23a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208465"
---
# <a name="priority_queue-stlclr"></a>priority_queue (STL/CLR)

Třída šablony popisuje objekt, který ovládá uspořádanou sekvenci prvků s proměnlivou délkou, která má omezený přístup. Adaptér kontejneru `priority_queue` slouží ke správě podkladového kontejneru jako prioritní fronty.

V popisu níže je `GValue` stejné jako *hodnota* , pokud se jedná o typ REF, v takovém případě je `Value^`. Podobně `GContainer` je stejný jako *kontejner* , pokud se jedná o typ REF, v takovém případě je `Container^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value,
    typename Container>
    ref class priority_queue
        System::ICloneable,
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Typ elementu v řízené sekvenci

*Vnitřního*<br/>
Typ podkladového kontejneru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/Queue >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[priority_queue::container_type (STL/CLR)](#container_type)|Typ podkladového kontejneru.|
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Typ obecného rozhraní pro adaptér kontejneru.|
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|
|[priority_queue::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[priority_queue::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Delegát řazení pro dva prvky.|
|[priority_queue::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[priority_queue::assign (STL/CLR)](#assign)|Nahradí všechny prvky.|
|[priority_queue::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[priority_queue::get_container (STL/CLR)](#get_container)|Přistupuje k základnímu kontejneru.|
|[priority_queue::pop (STL/CLR)](#pop)|Odebere element hghest-priority.|
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Sestaví objekt kontejneru.|
|[priority_queue::push (STL/CLR)](#push)|Přidá nový prvek.|
|[priority_queue::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[priority_queue::top (STL/CLR)](#top)|Přistupuje k elementu nejvyšší priority.|
|[priority_queue::to_array (STL/CLR)](#to_array)|Zkopíruje řízenou sekvenci do nového pole.|
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Zkopíruje delegáta řazení dvou prvků.|

|Vlastnost|Popis|
|--------------|-----------------|
|[priority_queue::top_item (STL/CLR)](#top_item)|Přistupuje k elementu nejvyšší priority.|

|Operátor|Popis|
|--------------|-----------------|
|[priority_queue::operator= (STL/CLR)](#op_as)|Nahradí řízenou sekvenci.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikuje objekt.|
|IPriorityQueue\<hodnota, kontejner >|Udržujte obecný adaptér kontejneru.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, kterou ovládá, prostřednictvím podkladového kontejneru, typu `Container`, který ukládá `Value` prvky a roste na vyžádání. Udržuje sekvenci uspořádanou jako haldu s prvkem nejvyšší priority (horním prvkem), který je snadno přístupný a vyměnitelný. Objekt omezuje přístup pro vložení nových elementů a odebrání pouze prvku nejvyšší priority, implementace fronty priorit.

Objekt seřadí sekvenci, kterou ovládá, voláním uloženého objektu delegáta typu [priority_queue:: value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Uložený objekt delegáta lze zadat při vytváření priority_queue; Pokud nezadáte žádný delegovaný objekt, výchozí hodnota je porovnávání `operator<(value_type, value_type)`. K tomuto uloženému objektu přistupujete voláním členské funkce [priority_queue:: value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.

Takový objekt delegáta musí způsobit přísné slabé řazení hodnot typu [priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). To znamená, že pro všechny dva klíče `X` a `Y`:

`value_comp()(X, Y)` vrací stejný logický výsledek při každém volání.

Pokud má `value_comp()(X, Y)` hodnotu true, `value_comp()(Y, X)` musí mít hodnotu false.

Pokud má `value_comp()(X, Y)` hodnotu true, `X` se říká, že se má seřadit před `Y`.

Pokud má `!value_comp()(X, Y) && !value_comp()(Y, X)` hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.

U všech prvků `X`, které předcházejí `Y` v řízené sekvenci, `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta klíče nikdy nesnižují hodnotu.)

Prvek s nejvyšší prioritou je tedy jedním z prvků, které nejsou seřazeny před jakýmkoli jiným prvkem.

Vzhledem k tomu, že podkladový kontejner uchovává prvky seřazené jako halda:

Kontejner musí podporovat iterátory s náhodným přístupem.

Prvky s ekvivalentním řazením mohou být odebrány v jiném pořadí, než byly vloženy. (Řazení není stabilní.)

Proto kandidáty pro základní kontejner zahrnují [deque (STL/CLR)](../dotnet/deque-stl-clr.md) a [Vector (STL/CLR)](../dotnet/vector-stl-clr.md).

## <a name="members"></a>Členové

## <a name="priority_queueassign-stlclr"></a><a name="assign"></a>priority_queue:: assign (STL/CLR)

Nahradí všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(priority_queue<Value, Container>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Adaptér kontejneru pro vložení.

### <a name="remarks"></a>Poznámky

Členská funkce přiřadí `right.get_container()` k základnímu kontejneru. Použijete ho ke změně celého obsahu fronty.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_assign.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign a repetition of values
    Mypriority_queue c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queueconst_reference-stlclr"></a><a name="const_reference"></a>priority_queue:: const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje konstantní odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_const_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mypriority_queue::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="priority_queuecontainer_type-stlclr"></a><a name="container_type"></a>priority_queue:: container_type (STL/CLR)

Typ podkladového kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_container_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c" using container_type
    Mypriority_queue::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuedifference_type-stlclr"></a><a name="difference_type"></a>priority_queue::d ifference_type (STL/CLR)

Typy podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje pravděpodobně negativní počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_difference_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute negative difference
    Mypriority_queue::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

    // compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
c a b
pushing 2 = -2
popping 3 = 3
```

## <a name="priority_queueempty-stlclr"></a><a name="empty"></a>priority_queue:: Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [priority_queue:: Size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Použijete ho k otestování, jestli je priority_queue prázdné.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_empty.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
c a b
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="priority_queuegeneric_container-stlclr"></a><a name="generic_container"></a>priority_queue:: generic_container (STL/CLR)

Typ obecného rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecné rozhraní pro tuto třídu kontejnerového adaptéru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_generic_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
d c b a
e d b a c
```

## <a name="priority_queuegeneric_value-stlclr"></a><a name="generic_value"></a>priority_queue:: generic_value (STL/CLR)

Typ elementu pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt typu `GValue`, který popisuje hodnotu uloženého elementu pro použití s obecným rozhraním pro tuto třídu kontejneru šablony. (`GValue` je buď `value_type` nebo `value_type^`, pokud `value_type` je typ ref.)

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_generic_value.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get interface to container
    Mypriority_queue::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display in priority order using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mypriority_queue::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
c b a
```

## <a name="priority_queueget_container-stlclr"></a><a name="get_container"></a>priority_queue:: get_container (STL/CLR)

Přistupuje k základnímu kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
container_type get_container();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí podkladový kontejner. Použijete ji k obejít omezení uložených obálkou kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_get_container.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queueoperator-stlclr"></a><a name="op_as"></a>priority_queue:: operator = (STL/CLR)

Nahradí řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Adaptér kontejneru ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ji k nahrazení kontrolované sekvence kopií kontrolované sekvence *vpravo*.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_operator_as.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mypriority_queue c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
c a b
```

## <a name="priority_queuepop-stlclr"></a><a name="pop"></a>priority_queue::p op (STL/CLR)

Odebere nejvyšší proirity prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Členská funkce odebere prvek nejvyšší priority kontrolované sekvence, který nesmí být prázdný. Použijete ho ke zkrácení fronty podle jednoho prvku na pozadí.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_pop.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
b a
```

## <a name="priority_queuepriority_queue-stlclr"></a><a name="priority_queue"></a>priority_queue::p riority_queue (STL/CLR)

Vytvoří objekt adaptéru kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
priority_queue();
priority_queue(priority_queue<Value, Container> right);
priority_queue(priority_queue<Value, Container> right);
explicit priority_queue(value_compare^ pred);
priority_queue(value_compare^ pred, container_type% cont);
template<typename InIt>
    priority_queue(InIt first, InIt last);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred);
template<typename InIt>
    priority_queue(InIt first, InIt last,
        value_compare^ pred, container_type% cont);
```

#### <a name="parameters"></a>Parametry

*kont*<br/>
Kontejner ke zkopírování.

*první*<br/>
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*čekání*<br/>
Predikát řazení pro řízenou sekvenci.

*Kliknutím*<br/>
Objekt nebo rozsah, který chcete vložit.

### <a name="remarks"></a>Poznámky

Konstruktor:

`priority_queue();`

Vytvoří prázdný zabalený kontejner s výchozím predikátem řazení. Použijete ji k zadání prázdné počáteční řízené sekvence s výchozím predikátem řazení.

Konstruktor:

`priority_queue(priority_queue<Value, Container>% right);`

Vytvoří zabalený kontejner, který je kopií `right.get_container()`, s predikátem řazení `right.value_comp()`. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené *přímo*objektem fronty, se stejným predikátem řazení.

Konstruktor:

`priority_queue(priority_queue<Value, Container>^ right);`

Vytvoří zabalený kontejner, který je kopií `right->get_container()`, s predikátem řazení `right->value_comp()`. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem fronty `*right`se stejným predikátem řazení.

Konstruktor:

`explicit priority_queue(value_compare^ pred);`

Vytvoří prázdný zabalený kontejner s predikátem řazení *před*. Použijete ji k zadání prázdné počáteční řízené sekvence se zadaným predikátem řazení.

Konstruktor:

`priority_queue(value_compare^ pred, container_type cont);`

Vytvoří prázdný zabalený kontejner s predikátem řazení *před*a poté vloží všechny prvky *, které mají* být použity, k určení počáteční sekvence z existujícího kontejneru se zadaným predikátem řazení.

Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last);`

Vytvoří prázdný zabalený kontejner s výchozím predikátem řazení a pak vloží sekvenci [`first`, `last`). Použijete ji k určení počáteční řízené sekvence ze zadaného eqeuence se zadaným predikátem řazení.

Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`

Vytvoří prázdný zabalený kontejner s predikátem řazení *před*a poté vloží sekvenci [`first`, `last`). Použijete ji k určení počáteční řízené sekvence ze zadaného seqeuence se zadaným predikátem řazení.

Konstruktor:

`template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`

Vytvoří prázdný zabalený kontejner s predikátem řazení *před*a poté vloží všechny *prvky typu push* plus sekvence [`first`, `last`). Použijete ji k určení počáteční řízené sekvence z existujícího kontejneru a zadaného seqeuence se zadaným predikátem řazení.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_construct.cpp
// compile with: /clr
#include <cliext/queue>
#include <cliext/deque>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
typedef cliext::deque<wchar_t> Mydeque;
int main()
    {
// construct an empty container
    Mypriority_queue c1;
    Mypriority_queue::container_type^ wc1 = c1.get_container();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    for each (wchar_t elem in wc1)
        c2.push(elem);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule by copying an underlying container
    Mypriority_queue c2x =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
   for each (wchar_t elem in c2x.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mypriority_queue c3(wc1->begin(), wc1->end());
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mypriority_queue c4(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>());
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range, another container, and an ordering rule
    Mypriority_queue c5(wc1->begin(), wc1->end(),
        cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c5.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mypriority_queue c6(c3);
    for each (wchar_t elem in c6.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mypriority_queue c7(%c3);
    for each (wchar_t elem in c7.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule, by copying an underlying container
    Mypriority_queue c8 =
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);
    for each (wchar_t elem in c8.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
c a b
size() = 0
a c b
a c b
c a b
a c b
a a b c c b
c a b
c a b
a c b
```

## <a name="priority_queuepush-stlclr"></a><a name="push"></a>priority_queue::p USH (STL/CLR)

Přidá nový prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží prvek s hodnotou `val` do řízené sekvence a změní pořadí řízené sekvence pro zachování oboru haldy. Použijete ho k přidání dalšího elementu do fronty.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_push.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
```

## <a name="priority_queuereference-stlclr"></a><a name="reference"></a>priority_queue:: Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_reference.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify top of priority_queue and redisplay
    Mypriority_queue::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
x a b
```

## <a name="priority_queuesize-stlclr"></a><a name="size"></a>priority_queue:: Size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací délku řízené sekvence. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci. Pokud vás zajímá, zda má sekvence nenulovou velikost, přečtěte si téma [priority_queue:: Empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_size.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

    // add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
c a b
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="priority_queuesize_type-stlclr"></a><a name="size_type"></a>priority_queue:: size_type (STL/CLR)

Typ podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje nezáporný počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_size_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mypriority_queue::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
c a b
size difference = 2
```

## <a name="priority_queueto_array-stlclr"></a><a name="to_array"></a>priority_queue:: to_array (STL/CLR)

Zkopíruje řízenou sekvenci do nového pole.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízenou sekvenci. Použijete ho k získání kopie řízené sekvence ve formuláři Array.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_to_array.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
d c b a
c a b
```

## <a name="priority_queuetop-stlclr"></a><a name="top"></a>priority_queue:: Top (STL/CLR)

Přistupuje k elementu nejvyšší priority.

### <a name="syntax"></a>Syntaxe

```cpp
reference top();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na horní prvek (nejvyšší priorita) kontrolované sekvence, který nesmí být prázdný. Můžete ji použít pro přístup k elementu nejvyšší priority, pokud víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_top.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

    // alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

## <a name="priority_queuetop_item-stlclr"></a><a name="top_item"></a>priority_queue:: top_item (STL/CLR)

Přistupuje k elementu nejvyšší priority.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k hornímu prvku (nejvyšší priority) kontrolované sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu elementu nejvyšší priority, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_top_item.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

    // alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c a b
top_item = c
x a b
```

## <a name="priority_queuevalue_comp-stlclr"></a><a name="value_comp"></a>priority_queue:: value_comp (STL/CLR)

Zkopíruje delegáta řazení dvou prvků.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou hodnot.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_value_comp.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_compare-stlclr"></a><a name="value_compare"></a>priority_queue:: value_compare (STL/CLR)

Delegát pro řazení dvou hodnot.

### <a name="syntax"></a>Syntaxe

```cpp
binary_delegate<value_type, value_type, int> value_compare;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro delegáta, který určuje, zda je první argument řazen před druhým.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_value_compare.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mypriority_queue c2 = cliext::greater<wchar_t>();
    vcomp = c2.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        vcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        vcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        vcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="priority_queuevalue_type-stlclr"></a><a name="value_type"></a>priority_queue:: value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *hodnotu*parametru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_priority_queue_value_type.cpp
// compile with: /clr
#include <cliext/queue>

typedef cliext::priority_queue<wchar_t> Mypriority_queue;
int main()
    {
    Mypriority_queue c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

    // display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mypriority_queue::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```
