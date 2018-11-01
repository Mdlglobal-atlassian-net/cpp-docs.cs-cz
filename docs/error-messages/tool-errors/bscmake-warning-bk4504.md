---
title: Upozornění nástroje BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450294"
---
# <a name="bscmake-warning-bk4504"></a>Upozornění nástroje BSCMAKE BK4504

soubor obsahuje příliš mnoho odkazů; Další odkazy z tohoto zdroje se ignoruje

Soubor .cpp obsahuje víc než 64 000 odkazy na symboly. Když BSCMAKE došlo k 64 000 odkazy v souboru, ignoruje všechny odkazy na další.

Chcete-li tento problém, buď rozdělení souboru na dva nebo více souborů, z nichž každá má méně než 64 000 odkazy na symbol, použijte `#pragma component(browser)` direktivy preprocesoru na limit symboly, které jsou generovány pro konkrétní odkazy. Další informace najdete v tématu [komponenty](../../preprocessor/component.md).