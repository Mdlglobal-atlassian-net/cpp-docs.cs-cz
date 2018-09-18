---
title: Chyba kompilátoru C3550 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08c22d7e371fda7a229b541f78d4385f2943ee54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047782"
---
# <a name="compiler-error-c3550"></a>Chyba kompilátoru C3550

v tomto kontextu je povolené jenom prosté zadání: decltype(auto).

Pokud `decltype(auto)` slouží jako zástupný symbol pro návratový typ funkce, musí být použit samostatně. Nelze použít jako součást deklarace ukazatelů (`decltype(auto*)`), deklarace odkazu (`decltype(auto&)`), nebo jakékoli jiné takové kvalifikace.

## <a name="see-also"></a>Viz také

[auto](../../cpp/auto-cpp.md)