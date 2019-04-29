---
title: out_of_range – třída
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::out_of_range
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
ms.openlocfilehash: 59d1a0dc987ddb0dc538fb02bfe28e0b073d3a7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370811"
---
# <a name="outofrange-class"></a>out_of_range – třída

Tato třída slouží jako základní třída pro všechny výjimky vyvolané argument, který je mimo platný rozsah hlášení.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_range : public logic_error {
public:
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená [co](../standard-library/exception-class.md) je kopie **zpráva**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Příklad

```cpp
// out_of_range.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

using namespace std;

int main() {
// out_of_range
   try {
      string str( "Micro" );
      string rstr( "soft" );
      str.append( rstr, 5, 3 );
      cout << str << endl;
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
   };
}
```

## <a name="output"></a>Výstup

```cpp
Caught: invalid string position
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<stdexcept – >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[logic_error – třída](../standard-library/logic-error-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
