---
title: Upozornění linkerů LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: c81c93a6df8c7eef809f243e3dc56164ea548371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472225"
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