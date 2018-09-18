---
title: Chyba kompilátoru C3381 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd6c1d641f7476d3c372939b948931a306e0f80
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080711"
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