---
title: invalid_argument – třída
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::invalid_argument
helpviewer_keywords:
- invalid_argument class
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
ms.openlocfilehash: 1c5caa0129730750a6429d9f7fa883e9af30f225
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449264"
---
# <a name="invalidargument-class"></a>invalid_argument – třída

Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení neplatného argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_argument : public logic_error {
public:
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená funkcí [co](../standard-library/exception-class.md) je kopie[dat](../standard-library/basic-string-class.md#data) **zprávy**`.`.

## <a name="example"></a>Příklad

```cpp
// invalid_arg.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 32 > bitset( string( "11001010101100001b100101010110000") );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught invalid bitset<N> char
Type class std::invalid_argument
*/
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<stdexcept >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[logic_error – třída](../standard-library/logic-error-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
