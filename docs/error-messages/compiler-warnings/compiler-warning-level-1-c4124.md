---
title: Upozornění (úroveň 1) C4124 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a69190487c22987ead2d00ec102785ed42ea93c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090922"
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilátor upozornění (úroveň 1) C4124

__fastcall s kontrolou zásobníku je neefektivní

`__fastcall` – Klíčové slovo byl použit s kontrolou zásobníku povolena.

`__fastcall` Konvence generuje rychlejší, ale kontrolou zásobníku způsobí pomalejší kódu. Při použití `__fastcall`, vypněte s kontrolou zásobníku **check_stack –** – Direktiva pragma nebo /Gs.

Jenom pro první funkce deklarovaná za těchto podmínek se objeví toto upozornění.