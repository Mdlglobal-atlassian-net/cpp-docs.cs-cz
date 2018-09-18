---
title: Chyba kompilátoru C3171 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c58f2ecd9651c347f45c29139ffe0ed65a6e3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082258"
---
# <a name="compiler-error-c3171"></a>Chyba kompilátoru C3171

'module': nelze specifikovat odlišné atributy module v projektu

[modul](../../windows/module-cpp.md) atributy se seznamy různých parametrů nebyly nalezeny ve dvou souborů v kompilaci. Pouze jeden jedinečný `module` může být určen atribut za kompilace.

Identické `module` atributy lze zadat ve více než jeden soubor zdrojového kódu.

Například pokud následující `module` byly nalezeny atributy:

```
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

a pak,

```
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

kompilátor vygeneruje C3171 (Všimněte si hodnot jinou verzi).