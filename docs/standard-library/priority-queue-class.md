---
title: priority_queue – třída | Microsoft Docs
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
ms.openlocfilehash: 149d255dd82d0dff2d2ddb1101b38bf05c69673a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861913"
---
# <a name="priorityqueue-class"></a>priority_queue – třída

Třída adaptéru kontejneru šablony, která poskytuje omezení funkcí omezení přístupu k nejvyšší element některé základní typ kontejneru, který je vždycky na největší nebo nejvyšší prioritou. Nové prvky lze přidat do priority_queue a nejvyšší element priority_queue může být prověřovány nebo odebrat.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>Parametry

*Typ* element datový typ se neukládají v priority_queue.

`Container` Typ základního kontejneru použít k implementaci priority_queue.

*Porovnání* typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v priority_queue. Tento argument je volitelný a binární predikát **menší***\<*** typename** *kontejneru ***:: value_type*** >* je výchozí hodnota.

## <a name="remarks"></a>Poznámky

Elementy třídy **typ** stanovené v šabloně první parametr objekt fronty jsou shodné s [value_type](#value_type) a musí shodovat s typem elementu v základní třídě kontejneru **Kontejneru** stanoveno druhý parametr šablony. **Typu** musí být přiřaditelný, takže je možné zkopírovat objekty daného typu a přiřadit hodnoty proměnné daného typu.

Priority_queue řadí pořadí jimi řídí voláním funkce uložené objektu třídy **vlastnosti**. Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem.

Zahrnout vhodný základní třídy kontejnerů pro priority_queue [deque – třída](../standard-library/deque-class.md) a ve výchozím nastavení [vector – třída](../standard-library/vector-class.md) nebo jakékoli jiné pořadí kontejner, který podporuje operace `front`, `push_back`, a `pop_back` a iterator náhodný přístup. Základní třída kontejneru je zapouzdřený v rámci kontejneru adaptéru, který zveřejňuje jenom omezená sada členské funkce kontejneru pořadí jako veřejné rozhraní.

Elementy pro přidávání a odebírání elementů z `priority_queue` mají logaritmické složitost. Přístup k elementům v `priority_queue` má konstantní složitost.

Existují tři typy kontejneru adaptéry standardní knihovny C++ definované: zásobníku, fronty a priority_queue. Každý omezuje funkci některé základní třídy kontejneru zajistit přesněji řízené rozhraní pro standardní datová struktura.

- [Stack – třída](../standard-library/stack-class.md) podporuje last-in ven (LIFO) datová struktura. Dobrý analogovým pamatovat by zásobník desky. Elementy (tabulky) může vložit, prověřovány nebo odebrat pouze z horní části zásobníku, který je posledním elementem na konci základní kontejneru. Omezení přístup pouze nejvyšší element je z důvodu pro použití třídy zásobníku.

- [Queue – třída](../standard-library/queue-class.md) podporuje first-in použity datová struktura. Dobrý analogovým pamatovat by zarovnání pro bankovní pokladnu osoby. Elementy (uživatelé) mohou být přidány do pozadí čáry a jsou odebrány z před řádku. Může být prověřovány přední a zadní straně řádku. Omezení přístup pouze přední a zadní prvky tímto způsobem je z důvodu pro použití třídy fronty.

- Priority_queue – třída řadí jeho prvky tak, aby největší element je vždy na nejvyšší pozici. Podporuje vkládání element a kontroly a odebrání nejvyšší elementu. Dobrý analogovým pamatovat by uživatelé zarovnávání, kde jsou uspořádané podle stáří, výšky nebo jiné kritérium.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[priority_queue](#priority_queue)|Vytvoří `priority_queue` který je prázdný nebo je kopie rozsah objektů základní kontejneru nebo jiné `priority_queue`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje základní kontejner, aby se přizpůsobit podle `priority_queue`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, která představuje počet elementů ve `priority_queue`.|
|[value_type](#value_type)|Typ, který reprezentuje typ objektu uložené jako element v `priority_queue`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[prázdný](#empty)|Pokud testy `priority_queue` je prázdný.|
|[POP](#pop)|Odebere největší elementu `priority_queue` z první pozici.|
|[push](#push)|Přidá element do fronty priority na základě priority element ze operátor <.|
|[Velikost](#size)|Vrátí počet prvků v `priority_queue`.|
|[Horní](#top)|Vrátí const odkaz na element největší v horní části `priority_queue`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fronty >

**Namespace:** – std

## <a name="container_type"></a>  priority_queue::container_type

Typ, který poskytuje základní kontejner, aby se přizpůsobit.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Container`. Kontejner – třída standardní knihovna C++ pořadí `deque` a výchozí třídu `vector` požadavkům má být použit jako základní kontejner pro objekt priority_queue. Uživatelem definované typy, které splňují požadavky mohou být využity také.

Další informace o `Container`, najdete v části poznámky [priority_queue – třída](../standard-library/priority-queue-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [priority_queue](#priority_queue) příklad toho, jak deklarace a používání `container_type`.

## <a name="empty"></a>  priority_queue::Empty

Testy, pokud priority_queue je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud priority_queue je prázdná. **false** Pokud je priority_queue neprázdný.

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

Odebere první pozici největší elementu priority_queue.

```cpp
void pop();
```

### <a name="remarks"></a>Poznámky

Priority_queue musí být neprázdný použít – členská funkce. Horní části priority_queue je vždy obsazena největší element v kontejneru.

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

Vytvoří priority_queue, který je prázdný nebo který je kopií rozsahu základní kontejnerového objektu nebo jiné priority_queue.

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

*_ comp* funkci porovnání typu **constTraits** sloužící k uspořádání elementy v priority_queue, výchozí nastavení je k porovnání funkce základní kontejneru.

`_Cont` Základní kontejner, který je vytvořený priority_queue být kopii.

`right` Priority_queue, které má být kopii sady vytvořený.

`first` Pozice první prvek v rozsahu elementy, které se mají zkopírovat.

`last` Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.

### <a name="remarks"></a>Poznámky

Každý z prvních tří konstruktorů určuje prázdný počáteční priority_queue druhý také určení typu funkce porovnání ( `comp`) pro použití při vytváření pořadí elementy a třetí explicitně zadáte `container_type`( `_Cont`) má být použit. Klíčové slovo **explicitní** potlačí určité druhy převod automatické typu.

Čtvrtý konstruktor určuje kopii priority_queue `right`.

Poslední tři konstruktory zkopírujte rozsahu [* první, poslední *) některé kontejneru a používají hodnoty k chybě při inicializaci priority_queue se zvýšeným explicitness v určení typu funkci porovnání třídy **vlastnosti** a `container_type`.

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

Přidá element do fronty priority na základě priority element ze operátor <.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Element přidán do horní části priority_queue.

### <a name="remarks"></a>Poznámky

Horní části priority_queue je pozice obsazena největší element v kontejneru.

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

Vrátí počet prvků priority_queue.

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

## <a name="size_type"></a>  priority_queue::size_type

Typ celé číslo bez znaménka, která představuje počet elementů ve priority_queue.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `size_type` základní kontejneru přizpůsobit pomocí priority_queue.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`.

## <a name="top"></a>  priority_queue::TOP

Vrátí const odkaz na element největší v horní části priority_queue.

```cpp
const_reference top() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na element největší určeného **vlastnosti** funkce, objekt priority_queue.

### <a name="remarks"></a>Poznámky

Priority_queue musí být neprázdný použít – členská funkce.

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

Typ, který představuje typ objektu uložené jako element v priority_queue.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `value_type` základní kontejneru přizpůsobit pomocí priority_queue.

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
