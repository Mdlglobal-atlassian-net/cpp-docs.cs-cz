---
title: Chyba kompilátoru C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 8b01a2f7b9c55fb57c880df5033538f4e45f76b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643687"
---
# <a name="compiler-error-c2410"></a>Chyba kompilátoru C2410

'identifier': nejednoznačný název členu "context"

Identifikátor je členem více než jeden struktury nebo sjednocení v tomto kontextu.

Použijte specifikátor struktury nebo sjednocení na operand, který způsobil chybu. Je identifikátor typu struktury nebo sjednocení specifikátor `struct` nebo `union` ( `typedef` název nebo proměnnou stejného typu jako struktury nebo sjednocení, na kterou se odkazuje). Levý operand první operátor výběru členů (.) použít operand musí být specifikátor.