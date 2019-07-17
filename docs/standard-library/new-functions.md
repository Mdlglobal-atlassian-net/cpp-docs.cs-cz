---
title: '&lt;nové&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243666"
---
# <a name="ltnewgt-functions"></a>&lt;nové&gt; funkce

## <a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Poznámky

Vrátí aktuální `new_handler`.

## <a name="launder"></a> praní

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parametry

*PTR*\
Adresa bajtů v paměti, která obsahuje objekt, jehož typ je podobný *T*.

### <a name="return-value"></a>Návratová hodnota

Hodnotu typu *T\**  , která odkazuje na X.

### <a name="remarks"></a>Poznámky

Také označuje jako překážku optimalizace ukazatele.

Při jako konstantní výraz hodnotu svého argumentu, může být použita v konstantním výrazu. Bajtů úložiště je dostupný prostřednictvím hodnotu ukazatele, který odkazuje na objekt, pokud v rámci úložiště obsazena jiným objektem, objekt se podobně jako ukazatel.

### <a name="example"></a>Příklad

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a> nothrow

Poskytuje objekt pro použití jako argument **nothrow** verzích **nové** a **odstranit**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Poznámky

Tento objekt slouží jako argument funkce tak, aby odpovídaly typu parametru [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Příklad

V tématu [operátor new](../standard-library/new-operators.md#op_new) a [operátor new&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) příklady `std::nothrow_t` se používá jako parametr funkce.

## <a name="set_new_handler"></a> set_new_handler

Nainstaluje funkci uživatele, který se má volat, pokud **operátor new** selže při jeho pokusu o přidělení paměti.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parametry

*Pnew*\
`new_handler` k instalaci.

### <a name="return-value"></a>Návratová hodnota

0 na první volání a předchozí `new_handler` při dalších volání.

### <a name="remarks"></a>Poznámky

Funkce úložiště *Pnew* v statickou [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler) ukazatel, který uchovává, vrátí hodnotu dříve uloženou v ukazateli. Používá novou obslužnou rutinu [operátor new](../standard-library/new-operators.md#op_new)(**size_t**).

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
