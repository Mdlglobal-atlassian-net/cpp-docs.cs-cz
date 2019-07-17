---
title: allocator – třída
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator
- memory/std::allocator::const_pointer
- memory/std::allocator::const_reference
- memory/std::allocator::difference_type
- memory/std::allocator::pointer
- memory/std::allocator::reference
- memory/std::allocator::size_type
- memory/std::allocator::value_type
- memory/std::allocator::address
- memory/std::allocator::allocate
- memory/std::allocator::construct
- memory/std::allocator::deallocate
- memory/std::allocator::destroy
- memory/std::allocator::max_size
- memory/std::allocator::rebind
helpviewer_keywords:
- std::allocator [C++]
- std::allocator [C++], const_pointer
- std::allocator [C++], const_reference
- std::allocator [C++], difference_type
- std::allocator [C++], pointer
- std::allocator [C++], reference
- std::allocator [C++], size_type
- std::allocator [C++], value_type
- std::allocator [C++], address
- std::allocator [C++], allocate
- std::allocator [C++], construct
- std::allocator [C++], deallocate
- std::allocator [C++], destroy
- std::allocator [C++], max_size
- std::allocator [C++], rebind
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
ms.openlocfilehash: 1a0c8a04dda6c396b4f56d0939838fb6cb8e7455
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245929"
---
# <a name="allocator-class"></a>allocator – třída

Třída šablony popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro pole objektů typu `Type`. Objekt třídy `allocator` je výchozí objekt alokátoru podle konstruktory pro třídy šablony několik kontejnerů ve standardní knihovně jazyka C++.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ objektu, pro který se ještě úložiště přidělené nebo uvolnit.

## <a name="remarks"></a>Poznámky

Všechny kontejnery standardní knihovny C++ mají parametr šablony, která jako výchozí `allocator`. Vytváření kontejneru pomocí vlastního alokátoru poskytují kontrolu nad přidělování a uvolňování prvků tohoto kontejneru.

Například objekt alokátoru může přidělit úložiště na privátní haldy nebo ve sdílené paměti, nebo může optimalizovat pro objekt malé nebo velké velikosti. To může také určit, prostřednictvím definice typu, který poskytne, aby prvky přístupná prostřednictvím speciální přistupující objekty, které spravovat sdílené paměti nebo provést automatické uvolňování paměti. Třídu, která přiděluje úložiště pomocí objekt alokátoru proto by měl používat tyto typy deklarace ukazatele a odkazovat na objekty, stejně jako kontejnery ve standardní knihovně C++.

