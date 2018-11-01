---
title: Chyba kompilátoru C3211
ms.date: 11/04/2016
f1_keywords:
- C3211
helpviewer_keywords:
- C3211
ms.assetid: 85e33fed-3b59-4315-97e6-20d31c6a985a
ms.openlocfilehash: 6de2129a1cdd6391245148816b29faa65d7e8721
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661215"
---
# <a name="compiler-error-c3211"></a>Chyba kompilátoru C3211

'explicitní specializace': explicitní specializace používá syntaxi částečné specializace, místo toho použijte <> šablony

Explicitní specializace byl chybně vytvořen.

Následující ukázka generuje C3211:

```
// C3211.cpp
// compile with: /LD
template<class T>
struct s;

template<class T>
// use the following line instead
// template<>
struct s<int>{};   // C3211
```