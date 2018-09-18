---
title: Chyba kompilátoru C3170 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7a193abcd59c3e9454eec1108f1e3bbb66efcc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070363"
---
# <a name="compiler-error-c3170"></a>Chyba kompilátoru C3170

v projektu nemůžete mít rozdílné identifikátory modulu.

[modul](../../windows/module-cpp.md) ve dvou souborů v kompilaci byly nalezeny atributy s různými názvy. Pouze jeden jedinečný `module` může být určen atribut za kompilace.

Identické `module` atributy lze zadat ve více než jeden soubor zdrojového kódu.

Například, pokud nebyly nalezeny následující atributy modulu:

```
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

a pak,

```
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

kompilátor vygeneruje C3170 (Všimněte si různých názvů).