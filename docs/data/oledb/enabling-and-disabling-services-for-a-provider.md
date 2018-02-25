---
title: "Povolování a zakazování služeb pro zprostředkovatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60e54d9d02cc819c9eaf7674257d846c537da615
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Povolování a zakazování služeb pro zprostředkovatele
Jednotlivé služby rozhraní OLE DB můžete povolit nebo zakázat ve výchozím nastavení pro všechny aplikace, která přistupují k jednoho zprostředkovatele. To se provádí přidáním **OLEDB_SERVICES** položky registru zprostředkovatele je CLSID, s `DWORD` hodnota určuje služby, které chcete povolit nebo zakázat, jak je znázorněno v následující tabulce.  
  
|Povolené výchozí služby|Hodnota – klíčové slovo|  
|------------------------------|-------------------|  
|Všechny služby (výchozí)|0xFFFFFFFF|  
|Všechny kromě sdružování a AutoEnlistment|0xFFFFFFFE|  
|Všechny kromě kurzoru klienta|0xfffffffb|  
|Všechny kromě sdružování AutoEnlistment a klienta kurzoru|0xfffffff0|  
|Žádné služby|0x00000000|  
|Žádné agregace všechny služby jsou zakázány|\<chybí klíč >|  
  
## <a name="see-also"></a>Viz také  
 [Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)