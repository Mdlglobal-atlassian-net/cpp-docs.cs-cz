---
title: Upozornění (úroveň 1) C4651 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b516ef86372901d00dd20d94ed10d5e361bbab8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099461"
---
# <a name="compiler-warning-level-1-c4651"></a>Kompilátor upozornění (úroveň 1) C4651

zadaná pro předkompilovanou hlavičku, ale ne pro aktuální kompilaci definice

Definice byl zadán při generování předkompilované hlavičky, ale není v této kompilaci.

Definice, nebudou platit uvnitř předkompilované hlavičky, ale ne ve zbývající části kódu.

Předkompilované hlavičky byl sestaven s /DSYMBOL, kompilátor vygeneruje toto upozornění v případě kompilace/YU nemá /DSYMBOL.  Přidání do příkazového řádku/YU /DSYMBOL řeší toto upozornění.