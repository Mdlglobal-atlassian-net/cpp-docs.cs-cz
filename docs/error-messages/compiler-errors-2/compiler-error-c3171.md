---
title: Chyba kompilátoru C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 602c9ca1051646fca2c5788c036354047fad2522
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175424"
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