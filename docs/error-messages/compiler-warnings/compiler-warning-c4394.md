---
title: Upozornění kompilátoru C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: b97819a6f1b95f083eb594d3b9b2e68cbf30d19a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623698"
---
# <a name="compiler-warning-c4394"></a>Upozornění kompilátoru C4394

' function ': symbol na úrovni AppDomain by neměl být označen atributem __declspec (dllexport)

Funkce označená modifikátorem [appdomain](../../cpp/appdomain.md)`__declspec` je zkompilována do jazyka MSIL (ne do nativního) a tabulky exportu (modifikátor pro[Export](../../windows/export.md)`__declspec`) nejsou podporovány pro spravované funkce.

Můžete deklarovat spravovanou funkci tak, aby měla veřejné usnadnění přístupu. Další informace naleznete v tématu [viditelnost typů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [viditelnost členů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 se vždy vydá jako chyba.  Toto upozornění můžete vypnout pomocí `#pragma warning` nebo **/WD**; Další informace najdete v tématech [Upozornění](../../preprocessor/warning.md) nebo [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4394.

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```