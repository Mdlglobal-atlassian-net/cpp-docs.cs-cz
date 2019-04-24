---
title: Chyba kompilátoru C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 581aae7e1f979b3dd39caf2ce3d263fdb856c56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221682"
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
