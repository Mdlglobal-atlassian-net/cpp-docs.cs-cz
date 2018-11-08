---
title: Sdružování prostředků OLE DB a služby
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 1fb5164b9e744175f60c920a1d92278e9d5213f2
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264655"
---
# <a name="ole-db-resource-pooling-and-services"></a>Sdružování prostředků OLE DB a služby

Pro práci s sdružování OLE DB nebo se všemi službami, OLE DB, váš poskytovatel musí podporovat agregace všechny objekty. Jde o požadavek OLE DB 1.5 nebo novější zprostředkovatele. Je velmi důležité pro využívání služby. Poskytovatelé, kteří nepodporují agregace nelze ve fondu a jsou k dispozici žádné další služby.

Do fondu, musí podporovat zprostředkovatelů zdarma vlákno modelu. Fond zdrojů Určuje model vláken poskytovatele podle vlastnost DBPROP_THREADMODEL.

Pokud má poskytovatel globálního připojení stavu, ve kterém můžou změnit zdroj dat je v inicializovaném stavu, má podporovat nové vlastnosti DBPROP_RESETDATASOURCE. Tato vlastnost je volána před připojení již byl použit a dává příležitost k vyčištění stavu před její další použití zprostředkovatele. Pokud zprostředkovatele nelze vyčistit některé stavu přidružené k připojení, může vrátit DBPROPSTATUS_NOTSETTABLE pro vlastnost a připojení nebude znovu použít.

Vlastnost DBPROP_CONNECTIONSTATUS by měla podporovat poskytovatelé, kteří připojení ke vzdálené databázi a může zjistit, zda toto připojení může být ztracené. Tato vlastnost poskytuje schopnost detekovat mrtvého připojení a ujistěte se, že se nevrátíte do fondu služeb OLE DB.

Nakonec automatický zápis do transakce obecně nebude fungovat pokud je implementováno na stejné úrovni, ke které dochází sdružování. Poskytovatelé, které podporují automatické transakce zařazení by měly podporovat zákaz tomuto zařazení ve vystavení vlastnost DBPROP_INIT_OLEDBSERVICES a zakázání zařazení, pokud DBPROPVAL_OS_TXNENLISTMENT není vybraná.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)