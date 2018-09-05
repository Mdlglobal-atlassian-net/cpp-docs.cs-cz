---
title: 'Uplynulý čas: Automatizační třídy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcde08e8ffdb30f9ebf0ae7577bf836e84513a07
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751674"
---
# <a name="elapsed-time-automation-classes"></a>Uplynulý čas: Automatizační třídy

Tento postup ukazuje, jak vypočítat rozdíl mezi dvěma `CTime` objekty a get `CTimeSpan` výsledek.

#### <a name="to-calculate-elapsed-time"></a>Pro výpočet uplynulého času

1. Pak vytvoříte další dva `COleDateTime` objekty.

2. Nastavte jednu z `COleDateTime` objektů na aktuální čas.

3. Provedení některých časově náročné úlohy.

4. Nastavit další `COleDateTime` objektů na aktuální čas.

5. Využijte rozdíl mezi dvěma časy.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Viz také

[Datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md)

