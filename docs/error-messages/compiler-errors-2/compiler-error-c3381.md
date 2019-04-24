---
title: Chyba kompilátoru C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: ae416d68831d1964c89d938dfcddd364e521195c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328861"
---
# <a name="compiler-error-c3381"></a>Chyba kompilátoru C3381

'assembly': sestavení specifikátory přístupu jsou dostupné pouze v kódu zkompilovaném s parametrem/CLR.

Nativní typy mohou být viditelný mimo sestavení, ale můžete nastavit jenom přístup k sestavení pro nativní typy v **/CLR** kompilace.

Další informace najdete v tématu [zadejte viditelnost](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3381.

```
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```