---
title: logic_error – třída
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::logic_error
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
ms.openlocfilehash: 9b7c432a649b566b455109f6de1f7bcc0734ff9b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453800"
---
# <a name="logicerror-class"></a>logic_error – třída

Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení chyb, které byly zjištěny před provedením programu, například porušení logických podmínek.

## <a name="syntax"></a>Syntaxe

```cpp
class logic_error : public exception {
public:
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená funkcí [co](../standard-library/exception-class.md) je kopie[dat](../standard-library/basic-string-class.md#data) **zprávy**`.`.

## <a name="example"></a>Příklad

```cpp
// logic_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;

int main( )
{
   try
   {
      throw logic_error( "logic error" );
   }
   catch ( exception &e )
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
```

```Output
Caught: logic error
Type: class std::logic_error
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<stdexcept >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Exception – třída](../standard-library/exception-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
