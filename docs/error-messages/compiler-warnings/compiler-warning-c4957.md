---
title: Upozornění kompilátoru C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 340c26c97d0b5b686eee487cd3fd8b6b05bdf373
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164901"
---
# <a name="compiler-warning-c4957"></a>Upozornění kompilátoru C4957

> '*cast*': explicitní přetypování z '*cast_from*' na '*cast_to*' nelze ověřit

## <a name="remarks"></a>Poznámky

Výsledkem přetypování bude neověřitelný obraz.

Některá přetypování jsou bezpečná (například `static_cast`, která aktivuje uživatelsky definované převody a `const_cast`). [Safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) je zaručeno vytvořit ověřitelný kód.

Další informace najdete v tématu [čistý a ověřitelný kódC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Možnost **/clr: Safe** je v aplikaci visual Studio 2015 zastaralá a nepodporovaná ve visual studiu 2017.

Toto upozornění je vystaveno jako chyba a může být zakázáno pomocí direktivy pragma [Warning](../../preprocessor/warning.md) nebo [/WD](../../build/reference/compiler-option-warning-level.md) kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4957:

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
