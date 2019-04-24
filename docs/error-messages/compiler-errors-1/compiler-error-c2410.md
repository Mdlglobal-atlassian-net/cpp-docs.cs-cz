---
title: Chyba kompilátoru C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 8b01a2f7b9c55fb57c880df5033538f4e45f76b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282323"
---
# <a name="compiler-error-c2410"></a>Chyba kompilátoru C2410

'identifier': nejednoznačný název členu "context"

Identifikátor je členem více než jeden struktury nebo sjednocení v tomto kontextu.

Použijte specifikátor struktury nebo sjednocení na operand, který způsobil chybu. Je identifikátor typu struktury nebo sjednocení specifikátor `struct` nebo `union` ( `typedef` název nebo proměnnou stejného typu jako struktury nebo sjednocení, na kterou se odkazuje). Levý operand první operátor výběru členů (.) použít operand musí být specifikátor.