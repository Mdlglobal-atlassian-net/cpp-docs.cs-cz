---
title: Chyba kompilátoru C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: a3e2268bfc5597668e8689d093a0c2bb7f18e037
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207282"
---
# <a name="compiler-error-c2129"></a>Chyba kompilátoru C2129

statická funkce Function je deklarovaná, ale není definovaná.

Je proveden dopředný odkaz na funkci `static`, která není nikdy definována.

V rámci rozsahu souboru musí být definována funkce `static`. Pokud je funkce definována v jiném souboru, musí být deklarována `extern`.
