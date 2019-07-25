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
ms.openlocfilehash: d282d3ea54528b422509f4259e2d9a191f88e091
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453791"
---
# <a name="stack-class"></a>stack – třída

Třída adaptéru pro kontejner šablon, která poskytuje omezení funkcí omezující přístup k prvku, který byl naposledy přidán k některému základnímu typu kontejneru. Třída stack se používá, pokud je důležité, aby bylo jasné, že se v kontejneru provádí pouze operace zásobníku.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= deque <Type>>
class stack
```

### <a name="parameters"></a>Parametry

*Textový*\
Typ dat prvku, který bude uložen v zásobníku.

*Vnitřního*\
Typ podkladového kontejneru, který slouží k implementaci zásobníku. Výchozí hodnota je `deque`typ třídy  *\<>* .

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` specifikované v prvním parametru šablony objektu Stack jsou synonyma s [value_type](#value_type) a musí odpovídat typu elementu v základní třídě `Container` kontejneru, která je stanovena druhou šablonou. ukazatele. `Type` Musí být přiřazen, aby bylo možné zkopírovat objekty daného typu a přiřadit hodnoty proměnným tohoto typu.

Vhodné základní třídy kontejneru pro zásobník zahrnují [deque](../standard-library/deque-class.md), třídu [seznamu](../standard-library/list-class.md)a [třídu Vector](../standard-library/vector-class.md)nebo jakýkoli jiný kontejner sekvence, `back`který podporuje operace, `push_back`a `pop_back`. Základní třída kontejneru je zapouzdřena v rámci adaptéru kontejneru, který zpřístupňuje pouze omezené sady členských funkcí kontejneru sekvence jako veřejné rozhraní.

Objekty zásobníku jsou srovnatelné, pokud a pouze v případě, že prvky třídy `Type` jsou srovnatelné a jsou menší než porovnatelné, pokud jsou a pouze v případě, že `Type` prvky třídy jsou menší než srovnatelné.

- Třída Stack podporuje strukturu dat Last-in, First-out (LIFO). Dobrým analogem k tomu, že byste měli mít na paměti, je zásobník talířů. Prvky (pláty) mohou být vloženy, zkontrolovány nebo odebrány pouze z horní části zásobníku, což je poslední prvek na konci základního kontejneru. Omezení pro přístup pouze k hornímu prvku je důvodem pro použití třídy Stack.

- [Třída Queue](../standard-library/queue-class.md) podporuje strukturu dat first in, First-out (FIFO). Dobrým analogovým, kdo by měl mít na paměti, jsou lidé, kteří se budou podělit o bankovní informace. Prvky (lidé) mohou být přidány do zadní části řádku a jsou odebrány z přední části řádku. Může být zkontrolován jak přední, tak zadní strana řádku. Omezení pro přístup pouze k předním a zadním prvkům tímto způsobem je důvodem použití třídy Queue.

- [Třída priority_queue](../standard-library/priority-queue-class.md) řadí své prvky, aby největší prvek byl vždy na nejvyšší pozici. Podporuje vložení elementu a kontrolu a odebrání horního prvku. Dobrým analogovým, co je potřeba mít na paměti, jsou lidé, kteří se doplňují, kde jsou seřazené podle stáří, výšky nebo jiného kritéria.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[vrstvě](#stack)|Vytvoří objekt, který je prázdný nebo který je kopií základního objektu kontejneru. `stack`|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, který má být upraven pomocí `stack`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `stack`.|
|[value_type](#value_type)|Typ, který představuje typ objektu uložený jako prvek v `stack`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[empty](#empty)|Testuje, zda `stack` je pole prázdné.|
|[výstrah](#pop)|Odebere prvek z horní `stack`části.|
|[push](#push)|Přidá prvek na začátek `stack`.|
|[hodnota](#size)|Vrátí počet prvků v `stack`.|
|[vrchol](#top)|Vrátí odkaz na prvek v horní `stack`části.|

## <a name="container_type"></a>container_type

Typ, který poskytuje přizpůsobení základního kontejneru.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `Container`šablony. Všechny tři C++ standardní třídy kontejneru sekvence knihovny – Třída Vector, třída seznamu a výchozí třída deque – splňují požadavky, které se mají použít jako základní kontejner pro objekt stacku. Mohou být také použity uživatelsky definované typy, které splňují tyto požadavky.

Další informace o `Container`naleznete v části poznámky v tématu [Třída zásobníku](../standard-library/stack-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `container_type`, naleznete v příkladu pro [stack:: stack](#stack) .

## <a name="empty"></a>obsahovat

Testuje, zda je zásobník prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je zásobník prázdný; **false** , pokud je zásobník neprázdný.

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

## <a name="pop"></a>výstrah

Odebere prvek z vrcholu zásobníku.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Aby bylo možné použít členskou funkci, zásobník nesmí být prázdný. Horní část zásobníku je pozice obsazená naposledy přidaným prvkem a je posledním prvkem na konci kontejneru.

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

## <a name="push"></a>replik

Přidá prvek do horní části zásobníku.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný do horní části zásobníku.

### <a name="remarks"></a>Poznámky

Horní část zásobníku je pozice obsazená naposledy přidaným prvkem a je posledním prvkem na konci kontejneru.

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

## <a name="size"></a>hodnota

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

## <a name="size_type"></a>size_type

Typ unsigned integer, který může představovat počet prvků v zásobníku.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `size_type` základní kontejner přizpůsobený zásobníkem.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`.

## <a name="stack"></a>vrstvě

Vytvoří zásobník, který je prázdný nebo který je kopií základní třídy kontejneru.

```cpp
stack();

explicit stack(const container_type& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Kontejner, ze kterého má být vytvořen zásobník kopií.

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

## <a name="top"></a>vrchol

Vrátí odkaz na prvek v horní části zásobníku.

```cpp
reference top();

const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek v kontejneru v horní části zásobníku.

### <a name="remarks"></a>Poznámky

Aby bylo možné použít členskou funkci, zásobník nesmí být prázdný. Horní část zásobníku je pozice obsazená naposledy přidaným prvkem a je posledním prvkem na konci kontejneru.

Pokud `top` je vrácená hodnota přiřazena `const_reference`k, objekt stack nelze upravit. Pokud `top` je vrácená hodnota přiřazena `reference`k, lze objekt stack upravit.

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

## <a name="value_type"></a>value_type

Typ, který představuje typ objektu uložený jako prvek v zásobníku.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type` základní kontejner přizpůsobený zásobníkem.

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
