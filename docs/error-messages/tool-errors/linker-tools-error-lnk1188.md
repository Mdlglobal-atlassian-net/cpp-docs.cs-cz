---
title: Chyba Linkerů LNK1188 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36b31590d94d809c16ed64d16071db0919f60238
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098937"
---
# <a name="linker-tools-error-lnk1188"></a>Chyba linkerů LNK1188

BADFIXUPSECTION:: Neplatný cíl opravy 'symbol'; je to možné nula délku části

Při odkazu VxD cíl přemístění nemá oddíl. S LINK386 (starší verze), vytvoří se záznam omf – skupina (generovaných MASM GROUP – direktiva) pravděpodobně byl použit zkombinovat oddíl s nulovou délkou s jinou část nenulovou délkou. Formátu COFF nepodporuje skupiny směrnice a nulové délky oddílů. Pokud odkaz automaticky převede tento typ omf – objektů COFF, může dojít k této chybě.