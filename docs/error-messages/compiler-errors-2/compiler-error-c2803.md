---
title: Chyba kompilátoru C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d39f737ba02f3fa9c9d5f61594ddf730db6739a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760657"
---
# <a name="compiler-error-c2803"></a>Chyba kompilátoru C2803

operátor operator musí mít aspoň jeden formální parametr typu třídy.

Přetížený operátor nemá parametr typu třídy.

Je nutné předat alespoň jeden parametr odkazem (bez použití ukazatelů, ale odkazy) nebo podle hodnoty, aby bylo možné napsat "a < b" (a a b je typu Class A).

Pokud jsou oba parametry ukazateli, bude čistě porovnávání adres ukazatelů a nebude používat uživatelsky definovaný převod.

Následující ukázka generuje C2803:

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
