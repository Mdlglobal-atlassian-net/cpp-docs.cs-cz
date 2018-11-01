---
title: Chyba linkerů LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537958"
---
# <a name="linker-tools-error-lnk1223"></a>Chyba linkerů LNK1223

soubor je neplatný nebo poškozený: soubor obsahuje neplatný .pdata příspěvky

Pro RISC platformy, které používají pdata tato chyba nastane, pokud kompilátor generované .pdata oddílu s seřazená položky.

Chcete-li vyřešit tento problém, pokuste se zkompilovat bez [/GL (optimalizace celého programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) povolena. Prázdných těl funkcí může také v některých případech způsobit k této chybě.