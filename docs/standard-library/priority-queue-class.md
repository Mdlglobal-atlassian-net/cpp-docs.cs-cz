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
ms.openlocfilehash: cef85eafaa3aab1c448234399f146191de957b8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323020"
---
# <a name="priority_queue-class"></a>priority_queue – třída

Třída adaptéru kontejneru šablony, která poskytuje omezení funkcí omezujících přístup k hornímu prvku některého základního typu kontejneru, který je vždy největší nebo s nejvyšší prioritou. Nové prvky mohou být přidány do priority_queue a horní prvek priority_queue mohou být zkontrolovány nebo odstraněny.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Typ*\
Datový typ prvku, který má být uložen v priority_queue.

*Kontejner*\
Typ základní kontejner u implementovat priority_queue.

*Porovnat*\
Typ, který poskytuje objekt funkce, který může porovnat dva hodnoty elementu jako klíče řazení k určení jejich relativní pořadí v priority_queue. Tento argument je volitelný a binární `less<typename Container::value_type>` predikát je výchozí hodnota.

## <a name="remarks"></a>Poznámky

Prvky třídy `Type` stanovené v prvním parametru šablony objektu fronty jsou synonymem [value_type](#value_type) a musí `Container` odpovídat typu prvku v základní třídě kontejneru stanovenému druhým parametrem šablony. Musí `Type` být přiřaditelné, aby bylo možné kopírovat objekty tohoto typu a přiřadit hodnoty proměnným tohoto typu.

Priority_queue seřadí sekvenci, kterou řídí `Traits`voláním uloženého objektu funkce třídy . Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem.

Vhodné základní třídy kontejnerů pro priority_queue zahrnují [třídu deque](../standard-library/deque-class.md) a výchozí `front` `push_back` [vektorovou třídu](../standard-library/vector-class.md) nebo jakýkoli jiný kontejner sekvence, který podporuje operace aplikace , a `pop_back` a iterátor s náhodným přístupem. Základní třída kontejneru je zapouzdřena v adaptéru kontejneru, který zveřejňuje pouze omezenou sadu funkce kontejneru sekvence jako veřejné rozhraní.

Přidání prvků a odebrání `priority_queue` prvků z obou mají logaritmickou složitost. Přístup k prvkům `priority_queue` v má konstantní složitost.

Standardní knihovna jazyka C++definuje tři typy adaptérů kontejnerů: zásobník, fronta a priority_queue. Každý omezuje funkce některé základní třídy kontejneru poskytnout přesně řízené rozhraní pro standardní datové struktury.

- [Třída zásobníku](../standard-library/stack-class.md) podporuje strukturu dat poslední dovnitř, první ven (LIFO). Dobrým analogem, který je třeba mít na paměti, by byl stoh desek. Prvky (desky) mohou být vloženy, zkontrolovány nebo odstraněny pouze z horní části zásobníku, což je poslední prvek na konci základního kontejneru. Omezení přístupu pouze k hornímu prvku je důvodem pro použití třídy zásobníku.

- [Třída fronty](../standard-library/queue-class.md) podporuje strukturu dat fifo (first-in, first-out). Dobrým analogem, který je třeba mít na paměti, by byli lidé, kteří stojí frontu na bankovní pokladní. Prvky (osoby) mohou být přidány do zadní části řádku a jsou odstraněny z přední části řádku. Přední i zadní část linky mohou být zkontrolovány. Omezení přístupu pouze přední a zadní prvky tímto způsobem je důvod pro použití třídy fronty.

- Třída priority_queue objednává své prvky tak, aby největší prvek byl vždy na nejvyšší pozici. Podporuje vkládání prvku a kontrolu a odstranění horního prvku. Dobrým analogem, který je třeba mít na paměti, by byli lidé, kteří se řadí tam, kde jsou uspořádáni podle věku, výšky nebo jiného kritéria.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[priority_queue](#priority_queue)|Konstrukce, `priority_queue` který je prázdný nebo který je kopií rozsahu základní ho `priority_queue`kontejneru objektu nebo jiné .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, `priority_queue`který má být upraven .|
|[size_type](#size_type)|Nepodepsaný podnosný typ, který může představovat počet prvků v . `priority_queue`|
|[value_type](#value_type)|Typ, který představuje typ objektu uloženého `priority_queue`jako prvek v .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[empty](#empty)|Testuje, `priority_queue` pokud je prázdný.|
|[Pop](#pop)|Odstraní největší prvek `priority_queue` z horní pozice.|
|[Push](#push)|Přidá prvek do fronty priorit na základě priority prvku z operátoru<.|
|[Velikost](#size)|Vrátí počet prvků v `priority_queue`rozhraní .|
|[Top](#top)|Vrátí odkaz na největší prvek v horní `priority_queue`části .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> fronty

**Obor názvů:** std

## <a name="priority_queuecontainer_type"></a><a name="container_type"></a>priority_queue::container_type

Typ, který poskytuje základní kontejner, který má být upraven.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Container`parametr šablony . Třída `deque` kontejneru sekvencí standardní knihovny jazyka C++ a výchozí třída `vector` splňují požadavky, které mají být použity jako základní kontejner pro priority_queue objekt. Mohou být rovněž použity uživatelem definované typy splňující požadavky.

Další informace `Container`naleznete v části Poznámky v tématu [priority_queue třída.](../standard-library/priority-queue-class.md)

### <a name="example"></a>Příklad

Příklad pro [priority_queue](#priority_queue) najdete příklad, jak `container_type`deklarovat a používat .

## <a name="priority_queueempty"></a><a name="empty"></a>priority_queue::prázdný

Testuje, pokud je priority_queue prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je priority_queue prázdná; **false,** pokud priority_queue není prázdný.

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

## <a name="priority_queuepop"></a><a name="pop"></a>priority_queue::pop

Odstraní největší prvek priority_queue z horní pozice.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Priority_queue musí být neprázdný, aby bylo možné použít členskou funkci. Horní část priority_queue je vždy obsazena největším prvkem v kontejneru.

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

## <a name="priority_queuepriority_queue"></a><a name="priority_queue"></a>priority_queue::priority_queue

Vytvoří priority_queue, která je prázdná nebo je kopií rozsahu základního kontejneru nebo jiného priority_queue.

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
Funkce porovnání typu **constTraits** slouží k pořadí prvků v priority_queue, který výchozí porovnání funkce základníkontejner.

*_Cont*\
Základní kontejner, jehož vyrobeno priority_queue má být kopie.

*Právo*\
priority_queue, které je vytvořená sada kopie.

*První*\
Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Každý z prvních tří konstruktorů určuje prázdnou počáteční priority_queue, druhý také`comp`specifikuje typ funkce porovnání ( ) která má být `container_type` `_Cont`použita při určování pořadí prvků a třetí explicitně specifikuje ( ). Klíčové slovo **explicitní** potlačí určité druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii priority_queue *pravé*.

Poslední tři konstruktory \[zkopírují oblast *první*, *poslední*) některé hokontejneru a pomocí hodnot inicializovat priority_queue `Traits` s `container_type`rostoucí explicitní při určování typu funkce porovnání třídy a .

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

## <a name="priority_queuepush"></a><a name="push"></a>priority_queue::push

Přidá prvek do fronty priorit na základě priority prvku z operátoru<.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Prvek přidán do horní části priority_queue.

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

## <a name="priority_queuesize"></a><a name="size"></a>priority_queue::velikost

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

## <a name="priority_queuesize_type"></a><a name="size_type"></a>priority_queue::size_type

Nepodepsaný podčíslení typ, který může představovat počet prvků v priority_queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `size_type` pro základní kontejner přizpůsobený priority_queue.

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak `size_type`deklarovat a používat .

## <a name="priority_queuetop"></a><a name="top"></a>priority_queue::nahoru

Vrátí odkaz na největší prvek v horní části priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na největší prvek, jak `Traits` je určeno funkce, objekt priority_queue.

### <a name="remarks"></a>Poznámky

Priority_queue musí být neprázdný, aby bylo možné použít členskou funkci.

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

## <a name="priority_queuevalue_type"></a><a name="value_type"></a>priority_queue::value_type

Typ, který představuje typ objektu uloženého jako prvek v priority_queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `value_type` pro základní kontejner přizpůsobený priority_queue.

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

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
