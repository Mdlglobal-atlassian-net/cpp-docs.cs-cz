---
title: runtime_error – třída
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::runtime_error
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
ms.openlocfilehash: c4c4436c32f5f23c6bea119e95b165631384f583
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451124"
---
# <a name="runtimeerror-class"></a>runtime_error – třída

Třída slouží jako základní třída pro všechny výjimky vyvolané k ohlášení chyb, které jsou pravděpodobně zjišťovány pouze v případě, že je program proveden.

## <a name="syntax"></a>Syntaxe

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená třídou [Exception](../standard-library/exception-class.md) je kopií[dat](../standard-library/basic-string-class.md#data) **zprávy**`.`.

## <a name="example"></a>Příklad

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught bad locale name
Type class std::runtime_error
*/
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<stdexcept >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Exception – třída](../standard-library/exception-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
