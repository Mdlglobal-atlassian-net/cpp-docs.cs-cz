---
title: Upozornění kompilátoru C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: 474bdfa6eb670f39a2876b0c1490e7254cf216e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164897"
---
# <a name="compiler-warning-c4956"></a>Upozornění kompilátoru C4956

> *typ*: Tento typ nejde ověřit.

## <a name="remarks"></a>Poznámky

Toto upozornění je generováno, je-li zadána možnost [/clr: Safe](../../build/reference/clr-common-language-runtime-compilation.md) a váš kód obsahuje typ, který nelze ověřit. Možnost **/clr: Safe** je v aplikaci visual Studio 2015 zastaralá a nepodporovaná ve visual studiu 2017.

Další informace najdete v tématu [čistý a ověřitelný kódC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Toto upozornění je vystaveno jako chyba a může být zakázáno pomocí direktivy pragma [Warning](../../preprocessor/warning.md) nebo [/WD](../../build/reference/compiler-option-warning-level.md) kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
