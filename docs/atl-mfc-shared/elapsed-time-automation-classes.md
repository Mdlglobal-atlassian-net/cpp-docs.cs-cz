---
title: "Uplynulý čas: Třídy automatizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 51479f73112ed80ee981f3919fd3941d1eb0c8f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

