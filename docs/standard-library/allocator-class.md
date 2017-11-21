---
title: "Allocator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f298085fab156e8aecd0931dc72e358409a979d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="allocator-class"></a>allocator – třída
Šablony třídy popisuje objekt, který spravuje přidělení úložiště a uvolnění pro pole objektů typu **typu**. Třída objektu **allocator** je objekt allocator výchozí zadaný v konstruktorech pro několik tříd šablon kontejner ve standardní knihovně C++.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type>  
class allocator  
```  
  
#### <a name="parameters"></a>Parametry  
 *Typ*  
 Typ objektu, pro kterou se úložiště přidělené nebo navrácena.  
  
## <a name="remarks"></a>Poznámky  
 Všechny standardní knihovna C++ kontejnery mít parametr šablony, která jako výchozí **allocator**. Vytváření kontejneru s vlastní allocator poskytují kontrolu nad přidělení a uvolnění daného kontejneru elementů.  
  
 Například objekt allocator může přidělit úložiště na privátní haldy nebo ve sdílené paměti, nebo může optimalizovat pro malý nebo velký objekt velikosti. Ho může také určit, prostřednictvím definice typů, které poskytne, že elementy přistupovat prostřednictvím speciální přistupující objekty, které spravovat sdílené paměti nebo provádět automatické uvolňování paměti. Proto třídu, která přiděluje úložiště pomocí přidělujícího modulu objekt by měl používat tyto typy deklarace ukazatelů a odkazovaly na objekty, stejně jako kontejnery v standardní knihovna C++.  
  
 **(C_ ++ 98/03 pouze)** Pokud odvozujete od třídy allocator, je nutné zadat [rebind](#rebind) struktura, jejichž `_Other` typedef odkazuje na vaše nově odvozených tříd.  
  
 Proto přidělení definuje následující typy:  
  
- [ukazatel](#pointer) chová jako ukazatel na **typu**.  
  
- [const_pointer –](#const_pointer) chová jako const ukazatel na **typu**.  
  
- [referenční dokumentace](#reference) chová jako odkaz na **typu**.  
  
- [const_reference –](#const_reference) chová jako const odkaz na **typu**.  
  
 Tyto **typ**s zadejte formulář, který ukazatelů a odkazy, musíte provést pro přidělené elementy. ( [allocator::pointer](#pointer) není nutně stejné jako **typ** \* pro všechny objekty allocator, i když je tato zřejmé definice pro třídu **allocator**.)  
  
 **C ++ 11 a novější:** , aby operace přesunutí v vaší allocator, použijte rozhraní minimální allocator a implementaci kopírovacího konstruktoru, == a! = operátory, přidělte a navrátit. Další informace a příklady naleznete v tématu [Alokátorů](../standard-library/allocators.md)  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[Allocator](#allocator)|Konstruktory použít k vytvoření `allocator` objekty.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[const_pointer –](#const_pointer)|Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[const_reference –](#const_reference)|Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[difference_type –](#difference_type)|Integrální typ se znaménkem představující rozdíl mezi hodnotami ukazatelé na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[referenční dokumentace](#reference)|Typ, který obsahuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.|  
|[size_type –](#size_type)|Typu bez znaménka integrální, představující Délka libovolného pořadí, které objekt třídy šablony `allocator` můžete přidělit.|  
|[value_type](#value_type)|Typ, který je spravován pomocí přidělujícího modulu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Adresa](#address)|Vyhledá objekt, jehož hodnota je zadána adresa.|  
|[přidělit](#allocate)|Přiděluje blok paměti dostatečně velký pro uložení alespoň některé zadaný počet elementů.|  
|[konstrukce](#construct)|Vytvoří určitý typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
|[Destroy –](#destroy)|Volá destruktor objekty bez rušení přidělení paměti uloží objekt.|  
|[max_size –](#max_size)|Vrátí počet prvků typu `Type` které by mohly být přiděleny v objektu třídy `allocator` před použitím volné paměti.|  
|[rebind](#rebind)|Struktura, která umožňuje přidělení pro objekty jednoho typu se přidělit úložiště pro objekty jiného typu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#op_eq)|Přiřadí jeden `allocator` objektu na jiný `allocator` objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<paměti >  
  
 **Namespace:** – std  
  
##  <a name="address"></a>Allocator::Address  
 Vyhledá objekt, jehož hodnota je zadána adresa.  
  
```  
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Const nebo nonconst hodnota objektu, jejíž adresa se hledají.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnoty, respektive const nebo nonconst najít const nebo nonconst ukazatele na objekt.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátit adresu `val`, ve formuláři, který ukazatele musíte provést pro přidělené elementy.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="allocate"></a>Allocator::allocate  
 Přiděluje blok paměti dostatečně velký pro uložení alespoň některé zadaný počet elementů.  
  
