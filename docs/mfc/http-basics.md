---
title: HTTP – základy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56a2692edd9d41f80023e44f4ca8172cba8f9d00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="http-basics"></a>HTTP – základy
Při zápisu internetovou aplikaci, můžete často prozkoumat a přidat k informacím v hlavičce protokolu HTTP. Návratové kódy představují úspěch nebo selhání požadovaná událost. Několik běžných návratové kódy jsou uvedeny v následující tabulce.  
  
|Návratový kód|Význam|  
|-----------------|-------------|  
|200|Adresa URL umístěný, způsobem přenosu|  
|400|Nesrozumitelné požadavku|  
|404|Požadovaná adresa URL nebyla nalezena.|  
|405|Server nepodporuje požadovaný – metoda|  
|500|Neznámou chybu serveru|  
|503|Služba není k dispozici|  
  
 Odpovědi protokolu HTTP jsou seskupené, jak je znázorněno v následující tabulce.  
  
|Skupina|Význam|  
|-----------|-------------|  
|200-299|Úspěch|  
|300-399|Informace o|  
|400-499|Žádost o chybě|  
|500-599|Chyba serveru|  
  
 Protokolu HTTP (Hypertext Transfer) je protokol úrovni aplikace pro systémy hypermédií informace. Další informace o protokolu HTTP a komunikace webových prohlížečů a serverů najdete v části specifikace protokolu HTTP (Hypertext Transfer):  
  
 [http://www.w3.org/pub/WWW/Protocols/](http://www.w3.org/pub/www/protocols/)  
  
## <a name="see-also"></a>Viz také  
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

