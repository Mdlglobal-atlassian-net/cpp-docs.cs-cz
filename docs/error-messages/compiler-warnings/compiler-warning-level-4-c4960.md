---
title: Upozornění (úroveň 4) C4960 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed6ba083017c84cd6af05b917ff8417b0394d7c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085716"
---
# <a name="compiler-warning-level-4-c4960"></a>Kompilátor upozornění (úroveň 4) C4960

'function' je příliš velké, aby se dalo Profilovat.

Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupu modulu s funkcí větší než 65 535 pokyny. Velké funkce není k dispozici pro optimalizace řízenou profily.

Pokud chcete vyřešit toto upozornění, zmenšete velikost funkce.