---
title: Chyba kompilátoru C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 19b9c5a54bf405114bd4d596c2a2cc4708aadcc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507910"
---
# <a name="compiler-error-c2712"></a>Chyba kompilátoru C2712

> nelze použít __try ve funkcích, které vyžadovaly objekt vrácení zpět

## <a name="remarks"></a>Poznámky

Chyba C2712 může dojít, pokud používáte [/EHsc](../../build/reference/eh-exception-handling-model.md), a funkce se také zpracování strukturovaných výjimek má objektů, které vyžadují odvíjení (odstranění).

Možná řešení:

- Přesunout kód, který vyžaduje SEH do jiné funkce

- Přepisování funkcí, které používají SEH vyhnout se použití místních proměnných a parametry, které mají destruktory. Nepoužívejte SEH v konstruktory a destruktory

- Proveďte kompilaci bez/EHsc

Chyba C2712 může také dojít, pokud volání metody deklarované pomocí [__event](../../cpp/event.md) – klíčové slovo. Vzhledem k tomu, že událost může použít v prostředí s více vlákny, kompilátor generuje kód, který brání manipulaci s základního objektu události a poté uzavře generovaného kódu v SEH [try-finally – příkaz](../../cpp/try-finally-statement.md). V důsledku toho C2712 dojde k chybě Pokud zavoláte metodu události a předat hodnotu argument, jehož typ má destruktor. Předat argument jako konstantní odkaz v tomto případě je jedním z řešení.

C2712 může také dojít, pokud kompilujete s **/CLR: pure** a deklarujete statického pole ukazatelů na funkce v `__try` bloku. Statického člena, který vyžaduje, aby kompilátor používat dynamická inicializace v rámci **/CLR: pure**, což znamená zpracování výjimek jazyka C++. Nicméně zpracování výjimek jazyka C++ nepovoluje `__try` bloku.

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C2712 a ukazuje, jak ho opravit.

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```