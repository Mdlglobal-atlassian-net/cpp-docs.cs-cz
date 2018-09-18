---
title: Upozornění (úroveň 1) C4930 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4930
dev_langs:
- C++
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33c202cc6f062ac13bef3a73e4509e4ba870e2d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090188"
---
# <a name="compiler-warning-level-1-c4930"></a>Kompilátor upozornění (úroveň 1) C4930

'prototypu': nevolá se prototypovaná funkce se nevolala (byla definice proměnné záměrná?)

Kompilátor zjistil nepoužitou funkci prototypu. Pokud prototyp zamýšleno jako deklaraci proměnné, odeberte závorky otevřít nebo zavřít.

Následující ukázka generuje C4930:

```
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930 může dojít také při kompilátor nelze rozlišit mezi deklarace prototypu funkce a volání funkce.

Následující ukázka generuje C4930:

```
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

V ukázce výše výsledek metody, která nepřijímá žádné argumenty je předán jako argument konstruktoru Nepojmenovaná třída místní proměnné. Volání můžete jednoznačně rozlišit názvy v místní proměnné nebo předpony volání metody s instancí objektu společně s odpovídající operátor pointer-to-member.