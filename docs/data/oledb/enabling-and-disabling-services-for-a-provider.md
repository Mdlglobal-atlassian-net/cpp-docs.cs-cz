---
title: Povolování a zakazování služeb pro zprostředkovatele | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef36e35234aa4878e30e70748a5b2ba2975c38dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099729"
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