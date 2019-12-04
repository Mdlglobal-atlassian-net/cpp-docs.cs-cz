---
title: Chyba kompilátoru C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749565"
---
# <a name="compiler-error-c3381"></a>Chyba kompilátoru C3381

Assembly: specifikátory přístupu k sestavení jsou dostupné jenom v kódu kompilovaném s možností/CLR.

Nativní typy mohou být viditelné mimo sestavení, ale lze zadat pouze přístup k sestavení pro nativní typy v kompilaci **/CLR** .

Další informace naleznete v tématu [viditelnost typů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [/CLR (kompilace společného jazykového modulu runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3381.

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
