---
title: priority_queue – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
dev_langs:
- C++
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e63f13c07ceb6220ba3dc8e7932c7357ed649188
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199235"
---
# <a name="priorityqueue-class"></a>priority_queue – třída

Kontejner adaptér třídu šablony, která poskytuje omezení funkcí omezíte přístup k prvku na vrcholu některé základní typ kontejneru, který je vždycky největší nebo nejvyšší prioritou. Nové elementy lze přidat priority_queue – a prvku na vrcholu priority_queue – můžete prozkoumat nebo odebrat.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
 Typ dat prvku, který bude uložen do priority_queue –.

*Kontejner*<br/>
 Typ základního kontejneru používaný k implementaci priority_queue –.

*Compare*<br/>
 Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v priority_queue –. Tento argument je nepovinný a binární predikát `less<typename Container::value_type>` je výchozí hodnota.

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` stanovené v šabloně první parametr objekt fronty je synonymní s [value_type](#value_type) a musí shodovat s typem elementu v základní třídě kontejneru `Container` stanovených druhý parametr šablony. `Type` Musí být možné přiřadit, takže je možné zkopírovat objekty daného typu a přiřadit proměnné typu hodnoty.

Priority_queue – seřadí sekvence pomocí volání uloženého objektu funkce třídy `Traits`. Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem.

Zahrnout vhodný základní třídy kontejnerů pro priority_queue – [třídou deque](../standard-library/deque-class.md) a ve výchozím nastavení [vector – třída](../standard-library/vector-class.md) nebo jiném pořadí kontejneru, který podporuje operace `front`, `push_back`, a `pop_back` a iterátor náhodného přístupu. Základní třída kontejneru je zapouzdřen v rámci kontejneru adaptér, který zpřístupňuje pouze omezená sada členské funkce kontejneru pořadí jako veřejné rozhraní.

Prvky k přidávání a odebírání elementů z `priority_queue` mají logaritmické složitost. Přístup k prvkům v `priority_queue` má konstantní složitost.

Existují tři typy definované ve standardní knihovně C++ adaptéry kontejneru: zásobník, fronty a priority_queue –. Každý omezuje funkčnost některé základní třídy kontejneru a poskytuje tak přesně řízené rozhraní standardní datovou strukturu.

- [Stack – třída](../standard-library/stack-class.md) podporuje poslední dovnitř, první (ven LIFO) datové struktury. Dobré analogové brát v úvahu by stoh talířů shora. Elementy (tabulky) může vložit, prozkoumat nebo odebrat jenom z horní části zásobníku, což je poslední prvek na konci kontejneru základní. Omezení přístupu jenom k prvku na vrcholu je důvod horizontálních oddílů pomocí třídy zásobníku.

- [Front třídy](../standard-library/queue-class.md) podporuje první dovnitř, první ven (FIFO) datová struktura. Dobré analogové brát v úvahu by zarovnání pro bankovní pokladnu lidí. Elementy (lidé) mohou být přidány do pozadí řádku a odeberou se ze začátku řádku. Přední a zadní řádku může být kontrolována. Omezení přístupu jenom přední a zadní prvky tímto způsobem je důvod horizontálních oddílů pomocí třídy fronty.

- Priority_queue – třída orders jeho prvky tak, aby největšího prvku je vždy na nejvyšší pozici. Podporuje vložení elementu a kontrolu a odstranění prvku na vrcholu. Dobré analogové brát v úvahu by uživatelé zarovnání ve kterém jsou uspořádané podle věku, výšku ani jiné kritérium.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[priority_queue](#priority_queue)|Vytvoří `priority_queue` , který je prázdný nebo který je kopií rozsah objektu základní kontejneru nebo jiných `priority_queue`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejneru upraví `priority_queue`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka představující počet prvků v `priority_queue`.|
|[value_type](#value_type)|Typ, který představuje typ uložený jako prvek v objektu `priority_queue`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[prázdný](#empty)|Testuje, zda `priority_queue` je prázdný.|
|[POP](#pop)|Odstraní největší prvek z `priority_queue` z nejvyšší pozici.|
|[push](#push)|Přidá prvek do prioritní fronty, na základě priority element z operátoru <.|
|[Velikost](#size)|Vrátí počet prvků v `priority_queue`.|
|[nahoru](#top)|Vrátí konstantní odkaz na prvek největší v horní části `priority_queue`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fronty >

**Namespace:** std

## <a name="container_type"></a>  priority_queue::container_type

Typ, který poskytuje základní kontejner, aby ho upravit.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Třída kontejneru sekvence standardní knihovny C++ `deque` a výchozí třídu `vector` požadavkům má být použit jako základní kontejneru pro objekt priority_queue –. Uživatelem definované typy splňující požadavky může také sloužit.

Další informace o `Container`, najdete v části poznámky [priority_queue – třída](../standard-library/priority-queue-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [priority_queue –](#priority_queue) příklad toho, jak deklarace a používání `container_type`.

## <a name="empty"></a>  priority_queue::Empty

Testuje, zda je priority_queue – je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud priority_queue – je prázdná. **false** Pokud priority_queue – je prázdný.

### <a name="example"></a>Příklad

```cpp
// pqueue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue <int> q1, s2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The priority_queue q1 is empty." << endl;
   else
      cout << "The priority_queue q1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The priority_queue s2 is empty." << endl;
   else
      cout << "The priority_queue s2 is not empty." << endl;
}
```

```Output
The priority_queue q1 is not empty.
The priority_queue s2 is empty.
```

## <a name="pop"></a>  priority_queue::POP

Odebere největšího prvku priority_queue – od nejvyšší pozici.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Priority_queue – musí být neprázdné použít členskou funkci. Horní části priority_queue – je vždy obsazena největšího prvku v kontejneru.

### <a name="example"></a>Příklad

```cpp
// pqueue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   priority_queue <int>::size_type i, iii;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;

   q1.pop( );

   iii = q1.size( );
   cout << "After a pop, the priority_queue length is "
        << iii << "." << endl;

   const int& iv = q1.top( );
   cout << "After a pop, the element at the top of the "
        << "priority_queue is " << iv << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
