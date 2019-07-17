---
title: stack – třída
ms.date: 11/04/2016
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
helpviewer_keywords:
- std::stack [C++], container_type
- std::stack [C++], size_type
- std::stack [C++], value_type
- std::stack [C++], empty
- std::stack [C++], pop
- std::stack [C++], push
- std::stack [C++], size
- std::stack [C++], top
ms.assetid: 02151c1e-eab0-41b8-be94-a839ead78ecf
ms.openlocfilehash: 36074f75830f92ba3fb9e5edb4e1507aa5ae1407
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241068"
---
# <a name="stack-class"></a>stack – třída

Kontejner adaptér třídu šablony, která poskytuje omezení funkcí omezení přístupu k elementu naposledy přidaný do některé základní typy kontejnerů. Třída zásobníku se používá, když je důležité, aby bylo jasné, že se pouze zásobníku operace provádějí v kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ dat prvku, který bude uložen do zásobníku.

*Kontejner*\
Typ základního kontejneru používaný k implementaci zásobníku. Výchozí hodnota je třída `deque`  *\<typ >* .

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` stanovené v šabloně první parametr objektu zásobníku je synonymní s [value_type](#value_type) a musí shodovat s typem elementu v základní třídě kontejneru `Container` stanovených druhý parametr šablony. `Type` Musí být možné přiřadit, takže je možné zkopírovat objekty daného typu a přiřadit proměnné typu hodnoty.

Zahrnout vhodný základní třídy kontejnerů pro zásobník [deque](../standard-library/deque-class.md), [list – třída](../standard-library/list-class.md), a [vector – třída](../standard-library/vector-class.md), nebo jiném pořadí kontejneru, který podporuje operace `back`, `push_back`, a `pop_back`. Základní třída kontejneru je zapouzdřen v rámci kontejneru adaptér, který zpřístupňuje pouze omezená sada členské funkce kontejneru pořadí jako veřejné rozhraní.

Zásobníku objekty jsou srovnatelné if rovnosti a pouze v případě elementů třídy `Type` lze porovnávat rovnosti a jsou méně – než srovnatelné Pokud a pouze v případě elementů třídy `Type` jsou méně – než srovnatelná s hodnotou.

- Třída zásobníku podporuje poslední dovnitř, první (ven LIFO) datové struktury. Dobré analogové brát v úvahu by stoh talířů shora. Elementy (tabulky) může vložit, prozkoumat nebo odebrat jenom z horní části zásobníku, což je poslední prvek na konci kontejneru základní. Omezení přístupu jenom k prvku na vrcholu je důvod horizontálních oddílů pomocí třídy zásobníku.

- [Front třídy](../standard-library/queue-class.md) podporuje první dovnitř, první ven (FIFO) datová struktura. Dobré analogové brát v úvahu by zarovnání pro bankovní pokladnu lidí. Elementy (lidé) mohou být přidány do pozadí řádku a odeberou se ze začátku řádku. Přední a zadní řádku může být kontrolována. Omezení přístupu jenom přední a zadní prvky tímto způsobem je z důvodu kožešiny horizontálních oddílů pomocí třídy fronty.

- [Priority_queue – třída](../standard-library/priority-queue-class.md) orders jeho prvky tak, aby největšího prvku je vždy na nejvyšší pozici. Podporuje vložení elementu a kontrolu a odstranění prvku na vrcholu. Dobré analogové brát v úvahu by uživatelé zarovnání ve kterém jsou uspořádané podle věku, výšku ani jiné kritérium.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[Zásobník](#stack)|Vytvoří `stack` , který je prázdný nebo který je kopií základní kontejnerového objektu.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejneru upraví `stack`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka představující počet prvků v `stack`.|
|[value_type](#value_type)|Typ, který představuje typ uložený jako prvek v objektu `stack`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[prázdný](#empty)|Testuje, zda `stack` je prázdný.|
|[POP](#pop)|Odebere element z horní části `stack`.|
|[push](#push)|Přidá prvek do horní části `stack`.|
|[Velikost](#size)|Vrátí počet prvků v `stack`.|
|[nahoru](#top)|Vrátí odkaz na prvek v horní části `stack`.|

## <a name="container_type"></a> container_type –

Typ, který poskytuje základní kontejner, aby ho upravit.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Všechny tři třídy kontejnerů sekvence standardní knihovny C++ – třídu vector, list – třída a třídě deque výchozí – požadavkům má být použit jako základní kontejneru pro objekt zásobníku. Uživatelem definované typy, které splňují tyto požadavky může také sloužit.

Další informace o `Container`, najdete v části poznámky [stack – třída](../standard-library/stack-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [stack::stack](#stack) příklad toho, jak deklarace a používání `container_type`.

## <a name="empty"></a> prázdný

Testuje, zda je zásobník je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** pokud zásobník je prázdný; **false** pokud zásobník je prázdný.

### <a name="example"></a>Příklad

```cpp
// stack_empty.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack <int> s1, s2;

   s1.push( 1 );

   if ( s1.empty( ) )
      cout << "The stack s1 is empty." << endl;
   else
      cout << "The stack s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The stack s2 is empty." << endl;
   else
      cout << "The stack s2 is not empty." << endl;
}
```

```Output
The stack s1 is not empty.
The stack s2 is empty.
```

## <a name="pop"></a> POP

Odebere element z horní části zásobníku.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Zásobník musí být neprázdné použít členskou funkci. Horní části zásobníku je obsazena naposledy přidaný prvek pozice a poslední prvek na konci kontejneru.

### <a name="example"></a>Příklad

```cpp
// stack_pop.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;

   s1.pop( );

   i = s1.size( );
   cout << "After a pop, the stack length is "
        << i << "." << endl;

   i = s1.top( );
   cout << "After a pop, the element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
