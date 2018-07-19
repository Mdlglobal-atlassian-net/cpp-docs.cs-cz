---
title: Queue – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d50b53f9c06c5edbd159e7e2bac112f6f30432df
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954913"
---
# <a name="queue-class"></a>queue – třída

Kontejner adaptér třídu šablony, která poskytuje omezení funkcí pro některé základní typ kontejneru, omezíte přístup k prvkům přední a zadní. Elementy lze přidat na pozadí nebo odebrán z front a prvky můžete prozkoumat na jednom konci fronty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parametry

*Typ* typ dat prvku, který bude uložen do fronty

*Kontejner* typu základního kontejneru používaný k implementaci fronty.

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` stanovené v šabloně první parametr objekt fronty je synonymní s [value_type](#value_type) a musí shodovat s typem elementu v základní třídě kontejneru `Container` stanovených druhý parametr šablony. `Type` Musí být možné přiřadit, takže je možné zkopírovat objekty daného typu a přiřadit proměnné typu hodnoty.

Zahrnout vhodný základní třídy kontejnerů pro frontu [deque](../standard-library/deque-class.md) a [seznamu](../standard-library/list-class.md), nebo jiném pořadí kontejneru, který podporuje operace `front`, `back`, `push_back`, a `pop_front`. Základní třída kontejneru je zapouzdřen v rámci kontejneru adaptér, který zpřístupňuje pouze omezená sada členské funkce kontejneru pořadí jako veřejné rozhraní.

Fronty objekty jsou srovnatelné if rovnosti a pouze v případě elementů třídy `Type` lze porovnávat rovnosti a jsou méně – než srovnatelné Pokud a pouze v případě elementů třídy `Type` jsou méně – než srovnatelná s hodnotou.

Existují tři typy definované ve standardní knihovně C++ adaptéry kontejneru: zásobník, fronty a priority_queue –. Každý omezuje funkčnost některé základní třídy kontejneru a poskytuje tak přesně řízené rozhraní standardní datovou strukturu.

- [Stack – třída](../standard-library/stack-class.md) podporuje poslední dovnitř, první (ven LIFO) datové struktury. Dobré analogové brát v úvahu by stoh talířů shora. Elementy (tabulky) může vložit, prozkoumat nebo odebrat jenom z horní části zásobníku, což je poslední prvek na konci kontejneru základní. Omezení přístupu jenom k prvku na vrcholu je důvod horizontálních oddílů pomocí třídy zásobníku.

- Třída fronty podporuje první dovnitř, první ven (FIFO) datová struktura. Dobré analogové brát v úvahu by zarovnání pro bankovní pokladnu lidí. Elementy (lidé) mohou být přidány do pozadí řádku a odeberou se ze začátku řádku. Přední a zadní řádku může být kontrolována. Omezení přístupu jenom přední a zadní prvky tímto způsobem je důvod horizontálních oddílů pomocí třídy fronty.

- [Priority_queue – třída](../standard-library/priority-queue-class.md) orders jeho prvky tak, aby největšího prvku je vždy na nejvyšší pozici. Podporuje vložení elementu a kontrolu a odstranění prvku na vrcholu. Dobré analogové brát v úvahu by uživatelé zarovnání ve kterém jsou uspořádané podle věku, výšku ani jiné kritérium.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[fronty](#queue)|Vytvoří `queue` , který je prázdný nebo který je kopií základní kontejnerového objektu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejneru upraví `queue`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka představující počet prvků v `queue`.|
|[value_type](#value_type)|Typ, který představuje typ uložený jako prvek v objektu `queue`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zpět](#back)|Vrátí odkaz na poslední a naposledy přidat prvek při zálohování `queue`.|
|[prázdný](#empty)|Testuje, zda `queue` je prázdný.|
|[Přední](#front)|Vrátí odkaz na první prvek na začátku `queue`.|
|[POP](#pop)|Odstraní prvek z přední části `queue`.|
|[push](#push)|Přidá prvek na pozadí `queue`.|
|[Velikost](#size)|Vrátí počet prvků v `queue`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fronty >

**Namespace:** std

## <a name="back"></a>  Queue::back

Vrátí že odkaz na poslední a naposledy přidat element zádi fronty.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední element objektu do fronty. Pokud je fronta prázdná, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `back` je přiřazen `const_reference`, nelze upravit objekt fronty. Pokud návratová hodnota `back` je přiřazen `reference`, objekt fronty je možné upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku v prázdné frontě.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

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

## <a name="container_type"></a>  Queue::container_type

Typ, který poskytuje základní kontejner, aby ho upravit.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Dvě třídy kontejnerů sekvence standardní knihovny C++ – třídy seznamu a výchozí deque – požadavkům má být použit jako základní kontejneru pro objekt fronty. Uživatelem definované typy splňující požadavky může také sloužit.

Další informace o `Container`, najdete v části poznámky [front třídy](../standard-library/queue-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [fronty](#queue) příklad toho, jak deklarace a používání `container_type`.

## <a name="empty"></a>  Queue::Empty

Testuje, zda je fronta je prázdná.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronta je prázdná. **false** Pokud fronta je prázdný.

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

## <a name="front"></a>  Queue::front

Vrátí odkaz na první prvek na začátku fronty.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

První prvek fronty. Pokud je fronta prázdná, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `front` je přiřazen `const_reference`, nelze upravit objekt fronty. Pokud návratová hodnota `front` je přiřazen `reference`, objekt fronty je možné upravit.

Členská funkce vrátí `reference` na první prvek řízené sekvence, která musí být prázdný.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku v prázdné frontě.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

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

## <a name="pop"></a>  Queue::POP

Odebere element ze začátku fronty.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Fronty musí být neprázdné použít členskou funkci. Na začátek fronty je obsazena naposledy přidaný prvek pozice a poslední prvek na konci kontejneru.

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

## <a name="push"></a>  Queue::push

Přidá prvek na pozadí do fronty.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val* prvek přidán na pozadí do fronty.

### <a name="remarks"></a>Poznámky

Zpět do fronty je obsazena naposledy přidaný prvek pozice a poslední prvek na konci kontejneru.

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

## <a name="queue"></a>  Queue::Queue

Vytvoří frontu, který je prázdný nebo který je kopii základní kontejnerového objektu.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parametry

*správné* **const** kontejneru je vytvořený fronty kopií.

### <a name="remarks"></a>Poznámky

Výchozí základní kontejner pro frontu je deque. Můžete také zadat seznam jako kontejner základní, ale vektoru, nelze zadat, protože postrádá požadovaný `pop_front` členskou funkci.

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

## <a name="size"></a>  Queue::size

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

## <a name="size_type"></a>  Queue::size_type

Typ celé číslo bez znaménka představující počet prvků ve frontě.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `size_type` základní kontejneru přizpůsobené fronty.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [queue::front](#front) příklad toho, jak deklarace a používání `size_type`.

## <a name="value_type"></a>  Queue::value_type

Typ, který představuje typ objektu uložený jako prvek ve frontě.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type` základní kontejneru přizpůsobené fronty.

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

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
