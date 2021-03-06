---
title: bad_typeid – výjimka
ms.date: 10/04/2019
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: bb56de77ba001b5a511ef3a2695d18109b1ed3ca
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245918"
---
# <a name="bad_typeid-exception"></a>bad_typeid – výjimka

Výjimka **bad_typeid** je vyvolána [operátorem typeid](../cpp/typeid-operator.md) , pokud operand pro **typeid** je ukazatel s hodnotou null.

## <a name="syntax"></a>Syntaxe

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>Poznámky

Rozhraní pro **bad_typeid** :

```cpp
class bad_typeid : public exception
{
public:
   bad_typeid();
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();

   bad_typeid& operator=(const bad_typeid&);
   const char* what() const;
};
```

Následující příklad ukazuje, že operátor **typeid** vyvolává výjimku **bad_typeid** .

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class A{
public:
   // object for class needs vtable
   // for RTTI
   virtual ~A();
};

using namespace std;
int main() {
A* a = NULL;

try {
   cout << typeid(*a).name() << endl;  // Error condition
   }
catch (bad_typeid){
   cout << "Object is NULL" << endl;
   }
}
```

## <a name="output"></a>Výstup

```Output
Object is NULL
```

## <a name="see-also"></a>Viz také:

\ [informace o typu](../cpp/run-time-type-information.md) běhu
[Klíčová slova](../cpp/keywords-cpp.md)
