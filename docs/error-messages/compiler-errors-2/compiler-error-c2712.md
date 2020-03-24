---
title: Chyba kompilátoru C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202303"
---
# <a name="compiler-error-c2712"></a>Chyba kompilátoru C2712

> nejde použít __try ve funkcích, které vyžadují zrušení objektu.

## <a name="remarks"></a>Poznámky

K chybě C2712 může dojít, pokud používáte [/EHsc](../../build/reference/eh-exception-handling-model.md)a funkce se strukturovaným zpracováním výjimek také obsahuje objekty, které vyžadují unwind (zničení).

Možná řešení:

- Přesunout kód, který vyžaduje SEH, do jiné funkce

- Přepište funkce, které používají SEH, abyste zabránili použití lokálních proměnných a parametrů, které mají destruktory. Nepoužívejte SEH v konstruktorech nebo destruktorech

- Kompilovat bez/EHsc

K chybě C2712 může dojít také v případě, že zavoláte metodu deklarovanou pomocí klíčového slova [__event](../../cpp/event.md) . Vzhledem k tomu, že událost může být použita v prostředí s více vlákny, kompilátor vygeneruje kód, který brání manipulaci s podkladovým objektem události, a poté uzavře generovaný kód do [příkazu try-finally](../../cpp/try-finally-statement.md)SEH. V důsledku toho dojde k chybě C2712, pokud zavoláte metodu události a předáte argument, jehož typ má destruktor. Jedním z řešení v tomto případě je předat argument jako konstantní odkaz.

K C2712 může také dojít, pokud kompilujete pomocí **/clr: Pure** a deklarujete statické pole ukazatelů na funkce v bloku `__try`. Statický člen vyžaduje, aby kompilátor používal dynamickou inicializaci v rámci **/clr: Pure**, který C++ zahrnuje zpracování výjimek. Zpracování C++ výjimek není však v bloku `__try` povoleno.

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C2712 a ukazuje, jak ji opravit.

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
