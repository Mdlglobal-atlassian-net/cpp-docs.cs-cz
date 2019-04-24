---
title: Chyba linkerů LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 7551e2f3f1efc90913981feb674f48aadb9ace51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255316"
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