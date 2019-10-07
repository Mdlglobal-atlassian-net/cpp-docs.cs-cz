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
ms.openlocfilehash: 6410f27342ed40300ff236ee1c47ada740255f84
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998804"
---
# <a name="bad_typeid-exception"></a>bad_typeid – výjimka

Výjimka **bad_typeid** je vyvolána [operátorem typeid](../cpp/typeid-operator.md) , pokud operand pro **identifikátor TypeId** je ukazatel s hodnotou null.

## <a name="syntax"></a>Syntaxe

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>Poznámky

Rozhraní pro **bad_typeid** je:

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

[Informace o typu běhového](../cpp/run-time-type-information.md)běhu \
[Klíčová slova](../cpp/keywords-cpp.md)
