---
title: Chyba kompilátoru C3628 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a65dc33c5381b063c3adb01072e930075108649
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037369"
---
# <a name="compiler-error-c3628"></a>Chyba kompilátoru C3628

'základní třída': spravované nebo WinRTclasses podporují jenom dědění typu public

Byl proveden pokus o použití spravované nebo WinRT třídy jako [privátní](../../cpp/private-cpp.md) nebo [chráněné](../../cpp/protected-cpp.md) základní třídy. A spravovaný nebo třída WinRT jde použít jenom jako základní třída s atributem [veřejné](../../cpp/public-cpp.md) přístup.

Následující ukázka generuje C3628 a ukazuje, jak ho opravit:

```
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
