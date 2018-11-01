---
title: Upozornění kompilátoru C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: 00c9e139e920473590389c05f076a7cd91a4fb8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548847"
---
# <a name="compiler-warning-c4394"></a>Upozornění kompilátoru C4394

'function': symbol na úrovni appdomain nemůže být označena jako pomocí deklarace __declspec(dllexport)

Funkce označené [appdomain](../../cpp/appdomain.md) `__declspec` Modifikátor je kompilováno do jazyka MSIL (ne na nativní) a export tabulek ([exportovat](../../windows/export.md) `__declspec` modifikátor) nejsou podporovány pro spravované funkce.

Je možné deklarovat spravované funkce mít přístupnost public. Další informace najdete v tématu [zadejte viditelnost](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [viditelnost členu](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 je vždy vyvoláno jako chyba.  Můžete vypnout toto upozornění se `#pragma warning` nebo **/wd**; naleznete v tématu [upozornění](../../preprocessor/warning.md) nebo [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md)Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4394.

```
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```