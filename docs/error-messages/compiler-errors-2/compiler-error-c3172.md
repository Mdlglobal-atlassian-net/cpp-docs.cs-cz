---
title: Chyba kompilátoru C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 5c9c1561b63c740b9f7f5d85b2bf3e04de2542c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175183"
---
# <a name="compiler-error-c3172"></a>Chyba kompilátoru C3172

'module_name': nelze zadat jiné atributy idl_module v projektu

[možnost idl_module](../../windows/idl-module.md) atributy se stejným názvem ale jiným `dllname` nebo `version` parametry byly nalezeny ve dvou souborů v kompilaci. Pouze jeden jedinečný `idl_module` může být určen atribut za kompilace.

Identické `idl_module` atributy lze zadat ve více než jeden soubor zdrojového kódu.

Například pokud následující `idl_module` byly nalezeny atributy:

```
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

a pak,

```
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

kompilátor vygeneruje C3172 (Všimněte si hodnot jinou verzi).