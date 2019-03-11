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
ms.openlocfilehash: d6a77d57a88166354fcb222c0da09690426108e9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750046"
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

## <a name="see-also"></a>Viz také:

[Datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md)
