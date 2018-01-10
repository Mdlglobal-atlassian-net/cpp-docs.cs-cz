---
title: "Výjimky: Výjimky OLE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67be1947b3fa08c26d659838922ce42a905167a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-ole-exceptions"></a>Výjimky: Výjimky OLE
Techniky a zařízení pro zpracování výjimek v prostředí OLE jsou stejné jako v případě zpracování další výjimky. Další informace o zpracování výjimek, najdete v článku [zpracování výjimek C++](../cpp/cpp-exception-handling.md).  
  
 Všechny objekty výjimek jsou odvozeny od abstraktní základní třída `CException`. MFC poskytuje dvě třídy pro zpracování OLE – výjimky:  
  
-   [COleException](../mfc/reference/coleexception-class.md) pro zpracování obecné OLE – výjimky.  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) pro generování a zpracování OLE dispatch výjimky (Automatizace).  
  
 Rozdíl mezi tyto dvě třídy je množství informací o poskytují a kdy se používá. `COleException`má veřejná data člena, který obsahuje OLE stavový kód pro výjimku. `COleDispatchException`poskytuje další informace, včetně následujících:  
  
-   Kód chyby specifické pro aplikaci  
  
-   Popis chyby, jako je například "Disk plný."  
  
-   Nápověda kontext, který aplikace můžete použít pro poskytují další informace pro uživatele  
  
-   Název souboru nápovědy aplikace  
  
-   Název aplikace, které vygenerovalo výjimku  
  
 `COleDispatchException`poskytuje další informace, takže se dá použít s produkty, jako je Microsoft Visual Basic. Popis ústní chyby mohou být používány okno se zprávou nebo jiné oznámení; informace nápovědy lze pomoct uživateli reakce na stav, který způsobil výjimku.  
  
 Dvě globální funkce odpovídají dvě třídy výjimky OLE: [afxthrowoleexception –](../mfc/reference/exception-processing.md#afxthrowoleexception) a [afxthrowoledispatchexception –](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Je použijte k throw obecné OLE – výjimky a výjimky OLE odesílání, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

