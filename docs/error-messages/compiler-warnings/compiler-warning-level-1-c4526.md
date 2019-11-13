---
title: Upozornění kompilátoru (úroveň 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 60ac01d6a118f37a22b39ab41fa60252866f3360
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966274"
---
# <a name="compiler-warning-level-1-c4526"></a>Upozornění kompilátoru (úroveň 1) C4526

' function ': statická členská funkce nemůže přepsat virtuální funkci Virtual function'override se ignoruje, virtuální funkce bude skrytá.

Statická členská funkce splňuje kritéria pro přepsání virtuální funkce, která umožňuje, aby byla členská funkce virtuální i statická.

Následující kód generuje C4526:

```cpp
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

Níže jsou uvedené možné opravy:

- Pokud byla funkce určena k přepsání virtuální funkce základní třídy, odeberte Statický specifikátor.

- Pokud by byla funkce zamýšlena jako statická členská funkce, přejmenujte ji, aby nedošlo ke konfliktu s virtuální funkcí základní třídy.