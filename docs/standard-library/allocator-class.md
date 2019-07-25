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
ms.openlocfilehash: 09c30eb58655113ef3daa8338829ad43b37bc415
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456410"
---
# <a name="allocator-class"></a>allocator – třída

Třída šablony popisuje objekt, který spravuje přidělování úložiště a uvolnění pro pole objektů typu `Type`. Objekt třídy `allocator` je výchozí objekt přidělování zadaný v konstruktorech pro několik tříd šablon kontejneru ve C++ standardní knihovně.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>Parametry

*Textový*\
Typ objektu, pro který je úložiště přiděleno nebo zrušeno.

## <a name="remarks"></a>Poznámky

Všechny C++ standardní kontejnery knihovny mají parametr šablony, který je výchozím nastavením `allocator`. Sestavování kontejneru s vlastním přidělováním poskytuje kontrolu nad přidělením a uvolněním prvků kontejneru.

Například objekt přidělování může přidělit úložiště na privátní haldě nebo ve sdílené paměti nebo může optimalizovat pro malé nebo velké velikosti objektů. Může také specifikovat, prostřednictvím definic typů, které poskytuje, k těmto prvkům přistupovat prostřednictvím speciálních přístupových objektů, které spravují sdílenou paměť, nebo provádět automatické uvolňování paměti. Proto třída, která přiděluje úložiště pomocí objektu Alokátor, by měla používat tyto typy pro deklaraci ukazatelů a referenčních objektů, jako kontejnery ve C++ standardní knihovně.