After a pop, the stack length is 2.
After a pop, the element at the top of the stack is 20.
```

## <a name="push"></a> nabízených oznámení

Přidá prvek do horní části zásobníku.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Prvek přidán do horní části zásobníku.

### <a name="remarks"></a>Poznámky

Horní části zásobníku je obsazena naposledy přidaný prvek pozice a poslední prvek na konci kontejneru.

### <a name="example"></a>Příklad

```cpp
// stack_push.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 10 );
   s1.push( 20 );
   s1.push( 30 );

   stack <int>::size_type i;
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   i = s1.top( );
   cout << "The element at the top of the stack is "
        << i << "." << endl;
}
```

```Output
The stack length is 3.
The element at the top of the stack is 30.
```

## <a name="size"></a> Velikost

Vrátí počet prvků v zásobníku.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka zásobníku.

### <a name="example"></a>Příklad

```cpp
// stack_size.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1, s2;
   stack <int>::size_type i;

   s1.push( 1 );
   i = s1.size( );
   cout << "The stack length is " << i << "." << endl;

   s1.push( 2 );
   i = s1.size( );
   cout << "The stack length is now " << i << "." << endl;
}
```

```Output
The stack length is 1.
The stack length is now 2.
```

## <a name="size_type"></a> size_type

Typ celé číslo bez znaménka představující počet prvků v zásobníku.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `size_type` základní kontejneru přizpůsobené zásobníku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`.

## <a name="stack"></a> Zásobník

Sestaví zásobníku, který je prázdný nebo který je kopii kontejner základní třídy.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parametry

*doprava*\
Kontejner je vytvořený zásobníku kopií.

### <a name="example"></a>Příklad

```cpp
// stack_stack.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stack with default deque base container
   stack <char> dsc1;

   //Explicitly declares a stack with deque base container
   stack <char, deque<char> > dsc2;

   // Declares a stack with vector base containers
   stack <int, vector<int> > vsi1;

   // Declares a stack with list base container
   stack <int, list<int> > lsi;

   // The second member function copies elements from a container
   vector<int> v1;
   v1.push_back( 1 );
   stack <int, vector<int> > vsi2( v1 );
   cout << "The element at the top of stack vsi2 is "
        << vsi2.top( ) << "." << endl;
}
```

```Output
The element at the top of stack vsi2 is 1.
```

## <a name="top"></a> nahoru

Vrátí odkaz na prvek v horní části zásobníku.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek v kontejneru v horní části zásobníku.

### <a name="remarks"></a>Poznámky

Zásobník musí být neprázdné použít členskou funkci. Horní části zásobníku je obsazena naposledy přidaný prvek pozice a poslední prvek na konci kontejneru.

Pokud návratová hodnota `top` je přiřazena `const_reference`, objekt zásobníku nelze upravit. Pokud návratová hodnota `top` je přiřazen `reference`, objekt zásobníku lze upravit.

### <a name="example"></a>Příklad

```cpp
// stack_top.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   stack <int> s1;

   s1.push( 1 );
   s1.push( 2 );

   int& i = s1.top( );
   const int& ii = s1.top( );

   cout << "The top integer of the stack s1 is "
        << i << "." << endl;
   i--;
   cout << "The next integer down is "<< ii << "." << endl;
}
```

```Output
The top integer of the stack s1 is 2.
The next integer down is 1.
```

## <a name="value_type"></a> value_type

Typ, který představuje typ objektu uložený jako prvek v zásobníku.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type` základní kontejneru přizpůsobené zásobníku.

### <a name="example"></a>Příklad

```cpp
// stack_value_type.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;
   // Declares stacks with default deque base container
   stack<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   stack<int> s1;
   s1.push( AnInt );
   cout << "The element at the top of the stack is "
        << s1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the stack is 69.
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
