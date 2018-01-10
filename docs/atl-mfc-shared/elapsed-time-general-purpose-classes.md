---
title: "Uplynulý čas: Třídy pro obecné účely | Microsoft Docs"
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
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51eea60669fb7ad35525d65013ffc8420649349b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="elapsed-time-general-purpose-classes"></a>Uplynulý čas: Třídy pro obecné účely
Následující postup ukazuje, jak pro výpočet rozdílu mezi dvěma `CTime` objekty a získání přístupu `CTimeSpan` výsledek.  
  
#### <a name="to-calculate-elapsed-time"></a>Chcete-li vypočítat uplynulý čas  
  
1.  Použití `CTime` a `CTimeSpan` objekty, které chcete vypočítat uplynulý čas, následujícím způsobem:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     Jakmile jste vypočítali `elapsedTime`, můžete použít členské funkce `CTimeSpan` k extrakci komponenty hodnoty uplynulý čas.  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas: Obecné třídy](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

