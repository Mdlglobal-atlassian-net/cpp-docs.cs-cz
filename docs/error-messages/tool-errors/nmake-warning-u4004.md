---
title: Upozornění nástroje NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436215"
---
# <a name="nmake-warning-u4004"></a>Upozornění nástroje NMAKE U4004

příliš mnoho pravidel pro cíl targetname

Byla zadána více než jeden blok popis pro danou cílovou pomocí jednoho dvojtečky (**:**) jako oddělovače. NMAKE spouští příkazy v první blok popis a novější bloky ignorovat.

K určení stejného cíle ve více závislostí, použijte dvojité dvojtečky (`::`) jako oddělovač v každém řádku závislostí.