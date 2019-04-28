---
title: Chyba kompilátoru C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: 731e84955192688a87c020b2b65a80ab5671cad6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363931"
---
# <a name="compiler-error-c3507"></a>Chyba kompilátoru C3507

ProgID může mít maximálně 39 znaků 'id'; ani obsahovat interpunkci smí z '.'; nesmí začínat číslicí

[Progid](../../windows/progid.md) atribut má omezení na hodnoty, které může trvat.

Následující ukázka generuje C3507:

```
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```