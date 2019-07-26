---
title: priority_queue – třída
ms.date: 11/04/2016
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
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
ms.openlocfilehash: 3591264efec87c2c3454d0f885c19b30b73ae51c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458427"
---
# <a name="priorityqueue-class"></a>priority_queue – třída

Třída adaptivního kontejneru pro šablony, která poskytuje omezení funkcí omezující přístup k hlavnímu prvku určitého základního typu kontejneru, který je vždy největší nebo nejvyšší prioritou. Do priority_queue lze přidat nové prvky a nejvyšší prvek priority_queue lze zkontrolovat nebo odebrat.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Textový*\
Typ dat prvku, který bude uložen v priority_queue.

*Vnitřního*\
Typ podkladového kontejneru, který slouží k implementaci rozhraní priority_queue.

*Porovnán*\
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí v priority_queue. Tento argument je nepovinný a binární `less<typename Container::value_type>` predikát je výchozí hodnota.

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` specifikované v prvním parametru šablony objektu Queue jsou synonyma s [value_type](#value_type) a musí odpovídat typu elementu v základní třídě `Container` kontejneru, která je stanovena druhou šablonou. ukazatele. `Type` Musí být přiřazen, aby bylo možné zkopírovat objekty daného typu a přiřadit hodnoty proměnným tohoto typu.

Priority_queue objedná sekvenci, kterou řídí, voláním objektu uložené funkce třídy `Traits`. Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem.

Vhodné základní třídy kontejneru pro priority_queue zahrnují [třídu deque](../standard-library/deque-class.md) a výchozí [třídu Vector](../standard-library/vector-class.md) nebo jakýkoli jiný kontejner sekvence, který podporuje operace `front`, `push_back`a `pop_back` a a. iterátor náhodného přístupu. Základní třída kontejneru je zapouzdřena v rámci adaptéru kontejneru, který zpřístupňuje pouze omezené sady členských funkcí kontejneru sekvence jako veřejné rozhraní.

Přidávání prvků do a odebírání prvků z `priority_queue` obou má logaritmickou složitost. Přístup k prvkům `priority_queue` v má konstantní složitost.

Existují tři typy adaptérů kontejneru definovaných C++ standardní knihovnou: stack, Queue a priority_queue. Každý z nich omezuje funkčnost některé základní třídy kontejneru, aby poskytovala přesně kontrolované rozhraní pro standardní datovou strukturu.

- [Třída Stack](../standard-library/stack-class.md) podporuje strukturu dat Last-in, First-out (LIFO). Dobrým analogem k tomu, že byste měli mít na paměti, je zásobník talířů. Prvky (pláty) mohou být vloženy, zkontrolovány nebo odebrány pouze z horní části zásobníku, což je poslední prvek na konci základního kontejneru. Omezení pro přístup pouze k hornímu prvku je důvodem pro použití třídy Stack.

- [Třída Queue](../standard-library/queue-class.md) podporuje strukturu dat first in, First-out (FIFO). Dobrým analogovým, kdo by měl mít na paměti, jsou lidé, kteří se budou podělit o bankovní informace. Prvky (lidé) mohou být přidány do zadní části řádku a jsou odebrány z přední části řádku. Může být zkontrolován jak přední, tak zadní strana řádku. Omezení pro přístup pouze k prvkům front a back tímto způsobem je důvodem použití třídy Queue.

- Třída priority_queue řadí své prvky, aby největší prvek byl vždy na nejvyšší pozici. Podporuje vložení elementu a kontrolu a odebrání horního prvku. Dobrým analogovým, co je potřeba mít na paměti, jsou lidé, kteří se doplňují, kde jsou seřazené podle stáří, výšky nebo jiného kritéria.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[priority_queue](#priority_queue)|Vytvoří objekt `priority_queue` , který je prázdný nebo který je kopií rozsahu základního objektu kontejneru nebo jiného `priority_queue`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, který má být upraven pomocí `priority_queue`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `priority_queue`.|
|[value_type](#value_type)|Typ, který představuje typ objektu uložený jako prvek v `priority_queue`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[empty](#empty)|Testuje, zda `priority_queue` je pole prázdné.|
|[výstrah](#pop)|Odebere největší prvek `priority_queue` z horní pozice.|
|[push](#push)|Přidá prvek do fronty priorit na základě priority elementu z operátoru <.|
|[hodnota](#size)|Vrátí počet prvků v `priority_queue`.|
|[vrchol](#top)|Vrátí odkaz const na největší prvek v horní části `priority_queue`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> fronty

**Obor názvů:** std

## <a name="container_type"></a>priority_queue::container_type

Typ, který poskytuje přizpůsobení základního kontejneru.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `Container`šablony. C++ Standardní třída `deque` kontejneru sekvence knihovny a výchozí třída `vector` splňuje požadavky, které mají být použity jako základní kontejner pro objekt priority_queue. Mohou být také použity uživatelsky definované typy splňující požadavky.

Další informace o `Container`naleznete v části poznámky v tématu [Třída priority_queue](../standard-library/priority-queue-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat [](#priority_queue) a používat `container_type`, naleznete v příkladu pro priority_queue.

## <a name="empty"></a>priority_queue:: Empty

Testuje, zda je priority_queue prázdné.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je priority_queue prázdné; **false** , pokud je priority_queue neprázdné.

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

## <a name="pop"></a>priority_queue::p op

Odebere největší prvek priority_queue z horní pozice.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Aby bylo možné použít členskou funkci, musí být priority_queue neprázdný. Horní část priority_queue je vždy obsazena největším prvkem v kontejneru.

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

## <a name="priority_queue"></a>priority_queue::p riority_queue

Vytvoří priority_queue, který je prázdný nebo který je kopií rozsahu základního kontejneru objektu nebo jiného priority_queue.

```cpp
priority_queue();

