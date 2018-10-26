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
ms.openlocfilehash: ce6a8b2ef9ac807e48cff42186453666cebda5ee
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055981"
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