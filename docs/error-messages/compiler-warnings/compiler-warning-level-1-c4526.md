---
title: Kompilátor upozornění (úroveň 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 892e6c37e54a868be48ced35354a1096aa7bf9d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160741"
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