---
title: Queue – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62d3a937d2141134255708d441b901c15a826f7a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="queue-class"></a>queue – třída

Třída adaptéru kontejneru šablony, která poskytuje omezení funkcí pro některé základní typ kontejneru omezení přístupu k elementům přední a zadní. Elementy lze přidat na pozadí nebo odebrat z přední a elementy může být prověřovány na libovolném konci fronty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parametry

*Typ* data elementu typ, který má být uloženy ve frontě

`Container` Typ základního kontejneru použít k implementaci fronty.

## <a name="remarks"></a>Poznámky

Elementy třídy **typ** stanovené v šabloně první parametr objekt fronty jsou shodné s [value_type](#value_type) a musí shodovat s typem elementu v základní třídě kontejneru **Kontejneru** stanoveno druhý parametr šablony. **Typu** musí být přiřaditelný, takže je možné zkopírovat objekty daného typu a přiřadit hodnoty proměnné daného typu.

Zahrnout vhodný základní třídy kontejnerů pro frontu [deque](../standard-library/deque-class.md) a [seznamu](../standard-library/list-class.md), nebo jakékoli jiné pořadí kontejner, který podporuje operace `front`, **zpět** , `push_back`, a `pop_front`. Základní třída kontejneru je zapouzdřený v rámci kontejneru adaptéru, který zveřejňuje jenom omezená sada členské funkce kontejneru pořadí jako veřejné rozhraní.

Fronty objekty jsou v případě porovnatelný z hlediska rovnosti a pouze v případě elementy třídy **typ** jsou porovnatelný z hlediska rovnosti a méně – než porovnatelný z hlediska v případě a pouze v případě elementy třídy **typ** méně – než porovnatelný.

Existují tři typy kontejneru adaptéry standardní knihovny C++ definované: zásobníku, fronty a priority_queue. Každý omezuje funkci některé základní třídy kontejneru zajistit přesněji řízené rozhraní pro standardní datová struktura.

- [Stack – třída](../standard-library/stack-class.md) podporuje last-in ven (LIFO) datová struktura. Dobrý analogovým pamatovat by zásobník desky. Elementy (tabulky) může vložit, prověřovány nebo odebrat pouze z horní části zásobníku, který je posledním elementem na konci základní kontejneru. Omezení přístup pouze nejvyšší element je z důvodu pro použití třídy zásobníku.

- Queue – třída podporuje first-in použity datová struktura. Dobrý analogovým pamatovat by zarovnání pro bankovní pokladnu osoby. Elementy (uživatelé) mohou být přidány do pozadí čáry a jsou odebrány z před řádku. Může být prověřovány přední a zadní straně řádku. Omezení přístup pouze přední a zadní prvky tímto způsobem je z důvodu pro použití třídy fronty.

- [Priority_queue – třída](../standard-library/priority-queue-class.md) řadí jeho prvky tak, aby největší element je vždy na nejvyšší pozici. Podporuje vkládání element a kontroly a odebrání nejvyšší elementu. Dobrý analogovým pamatovat by uživatelé zarovnávání, kde jsou uspořádané podle stáří, výšky nebo jiné kritérium.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Fronty](#queue)|Vytvoří `queue` který je prázdný nebo je kopie základní kontejnerového objektu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, aby se přizpůsobit pomocí `queue`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `queue`.|
|[value_type](#value_type)|Typ, který reprezentuje typ objektu uložené jako element v `queue`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[zpět](#back)|Vrátí odkaz na poslední a naposledy přidají element v zálohování `queue`.|
|[prázdný](#empty)|Pokud testy `queue` je prázdný.|
|[Přední](#front)|Vrátí odkaz na první prvek na před `queue`.|
|[POP](#pop)|Odebere element z před `queue`.|
|[push](#push)|Přidá prvek na zadní straně `queue`.|
|[Velikost](#size)|Vrátí počet prvků v `queue`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fronty >

**Namespace:** – std

## <a name="back"></a>  Queue::back

Vrátí že odkaz na poslední a naposledy přidají element zadní straně fronty.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Posledním elementem fronty. Pokud je fronta prázdná, není definován návratovou hodnotu.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která **zpět** je přiřazena k `const_reference`, nemůže být upraven objekt fronty. Pokud vrátí hodnotu, která **zpět** je přiřazena k **odkaz**, je možné upravit objekt fronty.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu v prázdné frontě.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.

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

Typ, který poskytuje základní kontejner, aby se přizpůsobit.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Dvě třídy kontejnerů pořadí standardní knihovna C++ – třída seznamu a výchozí deque – třída – požadavkům má být použit jako základní kontejner pro objekt fronty. Uživatelem definované typy, které splňují požadavky mohou být využity také.

Další informace o `Container`, najdete v části poznámky [queue – třída](../standard-library/queue-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [fronty](#queue) příklad toho, jak deklarace a používání `container_type`.

## <a name="empty"></a>  Queue::Empty

Testy, pokud fronta je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud je fronta prázdná; **false** Pokud je fronta neprázdný.

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

Vrátí odkaz na první prvek na začátek fronty.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

První prvek fronty. Pokud je fronta prázdná, není definován návratovou hodnotu.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která `front` je přiřazena k `const_reference`, nemůže být upraven objekt fronty. Pokud vrátí hodnotu, která `front` je přiřazena k **odkaz**, je možné upravit objekt fronty.

Členské funkce vrátí hodnotu **odkaz** na první prvek řízené sekvenci, která musí být neprázdný.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu v prázdné frontě.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.

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

Odebere element z začátek fronty.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Fronty musí být neprázdný použít – členská funkce. Na začátek fronty je pozice obsazena naposledy přidaný prvek a posledním elementem na konci tohoto kontejneru.

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

Přidá prvek na stránce do pozadí fronty.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Prvek přidán na zadní straně fronty.

### <a name="remarks"></a>Poznámky

Zpět fronty je pozice obsazena naposledy přidaný prvek a posledním elementem na konci tohoto kontejneru.

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

Vytvoří frontu, který je prázdný nebo který je kopií základní kontejnerového objektu.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parametry

`right` **Const** kontejneru, které má být kopie sestavené fronty.

### <a name="remarks"></a>Poznámky

Výchozí základní kontejner pro frontu je deque. Seznam můžete také zadat jako základní kontejner, ale vektoru, nelze zadat, protože chybí požadovaná `pop_front` – členská funkce.

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

Vrátí počet elementů ve frontě.

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

Typ celé číslo bez znaménka, která představuje počet elementů ve frontě.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `size_type` základní kontejneru upraveném fronty.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [queue::front](#front) příklad toho, jak deklarace a používání `size_type`.

## <a name="value_type"></a>  Queue::value_type

Typ, který představuje typ objektu uložené jako element ve frontě.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `value_type` základní kontejneru upraveném fronty.

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
