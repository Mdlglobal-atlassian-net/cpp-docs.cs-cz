---
title: '&lt;iterátor&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 69f1007f0c7f587e81313f5de97947410bf243df
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244026"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterátor&gt; funkce

## <a name="advance"></a> zálohy

Zvýší iterátor o zadaný počet pozic.

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>Parametry

*Inicializace*\
Iterátor, který má být zvýšen a který musí splňovat požadavky pro vstupní iterátor.

*Vypnout*\
Integrální typ, který lze převést na typ rozdílu iterátoru a určuje počet přírůstků pozice, o které má být iterátor zvýšen.

### <a name="remarks"></a>Poznámky

Procházený rozsah nesmí být singulární, pokud musí být iterátory přesměrovatelné nebo musí následovat za koncem.

Pokud `InputIterator` splňuje požadavky pro typ obousměrného iterátoru, pak *vypnout* může být záporná. Pokud `InputIterator` je typ vstupního nebo dopředného iterátoru, *vypnout* musí být nezáporná.

Funkce postoupení má konstantní složitost při `InputIterator` splňuje požadavky iterátor s náhodným přístupem; jinak má lineární složitost a je tak potenciálně náročná.

### <a name="example"></a>Příklad

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a> back_inserter –

Vytvoří iterátor, který může vložit prvky do zadní části zadaného kontejneru.

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontejner, do kterého má být zpracována zpětné vložení.

### <a name="return-value"></a>Návratová hodnota

A `back_insert_iterator` přidružená k objektu kontejneru *_Cont*.

### <a name="remarks"></a>Poznámky

V rámci standardní knihovny C++ argumentu musí odkazovat na jeden z kontejnerů tři pořadí, které mají členské funkce `push_back`: [třídou deque](../standard-library/deque-class.md), [list – třída](../standard-library/list-class.md), nebo [vektoru Třída](../standard-library/vector-class.md).

### <a name="example"></a>Příklad

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a> začít

Načte iterátor na první prvek v zadaném kontejneru.

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>Parametry

*pokračování*\
Kontejner.

*Pole*\
Pole objektů typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

První dvě funkce šablony vrátí `cont.begin()`. První funkce není konstantní, druhá je konstantní.

Třetí funkce šablony vrátí *pole*.

### <a name="example"></a>Příklad

Doporučujeme použít tuto funkci místě člena kontejneru `begin()` při obecnější chování je povinný.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

Funkce `reverse_sort` podporuje jakéhokoli druhu, mimo pravidelných polí také kontejnery, protože volá třetí verzi `begin()`. Pokud `reverse_sort` bylo kódováno k použití člena kontejneru `begin()`:

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

Pak zasláním pole způsobíte tuto chybu kompilátoru:

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a> cbegin

Načte konstantní iterátor na první prvek v zadaném kontejneru.

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>Parametry

*pokračování*\
Kontejner nebo seznam initializer_list.

### <a name="return-value"></a>Návratová hodnota

Konstanta `cont.begin()`.

### <a name="remarks"></a>Poznámky

Tato funkce funguje se všemi C++ kontejnery standardní knihovny a s [initializer_list](../standard-library/initializer-list-class.md).

Můžete použít tuto členskou funkci místo `begin()` šablona funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner nebo `initializer_list` jakéhokoli druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a> cend

Načte iterátor const na prvek, který následuje po posledním prvku v zadaném kontejneru.

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>Parametry

*pokračování*\
Kontejner nebo seznam initializer_list.

### <a name="return-value"></a>Návratová hodnota

Konstanta `cont.end()`.

### <a name="remarks"></a>Poznámky

Tato funkce funguje se všemi C++ kontejnery standardní knihovny a s [initializer_list](../standard-library/initializer-list-class.md).

