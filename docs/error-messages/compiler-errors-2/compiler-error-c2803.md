---
title: Chyba kompilátoru C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447265"
---
# <a name="compiler-error-c2803"></a>Chyba kompilátoru C2803

'operator operátor' musí mít aspoň jeden formální parametr typu třídy.

Přetížený operátor chybí parametr typu třídy.

Je nutné předat nejmíň jeden parametr odkazem (bez použití ukazatele, ale odkazy) nebo hodnota, která má být schopni napsat "< b" (typ třídy A a b).

Pokud jsou oba parametry ukazatele bude čistě porovnání adresách ukazatelů a nebudeme je používat uživatelem definovaný převod.

Následující ukázka generuje C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```