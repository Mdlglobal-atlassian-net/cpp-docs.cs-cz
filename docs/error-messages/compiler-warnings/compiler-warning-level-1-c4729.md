---
title: Kompilátor upozornění (úroveň 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: f5f93cadd97eefe0d6c6da97be99ec5fd82ece24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574391"
---
# <a name="compiler-warning-level-1-c4729"></a>Kompilátor upozornění (úroveň 1) C4729

upozornění založená na funkce je moc velká pro graf toku

Toto upozornění se vygeneruje, když funkce je moc velké, aby se dalo kompilovat s reliable kontrolu pro situace, které se vygeneruje upozornění. Toto upozornění je pouze generován, když [/Od](../../build/reference/od-disable-debug.md) – možnost kompilátoru použít.

Pokud chcete vyřešit toto upozornění, rozdělte funkce na menší funkce.