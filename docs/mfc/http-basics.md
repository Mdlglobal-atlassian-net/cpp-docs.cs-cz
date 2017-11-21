---
title: "HTTP – základy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1fa71e0aa1dc73884ef9783824198912758592ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Základy internetového programování MFC](../mfc/mfc-internet-programming-basics.md)

