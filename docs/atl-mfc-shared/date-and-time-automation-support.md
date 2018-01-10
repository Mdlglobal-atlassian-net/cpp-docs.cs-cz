---
title: "Datum a čas: Podpora automatizace | Microsoft Docs"
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
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a40a8fe49d9564714c328b657bc0d85d52ad84b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="date-and-time-automation-support"></a>Datum a čas: Podpora automatizace
Tento článek popisuje, jak využívat výhod služeb knihovny třídy související se správou datum a čas. Popisuje postupy patří:  
  
-   [Získávání aktuální čas](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [Výpočet uplynulý čas](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [Formátování řetězec představující datum a čas](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) třída poskytuje způsob, jak představují informace o datu a času. Poskytuje podrobnější a větší rozsah než [CTime](../atl-mfc-shared/reference/ctime-class.md) třídy. [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) třída reprezentuje uplynulý čas, jako je rozdíl mezi dvěma `COleDateTime` objekty.  
  
 `COleDateTime` a `COleDateTimeSpan` třídy jsou určeny k použití s `COleVariant` třída používaná v automatizace. `COleDateTime`a `COleDateTimeSpan` jsou také užitečná při programování MFC databáze, ale lze ji použít vždy, když chcete k manipulaci se hodnoty data a času. I když `COleDateTime` třída má větší rozsah hodnot a podrobnější než `CTime` třída, vyžaduje další úložiště na objekt, než `CTime`. Existují také některé důležité informace při práci s základní **datum** typu. V tématu [typ DATE](../atl-mfc-shared/date-type.md) další podrobnosti o provádění **datum**.  
  
 `COleDateTime`objekty lze používá k reprezentování kalendářní data mezi 1. leden 100 a 31. prosince 9999. `COleDateTime`objekty jsou plovoucí hodnoty bodu s rozlišení odpovídající 1 milisekundu. `COleDateTime`je založena na **datum** datového typu, definovaného v dokumentaci k MFC pod [COleDateTime::operator datum](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). Skutečné implementace **datum** přesahuje tyto hranice. `COleDateTime` Implementace ukládá tyto hranice usnadňuje práci s třídou.  
  
 `COleDateTime`nepodporuje juliánský data. Gregoriánský kalendář se předpokládá, že rozšíření na 1. leden 100 zpět v čase.  
  
 `COleDateTime`ignoruje letní čas (letní čas). Následující příklad kódu porovná dvě metody výpočtu časový interval, který protne datum přepnutí DST: jeden pomocí CRT a na jiných pomocí `COleDateTime`. DST přepne, ve většině, druhý týden v dubnu a třetí v říjnu.  
  
 První metoda nastaví dva `CTime` objekty, *čas1* a *time2*, duben 5 a 6. dubna, pomocí standardní struktury typu C **tm** a `time_t`. Kód zobrazí *čas1* a *time2* a časový interval mezi nimi.  
  
 Druhá metoda vytvoří dvě `COleDateTime` objekty, `oletime1` a `oletime2`a nastaví je stejná data jako *čas1* a *time2*. Zobrazuje `oletime1` a `oletime2` a časový interval mezi nimi.  
  
 CRT správně vypočítá rozdíl 23 hodin. `COleDateTimeSpan`vypočítá rozdíl 24 hodin.  
  
 Upozorňujeme, že alternativní řešení je u konce v příkladu se zobrazí datum správně pomocí `COleDateTime::Format`. Najdete v článku znalostní báze Knowledge Base "chyb: Format("%D") nezdaří `COleDateTime` a `COleDateTimeSpan`" (Q167338).  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas](../atl-mfc-shared/date-and-time.md)