<strong>(Pouze C++ 98/03)</strong> Při odvozování od třídy přidělování je nutné zadat strukturu opětovné [vazby](#rebind) , jejíž `_Other` definice typedef odkazuje na vaši nově odvozenou třídu.

Proto Alokátor definuje následující typy:

- [ukazatel](#pointer) se chová jako ukazatel na `Type`.

- [const_pointer](#const_pointer) se chová jako ukazatel const na `Type`.

- [odkaz](#reference) se chová jako odkaz na `Type`.

- [const_reference](#const_reference) se chová jako odkaz const na `Type`.

Tyto `Type`typy s určují, které ukazatele a odkazy musí převzít pro přidělené elementy. ( [Alokátor::p ointer](#pointer) není nutně stejný jako `Type*` u všech objektů přidělování, i když má tuto zjevnou definici třídy `allocator`.)

**C++ 11 a novější:**  Chcete-li povolit operace přesunu ve vašem přidělování, použijte rozhraní minimálního přidělování a implementujte kopírovací konstruktor = = a! = Operators, allocate a unallocate. Další informace a příklad najdete v tématu [přidělování](../standard-library/allocators.md)

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[allocator](#allocator)|Konstruktory používané pro vytváření `allocator` objektů.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[const_pointer](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného přidělováním.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného přidělováním.|
|[difference_type](#difference_type)|Podepsaný integrální typ, který může představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného přidělováním.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného přidělováním.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na typ objektu spravovaného přidělováním.|
|[size_type](#size_type)|Celočíselný typ bez znaménka, který může představovat délku jakékoli sekvence, kterou může objekt třídy `allocator` šablony přidělit.|
|[value_type](#value_type)|Typ, který je spravován přidělováním.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[address](#address)|Najde adresu objektu, jehož hodnota je určena.|
|[allocate](#allocate)|Přidělí dostatečně velký blok paměti pro uložení alespoň některého zadaného počtu prvků.|
|[Contains](#construct)|Vytvoří konkrétní typ objektu na zadané adrese, která je inicializována se zadanou hodnotou.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|
|[způsobit](#destroy)|Volá destruktor objektů bez zrušení přidělení paměti, kde byl objekt uložen.|
|[max_size](#max_size)|Vrátí počet prvků typu `Type` , které mohou být přiděleny objektem třídy `allocator` před použitím volné paměti.|
|[Rebind](#rebind)|Struktura, která umožňuje Alokátor pro objekty jednoho typu přidělit úložiště pro objekty jiného typu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Přiřadí `allocator` jeden objekt k `allocator` jinému objektu.|

### <a name="address"></a>adresáře

Najde adresu objektu, jehož hodnota je určena.

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

#### <a name="parameters"></a>Parametry

*počítává*\
Hodnota konstanty nebo nepodílu objektu, jehož adresa je prohledávána.

#### <a name="return-value"></a>Návratová hodnota

Typ const nebo nepodílu na objektu nalezený, v uvedeném pořadí, konstanta nebo hodnota nenevýhody.

#### <a name="remarks"></a>Poznámky

Členské funkce vrátí adresu *Val*, ve tvaru, který ukazatelé musí přijmout pro přidělené prvky.

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

### <a name="allocate"></a>FISIM

Přidělí dostatečně velký blok paměti pro uložení alespoň některého zadaného počtu prvků.

```cpp
pointer allocate(size_type count, const void* _Hint);
```

#### <a name="parameters"></a>Parametry

*výpočtu*\
Počet prvků, pro které má být přiděleno dostatečné úložiště.

*_Hint*\
Ukazatel const, který může pomoci objektu přidělování, splnit požadavek na úložiště hledáním adresy objektu přiděleného před požadavkem.

#### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt nebo hodnotu null, pokud nebyla přidělena paměť.

#### <a name="remarks"></a>Poznámky

Členská funkce přiděluje úložiště pro pole počtu elementů typu `Type`, voláním operátoru new (*Count*). Vrátí ukazatel na přidělený objekt. Argument pomocného parametru pomáhá některým alokátorům zlepšit místní informace; platná volba je adresa objektu dříve přidělená stejným objektem přidělování a ještě není navrácená. Chcete-li zadat žádný pomocný parametr, použijte místo toho argument ukazatele s hodnotou null.

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

### <a name="allocator"></a>dělující

Konstruktory používané pro vytváření objektů přidělování

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
    allocator(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*\
Objekt přidělování, který se má zkopírovat

#### <a name="remarks"></a>Poznámky

Konstruktor neprovede žádnou akci. Obecně platí, že objekt přidělování vytvořený z jiného objektu přidělování by se měl porovnat se stejnou hodnotou a povolit vzájemné kombinování přidělování objektů a uvolnění mezi dvěma objekty přidělování.

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

### <a name="const_pointer"></a>const_pointer

Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného přidělováním.

```cpp
typedef const value_type *const_pointer;
```

#### <a name="remarks"></a>Poznámky

Typ ukazatele popisuje objekt `ptr` , který může být určen pomocí výrazu `*ptr`, libovolný objekt const, který objekt pro přidělování tříd šablon může přidělit.

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

### <a name="const_reference"></a>const_reference

Typ, který poskytuje konstantní odkaz na typ objektu spravovaného přidělováním.

```cpp
typedef const value_type& const_reference;
```

#### <a name="remarks"></a>Poznámky

Typ odkazu popisuje objekt, který může určit libovolný objekt const, který může přidělit objekt objektu pro přidělování tříd šablon.

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

### <a name="construct"></a>Contains

Vytvoří konkrétní typ objektu na zadané adrese, která je inicializována se zadanou hodnotou.

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
    void construct(pointer ptr, _Other&&... val);
```

#### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na umístění, kde má být objekt vytvořen.

*počítává*\
Hodnota, se kterou má být inicializován objekt vytvořen.

#### <a name="remarks"></a>Poznámky

První členská funkce je ekvivalentní typu **New** ((`void` \*) `ptr`) **Type** (`val`).

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

### <a name="deallocate"></a>uvolnit

Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.

```cpp
void deallocate(pointer ptr, size_type count);
```

#### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na první objekt, který má být vrácen z úložiště.

*výpočtu*\
Počet objektů, které se mají uvolnit z úložiště

#### <a name="remarks"></a>Poznámky

Členská funkce uvolní úložiště pro pole počtu objektů typu `Type` začínající na *PTR*, voláním. `operator delete(ptr)` Ukazatel *PTR* musí být vrácen dříve voláním pro [přidělení](#allocate) objektu alokace, který se rovná  **\*tomuto**, a přidělení objektu pole stejné velikosti a typu. `deallocate`nikdy nevyvolává výjimku.

#### <a name="example"></a>Příklad

Příklad použití členské funkce naleznete v tématu [přidělování:: allocate](#allocate).

### <a name="destroy"></a>způsobit

Volá destruktor objektů bez zrušení přidělení paměti, kde byl objekt uložen.

```cpp
void destroy(pointer ptr);
```

#### <a name="parameters"></a>Parametry

*střed*\
Ukazatel označující adresu objektu, který má být zničen.

#### <a name="remarks"></a>Poznámky

Členská funkce zničí objekt, který je určen *PTR*, voláním `ptr->` **typu**destruktoru:: **~ Type**.

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

### <a name="difference_type"></a>difference_type

Podepsaný integrální typ, který může představovat rozdíl mezi hodnotami ukazatelů na typ objektu spravovaného přidělováním.

```cpp
typedef ptrdiff_t difference_type;
```

#### <a name="remarks"></a>Poznámky

Typ signed integer popisuje objekt, který může představovat rozdíl mezi adresami všech dvou prvků v sekvenci, které může objekt pro přidělování tříd šablon přidělit.

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

### <a name="max_size"></a>max_size

Vrátí počet prvků typu `Type` , které mohou být přiděleny objektem Alokátor třídy před vyřazením volné paměti.

```cpp
size_type max_size() const;
```

#### <a name="return-value"></a>Návratová hodnota

Počet prvků, které mohou být přiděleny.

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

### <a name="op_eq"></a>operátor =

Přiřadí jeden objekt přidělování k jinému objektu přidělování.

```cpp
template <class Other>
    allocator<Type>& operator=(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*\
Objekt přidělování, který má být přiřazen k jinému takovému objektu.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt přidělování

#### <a name="remarks"></a>Poznámky

Operátor přiřazení šablony neprovádí žádnou akci. Obecně platí, že objekt přidělování přiřazený jinému objektu přidělování by se měl porovnat se stejnou hodnotou a povolit vzájemné kombinování přidělování objektů a uvolnění mezi dvěma objekty přidělování.

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

### <a name="pointer"></a>ukazatele

Typ, který poskytuje ukazatel na typ objektu spravovaného přidělováním.

```cpp
typedef value_type *pointer;
```

#### <a name="remarks"></a>Poznámky

Typ ukazatele popisuje objekt `ptr` , který lze určit pomocí výrazu  **\*PTR**, libovolný objekt, který může přidělit objekt objektu pro přidělování tříd šablon.

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

### <a name="rebind"></a>Rebind

Struktura, která umožňuje Alokátor pro objekty jednoho typu přidělit úložiště pro objekty jiného typu.

```cpp
struct rebind { typedef allocator<_Other> other; };
```

#### <a name="parameters"></a>Parametry

*jiná*\
Typ elementu, pro který je přidělena paměť.

#### <a name="remarks"></a>Poznámky

Tato struktura je užitečná pro přidělení paměti pro typ, který se liší od typu elementu implementovaného kontejneru.

Třída šablony člena definuje typ jiný. Jeho jediným účelem je poskytnout **Alokátor**\<názvu typu _ **jiné**>, s ohledem na **typ** **přidělování** \< názvu typu >.

Například s ohledem na objekt `al` Alokátor typu `A`můžete přidělit objekt typu `_Other` s výrazem:

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

Nebo můžete pojmenovat jeho typ ukazatele zápisem typu:

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

### <a name="reference"></a>odkaz

Typ, který poskytuje odkaz na typ objektu spravovaného přidělováním.

```cpp
typedef value_type& reference;
```

#### <a name="remarks"></a>Poznámky

Odkazový typ popisuje objekt, který může určit libovolný objekt, který může přidělit objekt objektu pro přidělování tříd šablon.

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

### <a name="size_type"></a>size_type

Celočíselný typ bez znaménka, který může představovat délku jakékoli sekvence, kterou může objekt přidělování tříd šablony přidělit.

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

### <a name="value_type"></a>value_type

Typ, který je spravován přidělováním.

```cpp
typedef Type value_type;
```

#### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `Type`šablony.

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

### <a name="allocator_arg_t"></a>allocator_arg_t

```cpp
struct allocator_arg_t { explicit allocator_arg_t() = default; };
inline constexpr allocator_arg_t allocator_arg{};
```

### <a name="uses_allocator"></a>uses_allocator

```cpp
template <class T, class Alloc> struct uses_allocator;
```
