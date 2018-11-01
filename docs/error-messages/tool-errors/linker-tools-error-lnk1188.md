---
title: Chyba linkerů LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461253"
---
# <a name="linker-tools-error-lnk1188"></a>Chyba linkerů LNK1188

BADFIXUPSECTION:: Neplatný cíl opravy 'symbol'; je to možné nula délku části

Při odkazu VxD cíl přemístění nemá oddíl. S LINK386 (starší verze), vytvoří se záznam omf – skupina (generovaných MASM GROUP – direktiva) pravděpodobně byl použit zkombinovat oddíl s nulovou délkou s jinou část nenulovou délkou. Formátu COFF nepodporuje skupiny směrnice a nulové délky oddílů. Pokud odkaz automaticky převede tento typ omf – objektů COFF, může dojít k této chybě.