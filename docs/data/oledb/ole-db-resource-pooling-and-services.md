---
title: "OLE DB sdílení prostředků ve fondech a služby | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2b3500c90455c7f180f16eae3c56433f57d0492
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-resource-pooling-and-services"></a>Sdružování prostředků OLE DB a služby
Pro práci s sdružování OLE DB nebo s jakoukoli službu, technologie OLE DB, musí podporovat poskytovatel agregace všech objektů. Jde o požadavek OLE DB 1.5 nebo novější zprostředkovatele. Je důležité pro využívání služby. Zprostředkovatelé, kteří nepodporují agregace nelze ve fondu a jsou k dispozici žádné další služby.  
  
 Chcete-li ve fondu, musí podporovat zprostředkovatelé volné vlákno modelu. Fond zdrojů Určuje model vláken poskytovatele podle požadavků **DBPROP_THREADMODEL** vlastnost.  
  
 Pokud má poskytovatel nástroje globální připojení stavu, který může změnit při inicializovaný stav zdroje dat, musí podporovat nové **DBPROP_RESETDATASOURCE** vlastnost. Tato vlastnost je volána před připojení se znovu použije a dává příležitost vyčištění stavu před jeho další použití zprostředkovatele. Pokud zprostředkovatele nelze vyčistit některé stavu přidružené k připojení, může vrátit **DBPROPSTATUS_NOTSETTABLE** pro vlastnost a připojení nebude znovu použít.  
  
 Zprostředkovatelé, které se připojují ke vzdálené databázi a může zjistit, zda by měly podporovat, může dojít ke ztrátě připojení **DBPROP_CONNECTIONSTATUS** vlastnost. Tato vlastnost poskytuje schopnost zjišťovat neaktivní připojení a ujistěte se, že nebudou zobrazeny do fondu služby rozhraní OLE DB.  
  
 Nakonec automatický zápis do transakce obecně nefunguje Pokud je implementována na stejné úrovni, ke kterému dochází sdružování. Zprostředkovatelé, kteří podporují automatický zápis do transakce sami by měly podporovat zakázání této zařazení díky zpřístupnění **DBPROP_INIT_OLEDBSERVICES** vlastnost a zakázání zařazení, pokud **DBPROPVAL_OS_ TXNENLISTMENT** není vybraná.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)