```  
pointer allocate(size_type count, const void* _Hint);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Počet elementů, u kterých je přidělit dostatek místa.  
  
 *_Hint*  
 Const ukazatele, který může pomoct objekt allocator vyhovovaly žádosti o pro úložiště tím, že adresu objektu přidělené před žádosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na přidělené objekt nebo hodnota null, pokud nebyla přidělit paměť.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce přidělí úložiště pro pole počet elementů typu **typ**, pomocí volání new – operátor ( `count`). Vrací ukazatel na objekt přidělená. Pomocný parametr argument pomáhá některé alokátorů vylepšovat polohu odkaz; platná volba je adresa objektu dříve přidělena na stejný objekt allocator a ještě nebyla navrácena. Chcete-li zadat bez pomocného parametru, použijte argument ukazatele null.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="allocator"></a>Allocator::Allocator  
 Konstruktory slouží k vytvoření přidělování objektů.  
  
```  
allocator();
allocator(const allocator<Type>& right);
template <class Other>  
allocator(const allocator<Other>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Objekt allocator ke kopírování.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor neprovede žádnou akci. Obecně platí ale objekt allocator zkonstruován z jiného objektu allocator by měl porovnat rovná se a umožňují intermixing objekt přidělení a uvolnění mezi dvěma objekty allocator.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="const_pointer"></a>Allocator::const_pointer  
 Typ, který poskytuje konstantní ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```  
typedef const value_type *const_pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Je ukazatel typu popisuje objekt **ptr** , můžete určit, prostřednictvím výraz  **\*ptr**, libovolný const objekt, který můžete přidělit objekt allocator – třída šablony.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="const_reference"></a>Allocator::const_reference  
 Typ, který poskytuje konstantní odkaz na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```  
typedef const value_type& const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ odkazu popisuje objekt, který můžete určit všechny const objekt, který můžete přidělit objekt allocator – třída šablony.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="construct"></a>Allocator::Construct  
 Vytvoří určitý typ objektu na zadané adrese, který je inicializován se zadanou hodnotou.  
  
```  
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>  
void construct(pointer ptr, _Other&&...   val);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel na umístění, kde je objekt zkonstruovat.  
  
 `val`  
 Hodnota, pomocí kterého je objekt vytvářen inicializovat.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce je ekvivalentní volání **nové** (( `void` \*) `ptr` ) **typ** ( `val` ).  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="deallocate"></a>Allocator::deallocate  
 Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.  
  
```  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel na první objekt, který má být navrácena z úložiště.  
  
 `count`  
 Počet objektů, které chcete být navrácena z úložiště.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce uvolní úložiště pro pole počet objektů typu **typ** začínající na `ptr`, voláním `operator delete(ptr)`. Ukazatele `ptr` musí byly vráceny dříve voláním [přidělit](#allocate) allocator objektu, který porovnává rovna  **\*to**, přidělování objekt pole stejnou velikost a typ. `deallocate`nikdy vyvolá výjimku.  
  
### <a name="example"></a>Příklad  
  Příklad použití – členská funkce, naleznete v části [allocator::allocate](#allocate).  
  
##  <a name="destroy"></a>Allocator::Destroy  
 Volá destruktor objekty bez rušení přidělení paměti uloží objekt.  
  
```  
void destroy(pointer ptr);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel určení adresu objekt, který má být způsobem zničena.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce zničí objektu určeném `ptr`, při volání destruktoru `ptr->` **typ**::**~ typu**.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="difference_type"></a>Allocator::difference_type  
 Integrální typ se znaménkem představující rozdíl mezi hodnotami ukazatelé na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```  
typedef ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se znaménkem popisuje objekt, který může představovat rozdíl mezi adresy dvěma prvky v pořadí, které můžete přidělit objekt allocator – třída šablony.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="max_size"></a>Allocator::max_size  
 Vrátí počet prvků typu **typ** které by mohly být přiděleny v objektu allocator – třída před použitím volné paměti.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů, které by mohly být přiděleny.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="op_eq"></a>Allocator::Operator =  
 Jeden objekt allocator přiřadí k jinému objektu přidělení.  
  
```  
template <class Other>  
allocator<Type>& operator=(const allocator<Other>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Objekt allocator pro přiřazení do jiného takový objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt přidělování  
  
### <a name="remarks"></a>Poznámky  
 Operátor přiřazení šablony neprovede žádnou akci. Obecně platí ale objekt allocator přiřazen k jinému objektu allocator by měl porovnat rovná se a umožňují intermixing objekt přidělení a uvolnění mezi dvěma objekty allocator.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="pointer"></a>Allocator::Pointer  
 Typ, který poskytuje ukazatel na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```  
typedef value_type *pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Je ukazatel typu popisuje objekt **ptr** , můžete určit, prostřednictvím výraz  **\*ptr**, libovolný objekt, který můžete přidělit objekt allocator – třída šablony.  
  
### <a name="example"></a>Příklad  
  
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
  
   cout << "The original vector v1 is:\n ( " ;  
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
  
##  <a name="rebind"></a>Allocator::rebind  
 Struktura, která umožňuje přidělení pro objekty jednoho typu se přidělit úložiště pro objekty jiného typu.  
```  
struct rebind {    typedef allocator<_Other> other ;    };  
```  
### <a name="parameters"></a>Parametry  
 *Další*  
 Typ elementu, pro kterou se přidělí paměť.  
  
### <a name="remarks"></a>Poznámky  
 Tato struktura je užitečné pro přidělování paměti pro typ, který se liší od typu elementu objektu kontejneru se implementuje.  
  
 Šablony třídy člen definuje typ Další. Jejím jediným účelem je poskytnout název typu **allocator**\<_ **jiných**>, název typu **allocator** \< **typu** >.  
  
 Například zadaný objekt allocator **al** typu **A**, kterou můžete přidělit objekt typu **_Other** s výraz:  
  
```  
A::rebind<Other>::other(al).allocate(1, (Other *)0)  
```  
  
 Nebo můžete pojmenovat typ ukazatele napsáním typ:  
  
```  
A::rebind<Other>::other::pointer  
```  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="reference"></a>Allocator::Reference  
 Typ, který obsahuje odkaz na typ objektu spravovaného pomocí přidělujícího modulu.  
  
```  
typedef value_type& reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ odkazu popisuje objekt, který můžete určit libovolný objekt, který můžete přidělit objekt allocator – třída šablony.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="size_type"></a>Allocator::size_type  
 Nepodepsaných integrálních typ, který může představovat délka žádné pořadí, které můžete přidělit objekt allocator – třída šablony.  
  
```  
typedef size_t size_type;  
```  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="value_type"></a>Allocator::value_type  
 Typ, který je spravován pomocí přidělujícího modulu.  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **typu**.  
  
### <a name="example"></a>Příklad  
  
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
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

