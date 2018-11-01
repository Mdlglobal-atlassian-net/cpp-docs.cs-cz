---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: 865524fe91b7d137e3a943973dcca6d833bd16df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471432"
---
# <a name="raise"></a>__raise

Zvýrazní stranu volání události.

## <a name="syntax"></a>Syntaxe

```
__raise method-declarator;
```

## <a name="remarks"></a>Poznámky

Ze spravovaného kódu lze událost vyvolat pouze ze třídy, ve které je definována. Zobrazit [události](../windows/event-cpp-component-extensions.md) Další informace.

Klíčové slovo **__raise** způsobí chybu, pokud zavoláte cokoli jiného než událost.

> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.

## <a name="example"></a>Příklad

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracování událostí](../cpp/event-handling.md)<br/>
[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)