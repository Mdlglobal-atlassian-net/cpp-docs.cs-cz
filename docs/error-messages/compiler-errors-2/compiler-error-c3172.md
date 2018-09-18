---
title: Chyba kompilátoru C3172 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25c3b1fd9132c6b170fdf74b1619a35d83959f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117633"
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