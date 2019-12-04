---
title: Chyba kompilátoru C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761748"
---
# <a name="compiler-error-c3171"></a>Chyba kompilátoru C3171

' Module ': v projektu nelze zadat jiné atributy modulu

atributy [modulů](../../windows/module-cpp.md) s různými seznamy parametrů byly nalezeny ve dvou souborech v kompilaci. Pro každou kompilaci lze zadat pouze jeden jedinečný atribut `module`.

Stejné atributy `module` lze zadat ve více než jednom souboru se zdrojovým kódem.

Například pokud byly nalezeny následující atributy `module`:

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

A potom

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

kompilátor vygeneruje C3171 (Všimněte si různých hodnot verze).
