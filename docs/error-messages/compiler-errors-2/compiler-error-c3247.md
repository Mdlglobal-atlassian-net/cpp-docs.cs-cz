---
title: Chyba kompilátoru C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: 7ca84b4f054852aefa75a9c4547286137b436c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569157"
---
# <a name="compiler-error-c3247"></a>Chyba kompilátoru C3247

'class1': Konstrukt coclass nemůže dědit z jiného konstruktu coclass 'class2'

Třída označena [coclass](../../windows/coclass.md) atribut nemůže dědit z jiné třídy označené `coclass` atribut.

Následující ukázka generuje C3247:

```
// C3247.cpp
[module(name="MyLib")];
[coclass]
class a {
};

[coclass]
class b : public a {   // C3247
};
int main() {
}
```