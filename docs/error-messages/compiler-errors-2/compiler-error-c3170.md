---
title: Chyba kompilátoru C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: 5ef39e4580601dd90b5695d9115902bb5b834409
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174702"
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