---
title: queue – třída
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: 512b9499e63933a71a27a87f91a3bef8a65339e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890847"
---
# <a name="queue-class"></a>queue – třída

Třída adaptéru pro kontejner šablon, která poskytuje omezení funkčnosti pro určitý typ kontejneru, a omezuje přístup k předním a zadním prvkům. Prvky lze přidat zpět nebo odebrat z front a prvky lze kontrolovat na konci fronty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Typ dat prvku, který bude uložen ve frontě

\ *kontejneru*
Typ podkladového kontejneru, který se používá k implementaci fronty.

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` stanovené v prvním parametru šablony objektu Queue jsou synonyma s [value_type](#value_type) a musí odpovídat typu elementu v podkladové třídě kontejneru `Container` stanovené druhým parametrem šablony. `Type` musí být možné přiřadit, aby bylo možné zkopírovat objekty daného typu a přiřadit hodnoty proměnným tohoto typu.

Vhodné základní třídy kontejnerů pro frontu zahrnují [deque](../standard-library/deque-class.md) a [list](../standard-library/list-class.md)nebo jakýkoli jiný kontejner sekvence, který podporuje operace `front`, `back`, `push_back`a `pop_front`. Základní třída kontejneru je zapouzdřena v rámci adaptéru kontejneru, který zpřístupňuje pouze omezené sady členských funkcí kontejneru sekvence jako veřejné rozhraní.

Objekty fronty jsou srovnatelné, pokud a pouze pokud jsou prvky třídy `Type` porovnatelné a jsou menší než srovnatelné, pokud je a pouze v případě, že prvky `Type` třídy jsou menší než srovnatelné.

Existují tři typy adaptérů kontejneru definovaných C++ standardní knihovnou: zásobník, fronta a priority_queue. Každý z nich omezuje funkčnost některé základní třídy kontejneru, aby poskytovala přesně kontrolované rozhraní pro standardní datovou strukturu.

- [Třída Stack](../standard-library/stack-class.md) podporuje strukturu dat Last-in, First-out (LIFO). Dobrým analogem k tomu, že byste měli mít na paměti, je zásobník talířů. Prvky (pláty) mohou být vloženy, zkontrolovány nebo odebrány pouze z horní části zásobníku, což je poslední prvek na konci základního kontejneru. Omezení pro přístup pouze k hornímu prvku je důvodem pro použití třídy Stack.

- Třída Queue podporuje strukturu dat first in, First-out (FIFO). Dobrým analogovým, kdo by měl mít na paměti, jsou lidé, kteří se budou podělit o bankovní informace. Prvky (lidé) mohou být přidány do zadní části řádku a jsou odebrány z přední části řádku. Může být zkontrolován jak přední, tak zadní strana řádku. Omezení pro přístup pouze k prvkům front a back tímto způsobem je důvodem použití třídy Queue.

- [Třída priority_queue](../standard-library/priority-queue-class.md) řadí své prvky, aby největší prvek byl vždy na nejvyšší pozici. Podporuje vložení elementu a kontrolu a odebrání horního prvku. Dobrým analogovým, co je potřeba mít na paměti, jsou lidé, kteří se doplňují, kde jsou seřazené podle stáří, výšky nebo jiného kritéria.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[provedených](#queue)|Vytvoří `queue`, který je prázdný nebo který je kopií základního objektu kontejneru.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, který má být upraven pomocí `queue`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `queue`.|
|[value_type](#value_type)|Typ, který představuje typ objektu uložený jako prvek v `queue`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[návrat](#back)|Vrátí odkaz na poslední a naposledy přidaný prvek na zadní straně `queue`.|
|[obsahovat](#empty)|Testuje, zda je `queue` prázdné.|
|[dopředu](#front)|Vrátí odkaz na první prvek na začátku `queue`.|
|[výstrah](#pop)|Odebere prvek z přední části `queue`.|
|[push](#push)|Přidá prvek do pozadí `queue`.|
|[hodnota](#size)|Vrátí počet prvků v `queue`.|

## <a name="back"></a>návrat

Vrátí odkaz na poslední a naposledy přidaný prvek na zadní stranu fronty.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední prvek fronty. Pokud je fronta prázdná, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `back` přiřazena k `const_reference`, nelze objekt Queue upravit. Pokud je vrácená hodnota `back` přiřazená k `reference`, objekt fronty se dá upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě za běhu, pokud se pokusíte o přístup k elementu v prázdné frontě.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Příklad

```cpp
// queue_back.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 11 );

   int& i = q1.back( );
   const int& ii = q1.front( );

   cout << "The integer at the back of queue q1 is " << i
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << ii
        << "." << endl;
}
```

## <a name="container_type"></a>container_type

Typ, který poskytuje přizpůsobení základního kontejneru.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Dvě C++ standardní třídy kontejneru sekvence knihovny – Třída list a výchozí třída deque – splňují požadavky, které se mají použít jako základní kontejner pro objekt Queue. Mohou být také použity uživatelsky definované typy splňující požadavky.

Další informace o `Container`naleznete v části poznámky v tématu [Třída fronty](../standard-library/queue-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `container_type`, najdete v příkladu pro [frontu](#queue) .

## <a name="empty"></a>obsahovat

Testuje, zda je fronta prázdná.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je fronta prázdná; **false** , pokud je fronta neprázdná.

### <a name="example"></a>Příklad

```cpp
// queue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The queue q1 is empty." << endl;
   else
      cout << "The queue q1 is not empty." << endl;

   if ( q2.empty( ) )
      cout << "The queue q2 is empty." << endl;
   else
      cout << "The queue q2 is not empty." << endl;
}
```

```Output
The queue q1 is not empty.
The queue q2 is empty.
```

## <a name="front"></a>dopředu

Vrátí odkaz na první prvek na začátku fronty.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

První prvek fronty. Pokud je fronta prázdná, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `front` přiřazena k `const_reference`, nelze objekt Queue upravit. Pokud je vrácená hodnota `front` přiřazená k `reference`, objekt fronty se dá upravit.

Členská funkce vrátí `reference` na první prvek řízené sekvence, který nesmí být prázdný.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě za běhu, pokud se pokusíte o přístup k elementu v prázdné frontě.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Příklad

```cpp
// queue_front.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main() {
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   int& ii = q1.back( );
   int& iii = q1.front( );

   cout << "The integer at the back of queue q1 is " << ii
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << iii
        << "." << endl;
}
```

## <a name="pop"></a>výstrah

Odebere prvek z přední části fronty.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Aby bylo možné použít členskou funkci, musí být fronta neprázdná. Horní část fronty je pozice obsazená naposledy přidaným prvkem a je posledním prvkem na konci kontejneru.

### <a name="example"></a>Příklad

```cpp
// queue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;

   q1.pop( );

   i = q1.size( );
   cout << "After a pop the queue length is "
        << i << "." << endl;

   i = q1. front ( );
   cout << "After a pop, the element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
