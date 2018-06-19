---
title: 'Výjimky: Výjimky OLE | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 991848e9b5b78ad960fb8ed0bdf09dd56db47e2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345536"
---
# <a name="exceptions-ole-exceptions"></a>Výjimky: Výjimky OLE
Techniky a zařízení pro zpracování výjimek v prostředí OLE jsou stejné jako v případě zpracování další výjimky. Další informace o zpracování výjimek, najdete v článku [zpracování výjimek C++](../cpp/cpp-exception-handling.md).  
  
 Všechny objekty výjimek jsou odvozeny od abstraktní základní třída `CException`. MFC poskytuje dvě třídy pro zpracování OLE – výjimky:  
  
-   [COleException](../mfc/reference/coleexception-class.md) pro zpracování obecné OLE – výjimky.  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) pro generování a zpracování OLE dispatch výjimky (Automatizace).  
  
 Rozdíl mezi tyto dvě třídy je množství informací o poskytují a kdy se používá. `COleException` má veřejná data člena, který obsahuje OLE stavový kód pro výjimku. `COleDispatchException` poskytuje další informace, včetně následujících:  
  
-   Kód chyby specifické pro aplikaci  
  
-   Popis chyby, jako je například "Disk plný."  
  
-   Nápověda kontext, který aplikace můžete použít pro poskytují další informace pro uživatele  
  
-   Název souboru nápovědy aplikace  
  
-   Název aplikace, které vygenerovalo výjimku  
  
 `COleDispatchException` poskytuje další informace, takže se dá použít s produkty, jako je Microsoft Visual Basic. Popis ústní chyby mohou být používány okno se zprávou nebo jiné oznámení; informace nápovědy lze pomoct uživateli reakce na stav, který způsobil výjimku.  
  
 Dvě globální funkce odpovídají dvě třídy výjimky OLE: [afxthrowoleexception –](../mfc/reference/exception-processing.md#afxthrowoleexception) a [afxthrowoledispatchexception –](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Je použijte k throw obecné OLE – výjimky a výjimky OLE odesílání, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

