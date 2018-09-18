---
title: Chyba kompilátoru C2803 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7885735ebad1ff90afaf4ba8eaf6dfca9f3e0ab3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027034"
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