explicit priority_queue(const Traits& _comp);

priority_queue(const Traits& _comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp, const container_type& _Cont);
```

### <a name="parameters"></a>Parametry

*_comp*\
Funkce Compare typu **constTraits** slouží k seřazení prvků v priority_queue, přičemž výchozí hodnota porovná funkci základního kontejneru.

*_Cont*\
Základní kontejner, ze kterého má být vytvořený priority_queue kopií

*Kliknutím*\
Priority_queue, ze kterého je vytvořená sada kopií.

*první*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*posledního*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Každý z prvních tří konstruktorů určuje prázdnou počáteční priority_queue, druhý také určující typ funkce porovnání (`comp`), která se má použít při vytváření pořadí prvků a třetího explicitního určení `container_type`(`_Cont`), který se má použít. Klíčové slovo **Explicit** potlačí určité druhy automatických převodů typu.

Čtvrtý konstruktor určuje kopii pravého priority_queueu.

Poslední tři konstruktory nakopírují rozsah \[ *první*, *Poslední*) z nějakého kontejneru a používají hodnoty k inicializaci priority_queue se zvýšením explicitního určení typu funkce porovnání třídy `Traits` a `container_type`.

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

## <a name="push"></a>priority_queue::p USH

Přidá prvek do fronty priorit na základě priority elementu z operátoru <.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný do horní části priority_queueu.

### <a name="remarks"></a>Poznámky

Horní část priority_queue je pozice obsazená největším prvkem v kontejneru.

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

## <a name="size"></a>priority_queue:: size

Vrátí počet prvků v priority_queue.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka priority_queue.

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

## <a name="size_type"></a>priority_queue::size_type

Typ unsigned integer, který může představovat počet prvků v objektu priority_queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `size_type` základní kontejner přizpůsobený priority_queue.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`.

## <a name="top"></a>priority_queue:: Top

Vrátí odkaz const na největší prvek v horní části priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na největší prvek, který je určen `Traits` funkcí, objektem priority_queue.

### <a name="remarks"></a>Poznámky

Aby bylo možné použít členskou funkci, musí být priority_queue neprázdný.

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

## <a name="value_type"></a>priority_queue::value_type

Typ, který představuje typ objektu uložený jako prvek v priority_queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `value_type` základní kontejner přizpůsobený priority_queue.

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
