---
title: Sdružování prostředků OLE DB a služby
ms.date: 11/04/2016
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 7c57376404b37de95e01be6459b3d57ddcc53fe3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448097"
---
# <a name="ole-db-resource-pooling-and-services"></a>Sdružování prostředků OLE DB a služby

Pro práci s sdružování OLE DB nebo se všemi službami, OLE DB, váš poskytovatel musí podporovat agregace všechny objekty. Jde o požadavek OLE DB 1.5 nebo novější zprostředkovatele. Je velmi důležité pro využívání služby. Poskytovatelé, kteří nepodporují agregace nelze ve fondu a jsou k dispozici žádné další služby.

Do fondu, musí podporovat zprostředkovatelů zdarma vlákno modelu. Fond zdrojů Určuje model vláken poskytovatele podle `DBPROP_THREADMODEL` vlastnost.

Pokud má poskytovatel globálního připojení stavu, ve kterém můžou změnit zdroj dat je v inicializovaném stavu, by měly podporovat nové `DBPROP_RESETDATASOURCE` vlastnost. Tato vlastnost je volána před připojení již byl použit a dává příležitost k vyčištění stavu před její další použití zprostředkovatele. Pokud zprostředkovatele nelze vyčistit některé stavu přidružené k připojení, může vrátit `DBPROPSTATUS_NOTSETTABLE` pro vlastnost a připojení nebude znovu použít.

Poskytovatelé, kteří připojení ke vzdálené databázi a může zjistit, zda by měla podporovat, může dojít ke ztrátě připojení `DBPROP_CONNECTIONSTATUS` vlastnost. Tato vlastnost poskytuje schopnost detekovat mrtvého připojení a ujistěte se, že se nevrátíte do fondu služeb OLE DB.

Nakonec automatický zápis do transakce obecně nefunguje Pokud je implementováno na stejné úrovni, ke které dochází sdružování. Poskytovatelé, které podporují automatické transakce zařazení sami by měly podporovat zakázání tomuto zařazení zveřejněním `DBPROP_INIT_OLEDBSERVICES` vlastnost a zakázání zařazení, pokud `DBPROPVAL_OS_TXNENLISTMENT` není vybraná.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)