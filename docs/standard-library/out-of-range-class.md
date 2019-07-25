---
title: out_of_range – třída
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::out_of_range
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
ms.openlocfilehash: 5f965e45e765f0c0cef6bc9cd8a175e2fdc50af7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453077"
---
# <a name="outofrange-class"></a>out_of_range – třída

Třída slouží jako základní třída pro všechny výjimky vyvolané pro hlášení argumentu, který je mimo platný rozsah.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_range : public logic_error {
public:
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená funkcí [co](../standard-library/exception-class.md) je kopie[dat](../standard-library/basic-string-class.md#data) **zprávy**`.`.

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

**Hlavička:** \<stdexcept >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[logic_error – třída](../standard-library/logic-error-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
