---
title: Chyba linkerů LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: f2e3e1d9948960beed631861c5981f2d09daf632
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455936"
---
# <a name="linker-tools-error-lnk1158"></a>Chyba linkerů LNK1158

nelze spustit 'název souboru.

Daný spustitelný soubor volá [odkaz](../../build/reference/linker-command-line-syntax.md) není v adresáři, který obsahuje odkaz, ani v adresáři uvedeném na proměnné prostředí PATH.

Například obdržíte tuto chybu, pokud se pokusíte použít parametr PGOPTIMIZE [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) – možnost linkeru na počítači s operačním systémem 32-bit.