---
title: Chyba kompilátoru C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 7c1a9e4e099fc33dd585e5cdbffa2bbb8ea36987
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755587"
---
# <a name="compiler-error-c3370"></a>Chyba kompilátoru C3370

název idl_module: idl_module ještě není definovaný.

Než budete moci použít [idl_module](../../windows/idl-module.md) k určení vstupního bodu v knihovně DLL, je nutné nejprve pomocí `idl_module` zadat název knihovny DLL.

Následující ukázka generuje C3370:

```cpp
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```
