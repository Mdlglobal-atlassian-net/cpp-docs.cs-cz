---
title: Upozornění kompilátoru C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 13d2ed705bff7b42eb3c348692a5829bd54158b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164869"
---
# <a name="compiler-warning-c4959"></a>Upozornění kompilátoru C4959

> nejde definovat nespravovanou strukturu*typu*v/CLR: safe, protože přístup k jejím členům poskytuje neověřitelný kód.

## <a name="remarks"></a>Poznámky

Přístup k členu nespravovaného typu vytvoří obrázek (Nástroj Peverify. exe), který nelze ověřit.

Další informace najdete v tématu [čistý a ověřitelný kódC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Možnost **/clr: Safe** je v aplikaci visual Studio 2015 zastaralá a nepodporovaná ve visual studiu 2017.

Toto upozornění je vystaveno jako chyba a může být zakázáno pomocí direktivy pragma [Warning](../../preprocessor/warning.md) nebo [/WD](../../build/reference/compiler-option-warning-level.md) kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4959:

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```
