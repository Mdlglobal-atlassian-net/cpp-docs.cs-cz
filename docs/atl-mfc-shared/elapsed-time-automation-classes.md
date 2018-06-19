---
title: 'Uplynulý čas: Třídy automatizace | Microsoft Docs'
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
ms.openlocfilehash: c1abf6274137ae67b159ad43612d24020a0d14e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354965"
---
# <a name="elapsed-time-automation-classes"></a>Uplynulý čas: Třídy automatizace
Tento postup ukazuje, jak pro výpočet rozdílu mezi dvěma `CTime` objekty a získání přístupu `CTimeSpan` výsledek.  
  
#### <a name="to-calculate-elapsed-time"></a>Chcete-li vypočítat uplynulý čas  
  
1.  Vytvořte dvě `COleDateTime` objekty.  
  
2.  Nastavte jednu z `COleDateTime` objekty na aktuální čas.  
  
3.  Proveďte některé časově náročný úkol.  
  
4.  Nastavení dalších `COleDateTime` objektu na aktuální čas.  
  
5.  Rozdíl mezi dvěma dobu trvat.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md)