Můžete použít tuto členskou funkci místo [end()](../standard-library/iterator-functions.md#end) šablona funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner nebo `initializer_list` jakéhokoli druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a> crbegin –

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a> crend –

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a> Data

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a> vzdálenost

Určuje počet kroků mezi polohami řešenými dvěma iterátory.

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Parametry

*první*\
První iterátor, který má být stanovena jehož vzdálenost od druhé.

*poslední*\
Druhý iterátor, jehož vzdálenost od první má být stanovena.

### <a name="return-value"></a>Návratová hodnota

Počet opakování, který *první* musí být zvýšena dokud rovná *poslední*.

### <a name="remarks"></a>Poznámky

Distance – funkce má konstantní složitost při `InputIterator` splňuje požadavky iterátor s náhodným přístupem; jinak má lineární složitost a je tak potenciálně náročná.

### <a name="example"></a>Příklad

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="empty"></a> prázdný

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a> ukončení

Načte iterátor na prvek, který následuje po posledním prvku v zadaném kontejneru.

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>Parametry

*pokračování*\
Kontejner.

*Pole*\
Pole objektů typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

První dvě funkce šablony vrátí `cont.end()` (první není a druhá je konstantní).

Třetí funkce šablony vrátí `array + Size`.

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [začít](../standard-library/iterator-functions.md#begin).

## <a name="front_inserter"></a> front_inserter

Vytvoří iterátor, který může vložit prvky do přední části zadaného kontejneru.

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Objekt kontejneru, jehož přední dochází k danému elementu vložen.

### <a name="return-value"></a>Návratová hodnota

A `front_insert_iterator` přidružená k objektu kontejneru *_Cont*.

### <a name="remarks"></a>Poznámky

Členská funkce [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator) z front_insert_iterator třídy mohou být využity také.

V rámci standardní knihovny C++ argumentu musí odkazovat na jeden z kontejnerů dvě pořadí, které mají členské funkce `push_back`: [třídou deque](../standard-library/deque-class.md) nebo "list – třída".

### <a name="example"></a>Příklad

```cpp
// iterator_front_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a> Vkládací modul

Pomocná funkce šablony, které vám umožní používat `inserter(_Cont, _Where)` místo `insert_iterator<Container>(_Cont, _Where)`.

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontejner, ke kterému jsou nové prvky mají být přidány.

*_Where*\
Iterátor vyhledání bodu vložení.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator)`<Container>(_Cont, _Where)`.

### <a name="example"></a>Příklad

```cpp
// iterator_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a> make_checked_array_iterator

Vytvoří [checked_array_iterator](../standard-library/checked-array-iterator-class.md) , který mohou používat ostatní algoritmy.

> [!NOTE]
> Tato funkce je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel na cílové pole.

*Velikost*\
Velikost cílového pole.

*Index*\
Volitelný index do pole.

### <a name="return-value"></a>Návratová hodnota

Instance `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

`make_checked_array_iterator` Funkce je definována v `stdext` oboru názvů.

Tato funkce příjme nezpracovaný ukazatel – což by normálně vyvolalo obavy o překročení hranic – a zabalí jej [checked_array_iterator](../standard-library/checked-array-iterator-class.md) třídu, která provádí kontrolu. Protože tato třída je označena jako kontrolovaná, standardní knihovny C++ ni nezobrazí upozornění. Další informace a příklady kódu naleznete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

V následujícím příkladu [vektoru](../standard-library/vector-class.md) je vytvořen a vyplní se 10 položkami. Obsah vektoru se zkopíruje do pole pomocí algoritmu kopírování a potom `make_checked_array_iterator` slouží k určení cíle. Následuje úmyslné porušení kontroly hranic, aby se spustilo selhání kontrolního výrazu ladění.

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a> make_move_iterator

Vytvoří `move iterator` obsahující zadaný iterátor jako `stored` iterátoru.

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>Parametry

*_It*\
Iterátor uložené v nové iterátorem pohybu.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `move_iterator` `<Iterator>(_It)`.

## <a name="make_unchecked_array_iterator"></a> make_unchecked_array_iterator

Vytvoří [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) , který mohou používat ostatní algoritmy.

> [!NOTE]
> Tato funkce je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel na cílové pole.

### <a name="return-value"></a>Návratová hodnota

Instance `unchecked_array_iterator`.

### <a name="remarks"></a>Poznámky

`make_unchecked_array_iterator` Funkce je definována v `stdext` oboru názvů.

Tato funkce příjme nezpracovaný ukazatel a zabalí jej do třídy, která neprovádí žádnou kontrolu a tedy na hodnotu nothing, ale neoptimalizuje upozornění kompilátoru jako [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Proto se jedná o cílený způsob řešení upozornění nekontrolovaného ukazatele bez jejich globálního umlčení nebo nákladů na kontrolu. Další informace a příklady kódu naleznete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

V následujícím příkladu [vektoru](../standard-library/vector-class.md) je vytvořen a vyplní se 10 položkami. Obsah vektoru se zkopíruje do pole pomocí algoritmu kopírování a potom `make_unchecked_array_iterator` slouží k určení cíle.

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a> Další

Iteruje zadaný počet iterací a vrátí novou pozici iterace.

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parametry

*první*\
Aktuální pozice.

*_Off*\
Počet pokusů pro iteraci.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici iterace po iterace *_Off* časy.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `next` zvýšena *_Off* časy

## <a name="prev"></a> předchozí

Iteruje v opačném pořadí zadaný počet iterací a vrátí novou pozici iterace.

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>Parametry

*první*\
Aktuální pozice.

*_Off*\
Počet pokusů pro iteraci.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `next` snížen `off` časy.

## <a name="rbegin"></a> rbegin –

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a> rend –

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a> Velikost

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```
