---
title: priority_queue – (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 573b365e0ca0d1c5b607144b1d143796e1ce927c
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466199"
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
Třída šablony popisuje objekt, který řídí různé délky seřazené řadu prvků, která má omezený přístup. Můžete použít adaptér kontejneru `priority_queue` ke správě základního kontejneru jako prioritní fronty.  
  
 V popisu níže `GValue` je stejný jako *hodnotu* Pokud je typ odkazu, v takovém případě je `Value^`. Obdobně `GContainer` je stejný jako *kontejneru* Pokud je typ odkazu, v takovém případě je `Container^`.  
  
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
 *Hodnota*  
 Typ elementu v řízené sekvenci  
  
 *Kontejner*  
 Typ základního kontejneru.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – či fronty >  
  
 **Namespace:** cliext –  

## <a name="declarations"></a>Deklarace  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|  
|[priority_queue::container_type (STL/CLR)](#container_type)|Typ základního kontejneru.|  
|[priority_queue::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[priority_queue::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro adaptér kontejneru.|  
|[priority_queue::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|  
|[priority_queue::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[priority_queue::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[priority_queue::value_compare (STL/CLR)](#value_compare)|Pořadí delegáta pro dva prvky.|  
|[priority_queue::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](#assign)|Nahradí všechny elementy.|  
|[priority_queue::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[priority_queue::get_container (STL/CLR)](#get_container)|Přistupuje k podkladové kontejneru.|  
|[priority_queue::pop (STL/CLR)](#pop)|Odebere element hghest priority.|  
|[priority_queue::priority_queue (STL/CLR)](#priority_queue)|Sestaví objekt kontejneru.|  
|[priority_queue::push (STL/CLR)](#push)|Přidá nový prvek.|  
|[priority_queue::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[priority_queue::top (STL/CLR)](#top)|Přistupuje k elementu nejvyšší prioritou.|  
|[priority_queue::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|  
|[priority_queue::value_comp (STL/CLR)](#value_comp)|Zkopíruje pořadí delegáta pro dva prvky.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](#top_item)|Přistupuje k elementu nejvyšší prioritou.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objektu.|  
|IPriorityQueue\<hodnoty, kontejner >|Udržujte adaptér obecný kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolňuje úložiště pro sekvenci řídí, prostřednictvím základní kontejneru, typu `Container`, který ukládá `Value` elementy a roste na požádání. Pořadí řazení jako haldu, s elementem nejvyšší prioritu (nejvyšší prvek) snadno dostupné a vyměnitelných uchová. Objekt omezuje přístup k vložení nové prvky a odebrání pouze nejvyšší prioritou elementu, implementace prioritní fronty.  
  
 Objekt seřadí sekvence pomocí volání uloženého delegáta objekt typu [priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Můžete zadat objekt uložené delegáta při konstrukci priority_queue –; Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je porovnání `operator<(value_type, value_type)`. Přístup k tomuto uloženého objektu voláním členské funkce [priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.  
  
 Takový objekt delegáta musí uložit přísné slabé seřazení u hodnot typu [priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). To znamená pro jakékoli dva klíče `X` a `Y`:  
  
 `value_comp()(X, Y)` Vrátí výsledek stejný datový typ Boolean při každém volání.  
  
 Pokud `value_comp()(X, Y)` má hodnotu true, pak `value_comp()(Y, X)` musí mít hodnotu false.  
  
 Pokud `value_comp()(X, Y)` má hodnotu true, pak `X` říká, že je řazen před `Y`.  
  
 Pokud `!value_comp()(X, Y) && !value_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.  
  
 Pro libovolný element `X` , která předchází `Y` v řízené sekvenci `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta, klíče nikdy snížení hodnoty.)  
  
 Element nejvyšší priority je tedy jeden z prvků, které není řazen před jakýmkoli jiným prvkem.  
  
 Protože základní kontejneru udržuje prvky uspořádané jako haldu:  
  
 Kontejner musí podporovat iterátory s náhodným přístupem.  
  
 Elementy ekvivalentní řazení může být odebrány v jiném pořadí, než byly nabídnuty. (Řazení není stabilní.)  
  
 Proto kandidáty pro základní kontejner zahrnují [deque (STL/CLR)](../dotnet/deque-stl-clr.md) a [vektor (STL/CLR)](../dotnet/vector-stl-clr.md).  
  
## <a name="members"></a>Členové
  
## <a name="assign"></a> priority_queue::Assign (STL/CLR)
Nahradí všechny elementy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void assign(priority_queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Adaptér kontejneru pro vložení.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce přiřadí `right.get_container()` do základního kontejneru. Použijte ke změně celého obsahu do fronty.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mypriority_queue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
c a b  
```  

## <a name="const_reference"></a> priority_queue::const_reference (STL/CLR)
Typ konstantního odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje konstantní odkaz na element.  
  
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
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="container_type"></a> priority_queue::container_type (STL/CLR)
Typ základního kontejneru.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  

## <a name="difference_type"></a> priority_queue::difference_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje element může být záporný počet.  
  
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
        System::Console::Write(" {0}", elem);   
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

## <a name="empty"></a> priority_queue::Empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda priority_queue – je prázdný.  
  
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
        System::Console::Write(" {0}", elem);   
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

## <a name="generic_container"></a> priority_queue::generic_container (STL/CLR)
Typ obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::IPriorityQueue<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje obecné rozhraní pro tuto třídu adaptéru kontejner šablony.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
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

## <a name="generic_value"></a> priority_queue::generic_value (STL/CLR)
Typ elementu pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje. (`GValue` je buď `value_type` nebo `value_type^` Pokud `value_type` je typ odkazu.)  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mypriority_queue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in priority order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Mypriority_queue::generic_value elem = gc1->top();   
  
        System::Console::Write(" {0}", elem);   
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

## <a name="get_container"></a> priority_queue::get_container (STL/CLR)
Přistupuje k podkladové kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
container_type get_container();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí základní kontejneru. Použijete ji obejít omezení vynucená obálkou kontejneru.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  

## <a name="op_as"></a> priority_queue::Operator = (STL/CLR)
Nahradí řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
priority_queue <Value, Container>% operator=(priority_queue <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Adaptér kontejneru pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mypriority_queue c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
c a b  
c a b  
```  

## <a name="pop"></a> priority_queue::POP (STL/CLR)
Odebere prvek nejvyšší proirity.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void pop();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odstraní prvek nejvyšší prioritou řízené sekvence, která musí být neprázdný. Použijte ke zkrácení fronty podle jeden element na pozadí.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
b a  
```  

## <a name="priority_queue"></a> priority_queue::priority_queue (STL/CLR)
Sestaví objekt kontejneru adaptéru.  
  
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
 *pokračování*  
 Kontejner pro kopírování.  
  
 *první*  
 Začátek rozsahu pro vložení.  
  
 *poslední*  
 Konec rozsahu pro vložení.  
  
 *Před*  
 Řazení predikátu řízené sekvence.  
  
 *doprava*  
 Objekt nebo rozsahu pro vložení.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `priority_queue();`  
  
 Vytvoří prázdný zabalené kontejner, s výchozí řazení predikátu. Použijete ji k určení prázdnou počáteční řízenou sekvenci, s výchozí řazení predikátu.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 Vytvoří zabalené kontejner, který je kopií `right.get_container()`, pořadí predikátem `right.value_comp()`. Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objekt fronty *správné*, stejné pořadí predikátem.  
  
 Konstruktor:  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 Vytvoří zabalené kontejner, který je kopií `right->get_container()`, pořadí predikátem `right->value_comp()`. Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objekt fronty `*right`, stejné pořadí predikátem.  
  
 Konstruktor:  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 vytvoří kontejner prázdný zabalené pořadí predikátem *před*. Použít prázdnou počáteční řízenou sekvenci, určit se zadanou predikát pořadí.  
  
 Konstruktor:  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 vytvoří kontejner prázdný zabalené pořadí predikátem *před*, předá všechny prvky *pokračování* použilo ji k určení počáteční řízené sekvence z existující kontejner, se zadanou predikát pořadí.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 Vytvoří prázdný zabalené kontejner, výchozí pořadí predikátem a pak sekvence nabízených oznámení [`first`, `last`). Použijete ji k určení počáteční řízené sekvence ze zadaného eqeuence se zadanou predikát pořadí.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 vytvoří kontejner prázdný zabalené pořadí predikátem *před*, předá sekvenci [`first`, `last`). Použijete ji k určení počáteční řízené sekvence ze zadaného seqeuence se zadanou predikát pořadí.  
  
 Konstruktor:  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 vytvoří kontejner prázdný zabalené pořadí predikátem *před*, předá všechny prvky *pokračování* plus sekvenci [`first`, `last`). Použijete ji k určení počáteční řízené sekvence z existující kontejner a zadané seqeuence se zadanou predikát pořadí.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
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
  
## <a name="push"></a> priority_queue::push (STL/CLR)
Přidá nový prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void push(value_type val);  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vloží prvek s hodnotou `val` v řízené sekvenci a změní pořadí řízené sekvence udržovat disciplína haldy. Použijete ji Pokud chcete přidat jiný element do fronty.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
```  
  
## <a name="reference"></a> priority_queue::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje odkaz na element.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of priority_queue and redisplay   
    Mypriority_queue::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c a b  
x a b  
```  

## <a name="size"></a> priority_queue::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)`()`.  
  
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
        System::Console::Write(" {0}", elem);   
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

## <a name="size_type"></a> priority_queue::size_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet prvků záporná.  
  
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
        System::Console::Write(" {0}", elem);   
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
  
## <a name="to_array"></a> priority_queue::to_array (STL/CLR)
Zkopíruje do nového pole řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
d c b a  
c a b  
```  

## <a name="top"></a> priority_queue::top (STL/CLR)
Přistupuje k elementu nejvyšší prioritou.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reference top();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na prvek nejvyšší (nejvyšší priorita) řízené sekvence, která musí být neprázdný. Použijete ho pro přístup k prvku nejvyšší prioritu, když víte, že existuje.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  

## <a name="top_item"></a> priority_queue::top_item (STL/CLR)
Přistupuje k elementu nejvyšší prioritou.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>Poznámky  
 Vlastnost má přístup k elementu nahoře (nejvyšší priorita) řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu elementu nejvyšší prioritu, když víte, že existuje.  
  
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
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 c a b  
top_item = c  
 x a b  
```  

## <a name="value_comp"></a> priority_queue::value_comp (STL/CLR)
Zkopíruje pořadí delegáta pro dva prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnání dvou hodnot.  
  
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

## <a name="value_compare"></a> priority_queue::value_compare (STL/CLR)
Pořadí delegáta pro dvě hodnoty.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
binary_delegate<value_type, value_type, int> value_compare;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro delegáta, který určuje, zda první argument je řazen před druhým.  
  
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

## <a name="value_type"></a> priority_queue::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *hodnota*.  
  
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
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  