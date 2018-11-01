---
title: 'Uplynulý čas: Automatizační třídy'
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
ms.openlocfilehash: fbd01a4e7268456af342293d77ef74d372d2e639
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583908"
---
# <a name="elapsed-time-automation-classes"></a>Uplynulý čas: Automatizační třídy

Tento postup ukazuje, jak vypočítat rozdíl mezi dvěma `CTime` objekty a get `CTimeSpan` výsledek.

## <a name="to-calculate-elapsed-time"></a>Pro výpočet uplynulého času

1. Pak vytvoříte další dva `COleDateTime` objekty.

1. Nastavte jednu z `COleDateTime` objektů na aktuální čas.

1. Provedení některých časově náročné úlohy.

1. Nastavit další `COleDateTime` objektů na aktuální čas.

1. Využijte rozdíl mezi dvěma časy.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Viz také

[Datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md)
