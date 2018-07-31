---
title: zásobníku (STL/CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::stack::assign
- cliext::stack::const_reference
- cliext::stack::container_type
- cliext::stack::difference_type
- cliext::stack::empty
- cliext::stack::generic_container
- cliext::stack::generic_value
- cliext::stack::get_container
- cliext::stack::operator=
- cliext::stack::pop
- cliext::stack::push
- cliext::stack::reference
- cliext::stack::size
- cliext::stack::size_type
- cliext::stack::stack
- cliext::stack::to_array
- cliext::stack::top
- cliext::stack::top_item
- cliext::stack::value_type
dev_langs:
- C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
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
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- stack member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 09368f3a43a5ba7a5a1c4247fdbbccdf345b0b21
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376206"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, s přístupem k FIFO last-in. Můžete použít adaptér kontejneru `stack` ke správě základního kontejneru jako důkladné zásobníku.  
  
 V popisu níže `GValue` je stejný jako *hodnotu* Pokud je typ odkazu, v takovém případě je `Value^`. Obdobně `GContainer` je stejný jako *kontejneru* Pokud je typ odkazu, v takovém případě je `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
    { ..... };  
```  
  
### <a name="parameters"></a>Parametry  
 *Hodnota*  
 Typ elementu v řízené sekvenci  
  
 *Kontejner*  
 Typ základního kontejneru.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / stack >  
  
 **Namespace:** cliext –  
  
## <a name="declarations"></a>Deklarace  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[stack::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|  
|[stack::container_type (STL/CLR)](#container_type)|Typ základního kontejneru.|  
|[stack::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[stack::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro adaptér kontejneru.|  
|[stack::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro adaptér kontejneru.|  
|[stack::reference (STL/CLR)](#reference)|Typ odkazu na prvek|  
|[stack::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[stack::value_type (STL/CLR)](#value_type)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[stack::assign (STL/CLR)](#assign)|Nahradí všechny elementy.|  
|[stack::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[stack::get_container (STL/CLR)](#get_container)|Přistupuje k podkladové kontejneru.|  
|[stack::pop (STL/CLR)](#pop)|Odstraní poslední prvek.|  
|[stack::push (STL/CLR)](#push)|Přidá nový poslední prvek.|  
|[stack::size (STL/CLR)](#size)|Spočítá počet prvků.|  
|[stack::stack (STL/CLR)](#stack)|Sestaví objekt kontejneru.|  
|[stack::top (STL/CLR)](#top)|Přistupuje k poslední prvek.|  
|[stack::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[stack::top_item (STL/CLR)](#top_item)|Přistupuje k poslední prvek.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[stack::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|  
|[operator!= (stack) (STL/CLR)](#op_neq)|Určuje, zda `stack` není roven jinému objektu `stack` objektu.|  
|[operator< (stack) (STL/CLR)](#op_lt)|Určuje, zda `stack` je menší než jiný objekt `stack` objektu.|  
|[operator<= (stack) (STL/CLR)](#op_lteq)|Určuje, zda `stack` objekt je menší nebo rovna jiné `stack` objektu.|  
|[operator== (stack) (STL/CLR)](#op_eq)|Určuje, zda `stack` je roven jinému objektu `stack` objektu.|  
|[operator> (stack) (STL/CLR)](#op_gt)|Určuje, zda `stack` je větší než jiný objekt `stack` objektu.|  
|[operator>= (stack) (STL/CLR)](#op_gteq)|Určuje, zda `stack` objekt je větší než nebo roven jinému `stack` objektu.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objektu.|  
|IStack\<hodnoty, kontejner >|Udržujte adaptér obecný kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolňuje úložiště pro sekvenci řídí, prostřednictvím základní kontejneru, typu *kontejneru*, který ukládá *hodnotu* elementy a roste na požádání. Objekt omezuje přístup k vložení a odebrání právě posledního prvku, implementace fronty FIFO poslední dovnitř (označované také jako LIFO fronty nebo stack).  
 
## <a name="members"></a>Členové

## <a name="assign"></a> Stack::Assign (STL/CLR)
Nahradí všechny elementy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void assign(stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Adaptér kontejneru pro vložení.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce přiřadí `right.get_container()` do základního kontejneru. Použijte ke změně celého obsahu do zásobníku.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_assign.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mystack c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="const_reference"></a> Stack::const_reference (STL/CLR)
Typ konstantního odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje konstantní odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_const_reference.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " c b a"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Mystack::const_reference cref = c1.top();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="container_type"></a> Stack::container_type (STL/CLR)
Typ základního kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Container value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *kontejneru*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_container_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mystack::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
```  

## <a name="difference_type"></a> Stack::difference_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje element může být záporný počet.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_difference_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute negative difference   
    Mystack::difference_type diff = c1.size();   
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
 a b c  
pushing 2 = -2  
popping 3 = 3  
```  

## <a name="empty"></a> Stack::Empty (STL/CLR)
Zkouší, zda nejsou přítomny žádné prvky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda zásobník je prázdný.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_empty.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  
  
## <a name="generic_container"></a> Stack::generic_container (STL/CLR)
Typ obecné rozhraní pro adaptér kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Microsoft::VisualC::StlClr::IStack<Value>  
    generic_container;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje obecné rozhraní pro tuto třídu adaptéru kontejner šablony.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_generic_container.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mystack::generic_container^ gc1 = %c1;   
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
a b c  
a b c  
a b c d  
a b c d e  
```  
  
## <a name="generic_value"></a> Stack::generic_value (STL/CLR)
Typ elementu pro použití s obecné rozhraní pro kontejner.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje. (`GValue` je buď `value_type` nebo `value_type^` Pokud `value_type` je typ odkazu.)  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_generic_value.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mystack::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in reverse using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Mystack::generic_value elem = gc1->top();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
c b a  
```  
  
## <a name="get_container"></a> Stack::get_container (STL/CLR)
Přistupuje k podkladové kontejneru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
container_type^ get_container();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí obslužnou rutinu pro základní kontejneru. Použijete ji obejít omezení vynucená obálkou kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_get_container.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mystack::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="op_as"></a> Stack::Operator = (STL/CLR)
Nahradí řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
stack <Value, Container>% operator=(stack <Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Adaptér kontejneru pro kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_as.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2 = c1;   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
a b c  
a b c  
```  

## <a name="pop"></a> Stack::POP (STL/CLR)
Odstraní poslední prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void pop();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odstraní poslední prvek řízené sekvence, která musí být neprázdný. Použijte ke zkrácení zásobníku o jeden element na pozadí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_pop.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
a b c  
a b  
```  

## <a name="push"></a> Stack::push (STL/CLR)
Přidá nový poslední prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void push(value_type val);  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vloží prvek s hodnotou `val` na konci řízené sekvence. Použijete ji k připojení jiný element do zásobníku.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_push.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
a b c  
```  

## <a name="reference"></a> Stack::Reference (STL/CLR)
Typ odkazu na prvek  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje odkaz na element.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_reference.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of stack and redisplay   
    Mystack::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b x  
```  
  
## <a name="size"></a> Stack::size (STL/CLR)
Spočítá počet prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)`()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_size.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
 a b c  
size() = 3 starting with 3  
size() = 2 after popping  
size() = 4 after adding 2  
```  

## <a name="size_type"></a> Stack::size_type (STL/CLR)
Typ vzdálenosti se znaménkem mezi dvěma elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje počet prvků záporná.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_size_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mystack::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size difference = 2  
```  
  
## <a name="stack"></a> Stack::Stack (STL/CLR)
Sestaví objekt kontejneru adaptéru.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
stack();  
stack(stack<Value, Container>% right);  
stack(stack<Value, Container>^ right);  
explicit stack(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doprava*  
 Kopírovaný objekt.  
  
 *Zabalená*  
 Zabalená kontejner, aby používal.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor:  
  
 `stack();`  
  
 Vytvoří prázdný zabalené kontejner. Použijete ji k určení počáteční prázdnou řízenou sekvenci.  
  
 Konstruktor:  
  
 `stack(stack<Value, Container>% right);`  
  
 Vytvoří zabalené kontejner, který je kopií `right.get_container()`. Můžete použít k určení počáteční řízené sekvence, která je kopii sekvence řízenou parametrem objektu stack *správné*.  
  
 Konstruktor:  
  
 `stack(stack<Value, Container>^ right);`  
  
 Vytvoří zabalené kontejner, který je kopií `right->get_container()`. Můžete použít k určení počáteční řízené sekvence, která je kopii sekvence řízenou parametrem objektu stack `*right`.  
  
 Konstruktor:  
  
 `explicit stack(container_type% wrapped);`  
  
 používá existující kontejner *zabalené* jako zabalené kontejner. Můžete použít k vytvoření zásobníku z existující kontejner.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_construct.cpp   
// compile with: /clr   
#include <cliext/stack>   
#include <cliext/vector>   
  
typedef cliext::stack<wchar_t> Mystack;   
typedef cliext::vector<wchar_t> Myvector;   
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;   
int main()   
    {   
// construct an empty container   
    Mystack c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Myvector v2(5, L'x');   
    Mystack_vec c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mystack_vec c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Mystack_vec c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  

## <a name="to_array"></a> Stack::to_array (STL/CLR)
Zkopíruje do nového pole řízené sekvence.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_to_array.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
a b c d  
a b c  
```  

## <a name="top"></a> Stack::top (STL/CLR)
Přistupuje k poslední prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
reference top();  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí odkaz na poslední prvek řízené sekvence, která musí být neprázdný. Použijete ho pro přístup k posledního prvku, když víte, že existuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_top.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
  
```Output  
 a b c  
top() = c  
 a b x  
```  

## <a name="top_item"></a> Stack::top_item (STL/CLR)
Přistupuje k poslední prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property value_type top_item;  
```  
  
### <a name="remarks"></a>Poznámky  
 Vlastnost má přístup k poslední prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu posledního prvku, když víte, že existuje.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_top_item.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
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
 a b c  
top_item = c  
 a b x  
```  

## <a name="value_type"></a> Stack::value_type (STL/CLR)
Typ prvku  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony *hodnota*.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_value_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mystack::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
c b a  
```  

## <a name="op_neq"></a> Operator! = (stack) (STL/CLR)
Zásobník není rovno porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator!=(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* při dva balíčky jsou ve srovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_ne.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> operátor&lt; (stack) (STL/CLR)
Zásobník menší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator<(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->` [stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md) `() <` `right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* Když jsou dva balíčky porovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_lt.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> operátor&lt;= (stack) (STL/CLR)
Stack – menší nebo rovna porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator<=(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* při dva balíčky jsou ve srovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_le.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> Operator == (stack) (STL/CLR)
Porovnání rovna zásobníku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator==(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* při dva balíčky jsou ve srovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_eq.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  
  
## <a name="op_gt"></a> operátor&gt; (stack) (STL/CLR)
Zásobník je větší než porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator>(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* při dva balíčky jsou ve srovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_gt.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }   
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  
  
## <a name="op_gteq"></a> operátor&gt;= (stack) (STL/CLR)
Stack – větší než nebo roven hodnotě porovnání.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Value,  
    typename Container>  
    bool operator>=(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parametry  
 *doleva*  
 Levé kontejner k porovnání.  
  
 *doprava*  
 Správném kontejneru pro porovnání.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí funkci operátoru `!(left < right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* při dva balíčky jsou ve srovnání elementu pomocí elementu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// cliext_stack_operator_ge.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
``` 