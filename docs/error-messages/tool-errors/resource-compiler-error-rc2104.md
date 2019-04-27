---
title: Chyba kompilátoru prostředků RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: 6ac1786e795c0c8ed57af2d341f43b8ba39229c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346558"
---
# <a name="resource-compiler-error-rc2104"></a>Chyba kompilátoru prostředků RC2104

Nedefinovaný název – klíčové slovo nebo klíč: klíč

Zadané klíčové slovo nebo název klíče není definován.

Tato chyba je často způsobeno překlep v definici prostředků nebo v souboru hlaviček zahrnuté. Můžete se také jednat chybí soubor hlaviček.

Pokud chcete problém vyřešit, vyhledejte soubor hlaviček, který by měl obsahovat definované – klíčové slovo nebo název klíče a ověřte, že je součástí souboru prostředků, a že – klíčové slovo nebo klíč název je napsán správně. Pokud váš projekt byl vytvořen s předkompilovanou hlavičkou, a následně ho odebrat, ujistěte se, že soubor prostředků stále zahrnuje všechny požadované záhlaví.

Ověření definovaná klíčová slova a názvy klíčů v souboru prostředků v sadě Visual Studio, otevřete **zobrazení prostředků** okno – v panelu nabídky zvolte **zobrazení**, **zobrazení prostředků**– a pak otevřete místní nabídku pro soubor .rc a zvolte možnost **symbolů prostředků** zobrazíte seznam definovaných symbolů. K úpravě zahrnutých hlaviček, otevřete místní nabídku pro soubor .rc a zvolte **prostředek zahrnuje**.

Pokud narazíte na tuto zprávu:

```
undefined keyword or key name: MFT_STRING
```

Otevřete \MCL\MFC\Include\AfxRes.h a přidejte tuto direktivu:

```
#include <winresrc.h>
```