After a pop the queue length is 2.
After a pop, the element at the front of the queue is 20.
```

## <a name="push"></a>replik

Přidá prvek do pozadí fronty.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

\ *Val*
Prvek byl přidán do pozadí fronty.

### <a name="remarks"></a>Poznámky

Zadní část fronty je pozice obsazená naposledy přidaným prvkem a je posledním prvkem na konci kontejneru.

### <a name="example"></a>Příklad

```cpp
// queue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
```

## <a name="queue"></a>provedených

Vytvoří frontu, která je prázdná nebo je kopií základního objektu kontejneru.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Kontejner **const** , jehož vytvořená fronta bude kopií.

### <a name="remarks"></a>Poznámky

Výchozí základní kontejner pro frontu je deque. Seznam můžete také zadat jako základní kontejner, ale nelze zadat Vector, protože nemá požadovanou členskou funkci `pop_front`.

### <a name="example"></a>Příklad

```cpp
// queue_queue.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queue with default deque base container
   queue <char> q1;

   // Explicitly declares a queue with deque base container
   queue <char, deque<char> > q2;

   // These lines don't cause an error, even though they
   // declares a queue with a vector base container
   queue <int, vector<int> > q3;
   q3.push( 10 );
   // but the following would cause an error because vector has
   // no pop_front member function
   // q3.pop( );

   // Declares a queue with list base container
   queue <int, list<int> > q4;

   // The second member function copies elements from a container
   list<int> li1;
   li1.push_back( 1 );
   li1.push_back( 2 );
   queue <int, list<int> > q5( li1 );
   cout << "The element at the front of queue q5 is "
        << q5.front( ) << "." << endl;
   cout << "The element at the back of queue q5 is "
        << q5.back( ) << "." << endl;
}
```

```Output
The element at the front of queue q5 is 1.
The element at the back of queue q5 is 2.
```

## <a name="size"></a>hodnota

Vrátí počet prvků ve frontě.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka fronty.

### <a name="example"></a>Příklad

```cpp
// queue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2;
   queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The queue length is now " << i << "." << endl;
}
```

```Output
The queue length is 1.
The queue length is now 2.
```

## <a name="size_type"></a>size_type

Typ unsigned integer, který může představovat počet prvků ve frontě.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `size_type` základního kontejneru přizpůsobeného frontou.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `size_type`, naleznete v příkladu pro [front:: front](#front) .

## <a name="value_type"></a>value_type

Typ, který představuje typ objektu uložený jako prvek ve frontě.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type` základního kontejneru přizpůsobeného frontou.

### <a name="example"></a>Příklad

```cpp
// queue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   queue<int> q1;
   q1.push(AnInt);
   cout << "The element at the front of the queue is "
        << q1.front( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the front of the queue is 69.
```

## <a name="see-also"></a>Viz také

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
