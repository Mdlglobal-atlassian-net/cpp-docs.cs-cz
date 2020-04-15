---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: eb3ab24378071663b2a6a1abab700b81c3172419
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317225"
---
# <a name="__raise"></a>__raise

Zvýrazní stranu volání události.

## <a name="syntax"></a>Syntaxe

```
__raise method-declarator;
```

## <a name="remarks"></a>Poznámky

Ze spravovaného kódu lze událost vyvolat pouze ze třídy, ve které je definována. Další informace naleznete v [akci.](../extensions/event-cpp-component-extensions.md)

Klíčové slovo **__raise** způsobí, že chyba vyzařovat, pokud zavoláte non-event.

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

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

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracování událostí](../cpp/event-handling.md)<br/>
[Přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md)
