---
title: Kompilátor upozornění (úroveň 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 04732619571420e777244b81bf4b93b775477a20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310978"
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilátor upozornění (úroveň 1) C4124

__fastcall s kontrolou zásobníku je neefektivní

`__fastcall` – Klíčové slovo byl použit s kontrolou zásobníku povolena.

`__fastcall` Konvence generuje rychlejší, ale kontrolou zásobníku způsobí pomalejší kódu. Při použití `__fastcall`, vypněte s kontrolou zásobníku **check_stack –** – Direktiva pragma nebo /Gs.

Jenom pro první funkce deklarovaná za těchto podmínek se objeví toto upozornění.