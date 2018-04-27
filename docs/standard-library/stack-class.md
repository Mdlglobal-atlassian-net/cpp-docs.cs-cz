---
title: Stack – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- stack/std::stack::container_type
- stack/std::stack::size_type
- stack/std::stack::value_type
- stack/std::stack::empty
- stack/std::stack::pop
- stack/std::stack::push
- stack/std::stack::size
- stack/std::stack::top
dev_langs:
- C++
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df3e80177c81560fa7e9c87b7745277795d20bea
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="stack-class"></a>stack – třída

Třída adaptéru kontejneru šablony, která poskytuje omezení funkcí omezení přístupu k prvek naposledy přidaný do některé základní typ kontejneru. Stack – třída se používá v případě, že je důležité mít pouze zásobníku operace, se provádí na kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parametry

*Typ* element datový typ se neukládají v zásobníku.

`Container` Typ základního kontejneru použít k implementaci zásobníku. Výchozí hodnota je třída `deque`  *\<typ >*.

## <a name="remarks"></a>Poznámky

Elementy třídy **typ** stanovené v šabloně první parametr zásobníku objektu je shodný s [value_type](#value_type) a musí shodovat s typem elementu v základní třídě kontejneru **Kontejneru** stanoveno druhý parametr šablony. **Typu** musí být přiřaditelný, takže je možné zkopírovat objekty daného typu a přiřadit hodnoty proměnné daného typu.

Zahrnout vhodný základní třídy kontejnerů pro zásobník [deque](../standard-library/deque-class.md), [list – třída](../standard-library/list-class.md), a [vector – třída](../standard-library/vector-class.md), nebo jakékoli jiné pořadí kontejner, který podporuje operace **zpět**, `push_back`, a `pop_back`. Základní třída kontejneru je zapouzdřený v rámci kontejneru adaptéru, který zveřejňuje jenom omezená sada členské funkce kontejneru pořadí jako veřejné rozhraní.

Zásobník objekty jsou v případě porovnatelný z hlediska rovnosti a pouze v případě elementy třídy **typ** jsou porovnatelný z hlediska rovnosti a menší – než porovnatelný z hlediska v případě a pouze v případě elementy třídy **typ** méně – než porovnatelný.

- Stack – třída podporuje last-in ven (LIFO) datová struktura. Dobrý analogovým pamatovat by zásobník desky. Elementy (tabulky) může vložit, prověřovány nebo odebrat pouze z horní části zásobníku, který je posledním elementem na konci základní kontejneru. Omezení přístup pouze nejvyšší element je z důvodu pro použití třídy zásobníku.

- [Queue – třída](../standard-library/queue-class.md) podporuje first-in použity datová struktura. Dobrý analogovým pamatovat by zarovnání pro bankovní pokladnu osoby. Elementy (uživatelé) mohou být přidány do pozadí čáry a jsou odebrány z před řádku. Může být prověřovány přední a zadní straně řádku. Omezení přístup pouze přední a zadní prvky tímto způsobem je kožešiny důvod pomocí třídy fronty.

- [Priority_queue – třída](../standard-library/priority-queue-class.md) řadí jeho prvky tak, aby největší element je vždy na nejvyšší pozici. Podporuje vkládání element a kontroly a odebrání nejvyšší elementu. Dobrý analogovým pamatovat by uživatelé zarovnávání, kde jsou uspořádané podle stáří, výšky nebo jiné kritérium.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Zásobníku](#stack)|Vytvoří `stack` který je prázdný nebo je kopie základní kontejnerového objektu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, aby se přizpůsobit podle `stack`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `stack`.|
|[value_type](#value_type)|Typ, který reprezentuje typ objektu uložené jako element v `stack`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[prázdný](#empty)|Pokud testy `stack` je prázdný.|
|[POP](#pop)|Odebere element z horní části `stack`.|
|[push](#push)|Přidá prvek na začátek `stack`.|
|[Velikost](#size)|Vrátí počet prvků v `stack`.|
|[Horní](#top)|Vrátí odkaz na element v horní části `stack`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<zásobníku >

**Namespace:** – std

## <a name="container_type"></a>  Stack::container_type

Typ, který poskytuje základní kontejner, aby se přizpůsobit.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Všechny tři třídy kontejnerů pořadí standardní knihovna C++ – vector – třída list – třída a deque – třída výchozí – požadavkům má být použit jako základní kontejner pro objekt zásobníku. Uživatelem definované typy, které splňují tyto požadavky mohou být využity také.

Další informace o `Container`, najdete v části poznámky [stack – třída](../standard-library/stack-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [stack::stack](#stack) příklad toho, jak deklarace a používání `container_type`.

## <a name="empty"></a>  Stack::Empty

Testy, pokud zásobník je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** pokud zásobník je prázdný; **false** pokud zásobník představuje neprázdný.

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

## <a name="pop"></a>  Stack::POP

Odebere element z horní části zásobníku.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

V zásobníku musí být neprázdný použít – členská funkce. Horní části zásobníku je pozice obsazena naposledy přidaný prvek a posledním elementem na konci tohoto kontejneru.

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

## <a name="push"></a>  Stack::push

Přidá prvek na začátek konec zásobníku.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Element přidán do horní části zásobníku.

### <a name="remarks"></a>Poznámky

Horní části zásobníku je pozice obsazena naposledy přidaný prvek a posledním elementem na konci tohoto kontejneru.

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

## <a name="size"></a>  Stack::size

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

## <a name="size_type"></a>  Stack::size_type

Typ celé číslo bez znaménka, která představuje počet elementů v sadě.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `size_type` základní kontejneru upraveném zásobníku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`.

## <a name="stack"></a>  Stack::Stack

Vytvoří zásobníku, která je prázdný nebo který je kopií kontejner základní třídy.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parametry

`right` Kontejner, které má být kopie sestavené zásobníku.

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

## <a name="top"></a>  Stack::TOP

Vrátí odkaz na element v horní části zásobníku.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na posledním prvkem v kontejneru v horní části zásobníku.

### <a name="remarks"></a>Poznámky

V zásobníku musí být neprázdný použít – členská funkce. Horní části zásobníku je pozice obsazena naposledy přidaný prvek a posledním elementem na konci tohoto kontejneru.

Pokud vrátí hodnotu, která **horní** je přiřazena k `const_reference`, zásobník objekt nelze změnit. Pokud návratová hodnota **horní** je přiřazena k **odkaz**, je možné upravit objekt zásobníku.

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

## <a name="value_type"></a>  Stack::value_type

Typ, který představuje typ objektu uložené jako element v zásobníku.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `value_type` základní kontejneru upraveném zásobníku.

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

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
