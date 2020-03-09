---
title: '&lt;nové funkce&gt;'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854930"
---
# <a name="ltnewgt-functions"></a>&lt;nové funkce&gt;

## <a name="get_new_handler"></a>get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Poznámky

Vrátí aktuální `new_handler`.

## <a name="launder"></a>peníze

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parametry

\ *PTR*
Adresa bajtu v paměti, který obsahuje objekt, jehož typ je podobný *T*.

### <a name="return-value"></a>Návratová hodnota

Hodnota typu *T\** , která odkazuje na X.

### <a name="remarks"></a>Poznámky

Také se označuje jako bariéra optimalizace ukazatele.

Používá se jako konstantní výraz, pokud se hodnota jeho argumentu dá použít v konstantním výrazu. Bajt úložiště je dosažitelný prostřednictvím hodnoty ukazatele, která odkazuje na objekt, pokud v úložišti obsazeném jiným objektem objekt s podobným ukazatelem.

### <a name="example"></a>Příklad

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a>nothrow

Poskytuje objekt, který má být použit jako argument pro verze **nového** a **odstranění**ve verzi **throw** .

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Poznámky

Objekt se používá jako argument funkce, aby odpovídal typu parametru [std:: nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Příklad

Příklady použití `std::nothrow_t` jako parametru funkce naleznete v tématu [operator new](../standard-library/new-operators.md#op_new) a [operator new&#91; ](../standard-library/new-operators.md#op_new_arr) .

## <a name="set_new_handler"></a>set_new_handler

Nainstaluje uživatelskou funkci, která se má volat, když se **operátor New** v pokusu o přidělení paměti nezdařil.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parametry

*Pnew*\
`new_handler` k instalaci.

### <a name="return-value"></a>Návratová hodnota

0 při prvním volání a předchozí `new_handler` při následném volání.

### <a name="remarks"></a>Poznámky

Funkce ukládá *Pnew* do statického ukazatele [obslužných rutin](../standard-library/new-typedefs.md#new_handler) , které udržuje, a potom vrátí hodnotu, která byla dříve uložena v ukazateli. Novou obslužnou rutinu používá [operátor New](../standard-library/new-operators.md#op_new)(**size_t**).

### <a name="example"></a>Příklad

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
