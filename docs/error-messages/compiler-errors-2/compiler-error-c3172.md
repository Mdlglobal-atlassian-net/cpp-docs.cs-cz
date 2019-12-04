---
title: Chyba kompilátoru C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761735"
---
# <a name="compiler-error-c3172"></a>Chyba kompilátoru C3172

' module_name ': v projektu nelze zadat jiné atributy idl_module

[idl_module](../../windows/idl-module.md) atributů se stejným názvem, ale s různými parametry `dllname` nebo `version` byly nalezeny ve dvou souborech v kompilaci. Pro každou kompilaci lze zadat pouze jeden jedinečný atribut `idl_module`.

Stejné atributy `idl_module` lze zadat ve více než jednom souboru se zdrojovým kódem.

Například pokud byly nalezeny následující atributy `idl_module`:

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

A potom

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

kompilátor vygeneruje C3172 (Všimněte si různých hodnot verze).
