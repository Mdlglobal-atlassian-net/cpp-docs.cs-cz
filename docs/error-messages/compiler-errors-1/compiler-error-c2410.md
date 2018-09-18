---
title: Chyba kompilátoru C2410 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4c2b57bcae062ccf811e33cf1deaea45f83737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052449"
---
# <a name="compiler-error-c2410"></a>Chyba kompilátoru C2410

'identifier': nejednoznačný název členu "context"

Identifikátor je členem více než jeden struktury nebo sjednocení v tomto kontextu.

Použijte specifikátor struktury nebo sjednocení na operand, který způsobil chybu. Je identifikátor typu struktury nebo sjednocení specifikátor `struct` nebo `union` ( `typedef` název nebo proměnnou stejného typu jako struktury nebo sjednocení, na kterou se odkazuje). Levý operand první operátor výběru členů (.) použít operand musí být specifikátor.