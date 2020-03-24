---
title: Upozornění kompilátoru (úroveň 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 6c012e484bddeb204601265f9d56efb7bbee7e96
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199313"
---
# <a name="compiler-warning-level-1-c4930"></a>Upozornění kompilátoru (úroveň 1) C4930

' prototyp ': nebyla volána prototypovaná funkce (byla určena definice proměnné?)

Kompilátor zjistil nepoužitý prototyp funkce. Pokud prototyp byl zamýšlen jako deklarace proměnné, odeberte závorky Open/Close.

Následující ukázka generuje C4930:

```cpp
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

K C4930 může dojít také v případě, že kompilátor nemůže rozlišovat mezi deklarací prototypu funkce a voláním funkce.

Následující ukázka generuje C4930:

```cpp
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

Ve výše uvedeném příkladu je výsledek metody, která přijímá nula argumentů, předán jako argument konstruktoru nepojmenované lokální proměnné třídy. Volání může být nejednoznačná buď pojmenováním místní proměnné, nebo prefixem volání metody s instancí objektu spolu s odpovídajícím operátorem pointer-to-member.
