---
title: '&lt;nové&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: 6192805f0f427f86267a646b11d9f1d3365a1d57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716037"
---
# <a name="ltnewgt-functions"></a>&lt;nové&gt; funkce

|||
|-|-|
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|

## <a name="nothrow"></a>  nothrow

Poskytuje objekt pro použití jako argument **nothrow** verzích **nové** a **odstranit**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Poznámky

Tento objekt slouží jako argument funkce tak, aby odpovídaly typu parametru [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Příklad

V tématu [operátor new](../standard-library/new-operators.md#op_new) a [operátor new&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) příklady `std::nothrow_t` se používá jako parametr funkce.

## <a name="set_new_handler"></a>  set_new_handler

Nainstaluje funkci uživatele, který se má volat, pokud **operátor new** selže při jeho pokusu o přidělení paměti.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parametry

*Pnew*<br/>
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

## <a name="see-also"></a>Viz také:

[\<Nový >](../standard-library/new.md)<br/>
