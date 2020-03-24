---
title: Upozornění kompilátoru (úroveň 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198117"
---
# <a name="compiler-warning-level-4-c4960"></a>Upozornění kompilátoru (úroveň 4) C4960

funkce ' function ' je příliš velká pro profilaci

Při použití [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)Kompilátor zjistil vstupní modul s funkcí větším než 65 535 instrukcí. Tato velká funkce není k dispozici pro optimalizace na základě profilu.

Chcete-li toto upozornění vyřešit, snižte velikost funkce.
