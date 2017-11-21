---
title: "A zprostředkovatele OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd09e1566a6f53244d420387870a03b0b34f8fb6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-consumers-and-providers"></a>Příjemci a zprostředkovatelé technologie OLE DB
Architektura technologie OLE DB používá model příjemci a zprostředkovatelé. Příjemce vytváří požadavky na data. Zprostředkovatel reaguje na tyto požadavky uvedení v tabulkovém formátu data a vrátit k příjemce. Žádném volání, které uplatnit musí být implementované ve zprostředkovateli.  
  
 Technicky definované, příjemce je všechny systém nebo aplikace, kód (nikoli nutně komponenta technologie OLE DB), který používá data prostřednictvím rozhraní OLE DB. Rozhraní jsou implementované ve zprostředkovateli. Proto zprostředkovatele je softwarová součást, který implementuje rozhraní OLE DB pro zapouzdření přístup k datům a umístěte ho do jiné objekty (příjemci).  
  
 Z hlediska role příjemce volá metody rozhraní OLE DB; zprostředkovatele OLE DB implementuje potřebné rozhraní OLE DB.  
  
 OLE DB zabraňuje podmínky klient a server, protože tyto role vždy smysl, hlavně v situacích, n vrstvá. Vzhledem k příjemce může být součást na vrstvu, která má jiné komponenty, při volání klienta součásti být matoucí. Navíc poskytovatele někdy pracuje jako ovladač databáze, než server.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)