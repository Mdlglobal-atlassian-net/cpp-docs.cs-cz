---
title: Upozornění (úroveň 1) C4526 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed6f2da3252c27b7a84b4d5b73f7e8ba52823dd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118502"
---
# <a name="compiler-warning-level-1-c4526"></a>Kompilátor upozornění (úroveň 1) C4526

'function': statické členské funkce nemůže přepsat virtuální funkce "virtuální function'override ignorovat, virtuální funkce bude skrytá.

Statické členské funkce splňuje kritéria pro přepsání virtuální funkce, která je členská funkce statický i virtuální.

Následující kód vygeneruje C4526:

```
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

Toto jsou možné opravy:

- Pokud se má přepsat virtuální funkce základní třídy funkce, odeberte specifikátor statické.

- Pokud se funkce má být statickou členskou funkci, přejmenujte je tak, aby není v konfliktu s virtuální funkce základní třídy.