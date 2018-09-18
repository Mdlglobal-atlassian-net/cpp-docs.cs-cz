---
title: Upozornění nástroje BSCMAKE BK4502 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4142993b3f4f5bda2b3e4ce322aa26d7beca8584
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056323"
---
# <a name="bscmake-warning-bk4502"></a>Upozornění nástroje BSCMAKE BK4502

zkrácen. SBR soubor 'filename' není v názvu souboru

Během aktualizace byl zadán soubor .sbr nulové délky, které původně nebyly součástí souboru .bsc.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Zadán chybný název souboru.

1. Soubor byl odstraněn. (Chyba [nástroje BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) výsledky.)

1. Soubor poškozený, vyžadování BSCMAKE provést úplné sestavení.