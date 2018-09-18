---
title: Upozornění Linkerů LNK4006 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4006
dev_langs:
- C++
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c992369d7bb3d9a3571e23c42a64bf936d5ae383
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017609"
---
# <a name="linker-tools-warning-lnk4006"></a>Upozornění linkerů LNK4006

symbol už je definovaný v objektu. Druhá definice se ignoruje.

Dané `symbol`, zobrazí v upravené podobě, byl definován vícekrát. Když je zjištěna toto upozornění, `symbol` dvakrát se přidají, ale použije se jenom jeho první formulář.

Toto upozornění můžete získat, při pokusu sloučit do větve dvě knihovny importu.

Pokud bude probíhat opětovné sestavení knihovny run-time jazyka C, můžete tuto zprávu ignorovat.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Dané `symbol` může být zabalené funkce, vytvořené kompilací s [/Gy](../../build/reference/gy-enable-function-level-linking.md). Tento symbol je zahrnutý ve více než jeden soubor, ale byl změněn mezi kompilacemi. Znovu zkompilovat všechny soubory, které zahrnují `symbol`.

1. Dané `symbol` může byly definovány rozdílně v dva členské objekty v jiných knihovnách.

1. Absolutní je pravděpodobně definována dvakrát, s jinou hodnotou v každé definici.

1. Pokud chybová zpráva při kombinování knihovny, `symbol` již existuje v knihovně se přidávají do.