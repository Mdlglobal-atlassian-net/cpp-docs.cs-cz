---
title: OLE DB sdílení prostředků ve fondech a služby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c2a04d0b990906f9f124edc9dbda71d65127e4ed
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338558"
---
# <a name="ole-db-resource-pooling-and-services"></a>Sdružování prostředků OLE DB a služby
Pro práci s sdružování OLE DB nebo se všemi službami, OLE DB, váš poskytovatel musí podporovat agregace všechny objekty. Jde o požadavek OLE DB 1.5 nebo novější zprostředkovatele. Je velmi důležité pro využívání služby. Poskytovatelé, kteří nepodporují agregace nelze ve fondu a jsou k dispozici žádné další služby.  
  
 Do fondu, musí podporovat zprostředkovatelů zdarma vlákno modelu. Fond zdrojů Určuje model vláken poskytovatele podle `DBPROP_THREADMODEL` vlastnost.  
  
 Pokud má poskytovatel globálního připojení stavu, ve kterém můžou změnit zdroj dat je v inicializovaném stavu, by měly podporovat nové `DBPROP_RESETDATASOURCE` vlastnost. Tato vlastnost je volána před připojení již byl použit a dává příležitost k vyčištění stavu před její další použití zprostředkovatele. Pokud zprostředkovatele nelze vyčistit některé stavu přidružené k připojení, může vrátit `DBPROPSTATUS_NOTSETTABLE` pro vlastnost a připojení nebude znovu použít.  
  
 Poskytovatelé, kteří připojení ke vzdálené databázi a může zjistit, zda by měla podporovat, může dojít ke ztrátě připojení `DBPROP_CONNECTIONSTATUS` vlastnost. Tato vlastnost poskytuje schopnost detekovat mrtvého připojení a ujistěte se, že se nevrátíte do fondu služeb OLE DB.  
  
 Nakonec automatický zápis do transakce obecně nefunguje Pokud je implementováno na stejné úrovni, ke které dochází sdružování. Poskytovatelé, které podporují automatické transakce zařazení sami by měly podporovat zakázání tomuto zařazení zveřejněním `DBPROP_INIT_OLEDBSERVICES` vlastnost a zakázání zařazení, pokud `DBPROPVAL_OS_TXNENLISTMENT` není vybraná.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)