---
title: Chyba Linkerů LNK1106 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 719ff1a87f3f1afc19cf38736c0059c46a8a9bdc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110871"
---
# <a name="linker-tools-error-lnk1106"></a>Chyba linkerů LNK1106

Neplatný soubor nebo plný disk: Nelze vyhledat umístění

Nástroj nelze číst nebo zapisovat do `location` v souboru mapovaných do paměti.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Disk je plný.

     Uvolněte místo na disku a znovu propojit.

1. Chcete propojit přes síť.

     Některé sítě plně nepodporuje soubory mapované paměti používané linkeru. Zkuste propojení na místním disku.

1. Chybný blok na disku.

     I když operační systém a hardware disku by měl mít tyto došlo k chybě, můžete chtít spustit program kontroly disku.

1. Nedostatek prostoru v haldě.

     Zobrazit [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Další informace.