After a pop, the priority_queue length is 2.
After a pop, the element at the top of the priority_queue is 20.
```

## <a name="priority_queue"></a>  priority_queue::priority_queue

Priority_queue –, který je prázdný nebo který je kopii tohoto rozsahu základní kontejnerového objektu nebo jiné priority_queue – vytvoří.

```cpp
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```

### <a name="parameters"></a>Parametry

*kompozice _*<br/>
 Funkce porovnání typu **constTraits** používají k seřazení prvků v priority_queue –, kde je použit výchozí porovnání funkce základní kontejneru.

*_Cont*<br/>
 Základní kontejner, který je vytvořený priority_queue – kopií.

*doprava*<br/>
 Priority_queue –, který je vytvořen objekt set kopií.

*první*<br/>
 Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*poslední*<br/>
 Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

### <a name="remarks"></a>Poznámky

Každý z první tři konstruktory prázdný počáteční priority_queue –, druhé také určuje typ funkce porovnání určuje (`comp`) má být použit při stanovení pořadí prvků a třetí explicitně zadáte `container_type`(`_Cont`) který se má použít. Klíčové slovo **explicitní** potlačí některé druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii priority_queue – *správné*.

Poslední tři konstruktory kopírují rozsah [* první, poslední *) některé kontejneru objektů a použít hodnoty pro inicializaci priority_queue – se zvyšující se explicitností v určování typu funkce porovnání třídy **osobnostní rysy** a `container_type`.

### <a name="example"></a>Příklad

```cpp
// pqueue_ctor.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <deque>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function declares priority_queue
   // with a default vector base container
   priority_queue <int> q1;
   cout << "q1 = ( ";
   while ( !q1.empty( ) )
   {
      cout << q1.top( ) << " ";
      q1.pop( );
   }
   cout << ")" << endl;

   // Explicitly declares a priority_queue with nondefault
   // deque base container
   priority_queue <int, deque <int> > q2;
   q2.push( 5 );
   q2.push( 15 );
   q2.push( 10 );
   cout << "q2 = ( ";
   while ( !q2.empty( ) )
   {
      cout << q2.top( ) << " ";
      q2.pop( );
   }
   cout << ")" << endl;

   // This method of printing out the elements of a priority_queue
   // removes the elements from the priority queue, leaving it empty
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;

   // The third member function declares a priority_queue
   // with a vector base container and specifies that the comparison
   // function greater is to be used for ordering elements
   priority_queue <int, vector<int>, greater<int> > q3;
   q3.push( 2 );
   q3.push( 1 );
   q3.push( 3 );
   cout << "q3 = ( ";
   while ( !q3.empty( ) )
   {
      cout << q3.top( ) << " ";
      q3.pop( );
   }
   cout << ")" << endl;

   // The fourth member function declares a priority_queue and
   // initializes it with elements copied from another container:
   // first, inserting elements into q1, then copying q1 elements into q4
   q1.push( 100 );
   q1.push( 200 );
   priority_queue <int> q4( q1 );
   cout << "q4 = ( ";
   while ( !q4.empty( ) )
   {
      cout << q4.top( ) << " ";
      q4.pop( );
   }
   cout << ")" << endl;

   // Creates an auxiliary vector object v5 to be used to initialize q5
   vector <int> v5;
   vector <int>::iterator v5_Iter;
   v5.push_back( 10 );
   v5.push_back( 30 );
   v5.push_back( 20 );
   cout << "v5 = ( " ;
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )
      cout << *v5_Iter << " ";
   cout << ")" << endl;

   // The fifth member function declares and
   // initializes a priority_queue q5 by copying the
   // range v5[ first,  last) from vector v5
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );
   cout << "q5 = ( ";
   while ( !q5.empty( ) )
   {
      cout << q5.top( ) << " ";
      q5.pop( );
   }
   cout << ")" << endl;

   // The sixth member function declares a priority_queue q6
   // with a comparison function greater and initializes q6
   // by copying the range v5[ first,  last) from vector v5
   priority_queue <int, vector<int>, greater<int> >
      q6( v5.begin( ), v5.begin( ) + 2 );
   cout << "q6 = ( ";
   while ( !q6.empty( ) )
   {
      cout << q6.top( ) << " ";
      q6.pop( );
   }
   cout << ")" << endl;
}
```

## <a name="push"></a>  priority_queue::push

Přidá prvek do prioritní fronty, na základě priority element z operátoru <.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
 Prvek přidán do horní části priority_queue –.

### <a name="remarks"></a>Poznámky

Horní části priority_queue – je pozice obsazena největšího prvku v kontejneru.

### <a name="example"></a>Příklad

```cpp
// pqueue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="size"></a>  priority_queue::size

Vrátí počet prvků priority_queue –.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka priority_queue –.

### <a name="example"></a>Příklad

```cpp
// pqueue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, q2;
   priority_queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The priority_queue length is now " << i << "." << endl;
}
```

```Output
The priority_queue length is 1.
The priority_queue length is now 2.
```

## <a name="size_type"></a>  priority_queue::size_type

Typ celé číslo bez znaménka představující počet prvků v priority_queue –.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `size_type` upravena priority_queue – základní kontejneru.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`.

## <a name="top"></a>  priority_queue::TOP

Vrátí konstantní odkaz na prvek největší v horní části priority_queue –.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na největšího prvku určenému `Traits` funkce, objekt priority_queue –.

### <a name="remarks"></a>Poznámky

Priority_queue – musí být neprázdné použít členskou funkci.

### <a name="example"></a>Příklad

```cpp
// pqueue_top.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="value_type"></a>  priority_queue::value_type

Typ, který představuje typ objektu uložený jako prvek v priority_queue –.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type` upravena priority_queue – základní kontejneru.

### <a name="example"></a>Příklad

```cpp
// pqueue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   priority_queue<int> q1;
   q1.push( AnInt );
   cout << "The element at the top of the priority_queue is "
        << q1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the priority_queue is 69.
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