<strong>(C ++ 98/03 jenom)</strong>  Pokud odvozujete od třídy allocator, je nutné zadat [rebind](#rebind) – struktura, jejíž `_Other` definice typu odkazuje na vaše nově odvozených tříd.

Díky tomu se přidělování definuje následující typy:

- [ukazatel](#pointer) se chová jako ukazatel na `Type`.

- [const_pointer](#const_pointer) se chová jako konstantní ukazatel na `Type`.

- [referenční dokumentace](#reference) se chová jako odkaz na `Type`.

- [const_reference](#const_reference) se chová jako konstantní odkaz na `Type`.

Tyto `Type`s zadejte formulář, který ukazatele a reference musí přijmout přidělené elementů. ( [allocator::pointer](#pointer) není nutně stejné jako `Type*` pro všechny objekty přidělování, i když má tato zřejmé definice pro třídu `allocator`.)

**C ++ 11 a novější:**  Povolení operací přesunu ve vašich allocator, použijte rozhraní minimálních alokátorů a implementovat kopírovací konstuktor, == a! = operátory, přidělit a uvolnit. Další informace a příklad najdete v tématu [Alokátorů](../standard-library/allocators.md)

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[allocator](#allocator)|Umožňuje vytvořit konstruktory `allocator` objekty.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[const_pointer](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, které mohou představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného pomocí přidělujícího modulu.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|
|[size_type](#size_type)|Bez znaménka celočíselného typu, který může představovat Délka libovolného pořadí, které objekt třídy šablony `allocator` můžete přidělit.|
|[value_type](#value_type)|Typ, který je spravovaný nástrojem přidělujícího modulu.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[address](#address)|Vyhledá adresu objektu, jehož hodnota je určena.|
|[allocate](#allocate)|Přiděluje blok paměti dostatečně velký pro uložení alespoň nějaké zadaný počet prvků.|
|[Konstrukce](#construct)|Vytvoří konkrétní typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|
|[zrušení](#destroy)|Volá destruktor objekty bez rušení přidělení paměti uložení objektu.|
|[max_size](#max_size)|Vrátí počet prvků typu `Type` , které by mohly být přiděleny objektem třídy `allocator` předtím, než se využilo volné paměti.|
|[obnovení vazby](#rebind)|Struktura, která umožňuje alokátoru pro objekty jednoho typu pro přidělení úložiště pro objekty jiného typu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Přiřadí jednu `allocator` objektu na jiný `allocator` objektu.|

### <a name="address"></a> Adresa

Vyhledá adresu objektu, jehož hodnota je určena.

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

#### <a name="parameters"></a>Parametry

*Val*\
Const nebo nonconst hodnotu objektu, jehož adresu má být vyhledán pro.

#### <a name="return-value"></a>Návratová hodnota

Najít hodnoty, resp. const nebo nonconst konstantní nebo nonconst ukazatel na objekt.

#### <a name="remarks"></a>Poznámky

Členské funkce vrátí adresu *val*ve formuláři, který ukazatele musíte provést pro přidělené elementy.

#### <a name="example"></a>Příklad

```cpp
// allocator_address.cpp
// compile with: /EHsc
#include <memory>
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 8;
   v1Ptr = v1Alloc.address( *find(v1.begin( ), v1.end( ), k) );
   // v1Ptr = v1Alloc.address( k );
   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 8.
```

### <a name="allocate"></a> přidělení

Přiděluje blok paměti dostatečně velký pro uložení alespoň nějaké zadaný počet prvků.

```cpp
pointer allocate(size_type count, const void* _Hint);
```

#### <a name="parameters"></a>Parametry

*Počet*\
Počet elementů, u kterých má být přidělené dostatečné úložiště.

*_Hint*\
Konstantní ukazatel, který vám mohou pomoci objekt alokátoru, který vyhověli žádosti pro úložiště vyhledáním adresu objektu přidělena před požadavku.

#### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt nebo hodnota null, pokud nebyla přidělena paměť.

#### <a name="remarks"></a>Poznámky

Členská funkce alokují prostor pro pole count prvků typu `Type`, podle volání new – operátor (*počet*). Vrací ukazatel na přidělený objekt. Pomocný parametr argument pomáhá zlepšit místo odkazu; některé alokátorů platná volba je adresu objektu dříve přidělenou na stejný objekt alokátoru a ještě nebyla uvolněna. Slouží k poskytování žádné pomocný parametr, použijte argument ukazatele s hodnotou null.

#### <a name="example"></a>Příklad

```cpp
// allocator_allocate.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<int> v1Alloc;
   allocator<int>::pointer v1aPtr;
   v1aPtr = v1Alloc.allocate ( 10 );

   int i;
   for ( i = 0 ; i < 10 ; i++ )
   {
      v1aPtr[ i ] = i;
   }

   for ( i = 0 ; i < 10 ; i++ )
   {
      cout << v1aPtr[ i ] << " ";
   }
   cout << endl;
   v1Alloc.deallocate( v1aPtr, 10 );
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="allocator"></a> Allocator –

Konstruktory, které slouží k vytvoření objektů alokátoru.

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
    allocator(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parametry

*doprava*\
Objekt alokátoru, který má být zkopírován.

#### <a name="remarks"></a>Poznámky

Konstruktor nemá žádný účinek. Obecně platí ale objekt alokátoru, který je vytvořen z jiného objektu allocator by měl porovnávají se stejně k němu a povolit intermixing objekt přidělení a uvolnění mezi dvěma objekty alokátoru.

#### <a name="example"></a>Příklad

```cpp
// allocator_allocator.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int( int i )
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<double> Alloc;
   vector <Int>:: allocator_type v1Alloc;

   allocator<double> cAlloc(Alloc);
   allocator<Int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="const_pointer"></a> const_pointer

Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef const value_type *const_pointer;
```

#### <a name="remarks"></a>Poznámky

Typ ukazatele, který popisuje objekt `ptr` , které můžete určit, pomocí výrazu `*ptr`, libovolný objekt const, můžete přidělit objekt alokátoru třídy šablony.

#### <a name="example"></a>Příklad

```cpp
// allocator_const_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 10;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer's address found has a value of: "
        << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer's address found has a value of: 10.
```

### <a name="const_reference"></a> const_reference

Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef const value_type& const_reference;
```

#### <a name="remarks"></a>Poznámky

Typ odkazu, který popisuje objekt, který můžete určit všechny konstantní objekt, který můžete přidělit objekt alokátoru třídy šablony.

#### <a name="example"></a>Příklad

```cpp
// allocator_const_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::const_reference vcref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vcref << ",\n the first element in the vector." << endl;

   // const references can have their elements modified,
   // so the following would generate an error:
   // vcref = 150;
   // but the value of the first element could be modified through
   // its nonconst iterator and the const reference would remain valid
*vfIter = 175;
   cout << "The value of the element referred to by vcref,"
        <<"\n after nofication through its nonconst iterator, is: "
        << vcref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The value of the element referred to by vcref,
after nofication through its nonconst iterator, is: 175.
```

### <a name="construct"></a> Konstrukce

Vytvoří konkrétní typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
    void construct(pointer ptr, _Other&&... val);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel na umístění, kde má být vytvořen objekt.

*Val*\
Hodnota, pomocí kterého je inicializovat objekt vytváří.

#### <a name="remarks"></a>Poznámky

První členská funkce je ekvivalentní **nové** ((`void` \*) `ptr`) **typ** (`val`).

#### <a name="example"></a>Příklad

```cpp
// allocator_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 6, kB = 7;
   v1PtrA = v1Alloc.address( *find( v1.begin( ), v1.end( ), kA ) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The modified vector v1 is:
( 3 7 9 12 15 18 21 ).
```

### <a name="deallocate"></a> zrušit přidělení

Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.

```cpp
void deallocate(pointer ptr, size_type count);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel na první objekt k zrušeno přidělení úložiště.

*Počet*\
Počet objektů pro zrušeno přidělení úložiště.

#### <a name="remarks"></a>Poznámky

Členská funkce uvolňuje úložiště pro počet objektů typu pole `Type` počínaje *ptr*, voláním `operator delete(ptr)`. Ukazatel *ptr* musí vrácení dříve voláním [přidělit](#allocate) pro objekt alokátoru, který při porovnání rovna  **\*to**, přidělení matici objekt stejné velikosti a typu. `deallocate` nikdy nevyvolá výjimku.

#### <a name="example"></a>Příklad

Příklad použití členská funkce, najdete v části [allocator::allocate](#allocate).

### <a name="destroy"></a> zrušení

Volá destruktor objekty bez rušení přidělení paměti uložení objektu.

```cpp
void destroy(pointer ptr);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel s vyznačením adresu objektu, který se má zničit.

#### <a name="remarks"></a>Poznámky

Členská funkce odstraní objektu určeném *ptr*, voláním destruktoru `ptr->` **typ**:: **~ typ**.

#### <a name="example"></a>Příklad

```cpp
// allocator_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 12, kB = -99;
   v1PtrA = v1Alloc.address( *find(v1.begin( ), v1.end( ), kA) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The modified vector v1 is:
( 2 4 6 8 10 -99 14 ).
```

### <a name="difference_type"></a> difference_type

Celočíselný typ se znaménkem, které mohou představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef ptrdiff_t difference_type;
```

#### <a name="remarks"></a>Poznámky

Typ celé číslo se znaménkem, který popisuje objekt, který může představovat rozdíl mezi adresami jakékoli dva prvky v sekvenci, která může přidělit objekt alokátoru třídy šablony.

#### <a name="example"></a>Příklad

```cpp
// allocator_diff_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 0 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1PtrA, v1PtrB;
   const int kA = 4, kB =12;
   v1PtrA = v1Alloc.address( kA );
   v1PtrB = v1Alloc.address( kB );
   allocator<int>::difference_type v1diff = *v1PtrB - *v1PtrA;

   cout << "Pointer v1PtrA addresses " << *v1PtrA << "." << endl;
   cout << "Pointer v1PtrB addresses " << *v1PtrB <<  "." << endl;
   cout << "The difference between the integer's addresses is: "
        << v1diff << "." << endl;
}
```

```Output
The original vector v1 is:
( 0 2 4 6 8 10 12 14 ).
Pointer v1PtrA addresses 4.
Pointer v1PtrB addresses 12.
The difference between the integer's addresses is: 8.
```

### <a name="max_size"></a> max_size

Vrátí počet prvků typu `Type` , které by mohly být přiděleny v objektu alokátoru třídy předtím, než se využilo volné paměti.

```cpp
size_type max_size() const;
```

#### <a name="return-value"></a>Návratová hodnota

Počet prvků, které by mohly být přiděleny.

#### <a name="example"></a>Příklad

```cpp
// allocator_max_size.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   vector <double> v2;
   vector <double> ::iterator v2Iter;
   vector <double> :: allocator_type v2Alloc;
   allocator<int>::size_type v1size;
   v1size = v1Alloc.max_size( );

   cout << "The number of integers that can be allocated before\n"
        << " the free memory in the vector v1 is used up is: "
        << v1size << "." << endl;

   int ii;
   for ( ii = 1 ; ii <= 7 ; ii++ )
   {
      v2.push_back( ii * 10.0 );
   }

   cout << "The original vector v2 is:\n ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ; v2Iter++ )
      cout << *v2Iter << " ";
   cout << ")." << endl;
   allocator<double>::size_type v2size;
   v2size = v2Alloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v2 is used up is: "
        << v2size << "." << endl;
}
```

### <a name="op_eq"></a> operátor =

Přiřadí jeden objekt přidělování na jiný objekt alokátoru.

```cpp
template <class Other>
    allocator<Type>& operator=(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parametry

*doprava*\
Objekt alokátoru pro přiřazení jiného takový objekt.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt alokátoru, který

#### <a name="remarks"></a>Poznámky

Operátor přiřazení šablony nemá žádný účinek. Obecně platí ale objekt alokátoru, který je přiřazen k jinému objektu allocator by měl porovnávají se stejně k němu a povolit intermixing objekt přidělení a uvolnění mezi dvěma objekty alokátoru.

#### <a name="example"></a>Příklad

```cpp
// allocator_op_assign.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( ) {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<Int> Alloc;
   allocator<Int> cAlloc ;
   cAlloc = Alloc;
}
```

### <a name="pointer"></a> Ukazatel

Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef value_type *pointer;
```

#### <a name="remarks"></a>Poznámky

Typ ukazatele, který popisuje objekt `ptr` , které můžete určit, pomocí výrazu  **\*ptr**, libovolný objekt, který můžete přidělit objekt alokátoru třídy šablony.

#### <a name="example"></a>Příklad

```cpp
// allocator_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 12;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 12.
```

### <a name="rebind"></a> obnovení vazby

Struktura, která umožňuje alokátoru pro objekty jednoho typu pro přidělení úložiště pro objekty jiného typu.

```cpp
struct rebind { typedef allocator<_Other> other; };
```

#### <a name="parameters"></a>Parametry

*Ostatní*\
Typ prvku, pro kterou je přidělena paměť.

#### <a name="remarks"></a>Poznámky

Tato struktura je užitečné pro přidělení paměti pro typ, který se liší od typu elementu kontejneru se implementuje.

Člen šablony třídy definuje typ jiné. Jejím jediným účelem je poskytnout název typu **alokátoru**\<_ **jiných**>, název typu **alokátoru** \< **typu** >.

Mějme například objekt alokátoru `al` typu `A`, kterou můžete přidělit objekt typu `_Other` s výrazem:

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

Nebo můžete pojmenovat jeho typ ukazatele napsáním typ:

```cpp
A::rebind<Other>::other::pointer
```

#### <a name="example"></a>Příklad

```cpp
// allocator_rebind.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

typedef vector<int>::allocator_type IntAlloc;
int main( )
{
   IntAlloc v1Iter;
   vector<int> v1;

   IntAlloc::rebind<char>::other::pointer pszC =
      IntAlloc::rebind<char>::other(v1.get_allocator()).allocate(1, (void *)0);

   int * pInt = v1Iter.allocate(10);
}
```

### <a name="reference"></a> Referenční dokumentace

Typ, který poskytuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.

```cpp
typedef value_type& reference;
```

#### <a name="remarks"></a>Poznámky

Typ odkazu, který popisuje objekt, který můžete určit libovolný objekt, který můžete přidělit objekt alokátoru třídy šablony.

#### <a name="example"></a>Příklad

```cpp
// allocator_reference.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::reference vref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vref << ",\n the first element in the vector." << endl;

   // nonconst references can have their elements modified
   vref = 150;
   cout << "The element referred to by vref after being modified is: "
        << vref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The element referred to by vref after being modified is: 150.
```

### <a name="size_type"></a> size_type

Celočíselný typ bez znaménka představující délku jakékoli sekvenci, která může přidělit objekt alokátoru třídy šablony.

```cpp
typedef size_t size_type;
```

#### <a name="example"></a>Příklad

```cpp
// allocator_size_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   allocator<double>::size_type vsize;
   vsize = vAlloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v is used up is: "
        << vsize << "." << endl;
}
```

### <a name="value_type"></a> value_type

Typ, který je spravovaný nástrojem přidělujícího modulu.

```cpp
typedef Type value_type;
```

#### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Type`.

#### <a name="example"></a>Příklad

```cpp
// allocator_value_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::value_type vecVal = 150.0;
*vfIter = vecVal;
   cout << "The value of the element addressed by vfIter is: "
        << *vfIter << ",\n the first element in the vector." << endl;

   cout << "The modified vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element addressed by vfIter is: 150,
the first element in the vector.
The modified vector v is:
( 150 200 300 400 500 600 700 ).
```

## <a name="helpers"></a>Pomocné rutiny

### <a name="allocator_arg_t"></a> allocator_arg_t

```cpp
struct allocator_arg_t { explicit allocator_arg_t() = default; };
inline constexpr allocator_arg_t allocator_arg{};
```

### <a name="uses_allocator"></a> uses_allocator –

```cpp
template <class T, class Alloc> struct uses_allocator;
```
