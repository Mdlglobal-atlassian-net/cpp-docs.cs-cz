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
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210025"
---
# <a name="ole-db-resource-pooling-and-services"></a>Sdružování prostředků OLE DB a služby

Aby bylo možné dobře spolupracovat s OLE DB sdružováním nebo s jakoukoli OLE DB službou, váš poskytovatel musí podporovat agregaci všech objektů. Toto je požadavek jakéhokoli poskytovatele OLE DB 1,5 nebo novějšího. Je klíčové pro využití služeb. Zprostředkovatele, kteří nepodporují agregaci, nelze zařadit do fondu a žádné další služby nejsou k dispozici.

Aby bylo možné fondy vyřadit do fondu, musí podporovat model bezplatného vlákna. Fond zdrojů Určuje model vláken poskytovatele podle vlastnosti DBPROP_THREADMODEL.

Pokud má poskytovatel globální stav připojení, který se může změnit, pokud je zdroj dat v inicializovaném stavu, měla by podporovat novou vlastnost DBPROP_RESETDATASOURCE. Tato vlastnost je volána před tím, než se připojení znovu použije a dává poskytovateli možnost Vyčistit stav před dalším použitím. Pokud zprostředkovatel nemůže vyčistit nějaký stav přidružený k připojení, může vrátit DBPROPSTATUS_NOTSETTABLE pro vlastnost a připojení nebude znovu použito.

Poskytovatelé, kteří se připojují ke vzdálené databázi a mohou zjistit, zda může být toto připojení ztraceno, by mělo podporovat vlastnost DBPROP_CONNECTIONSTATUS. Tato vlastnost dává službám OLE DB možnost detekovat nedoručená připojení a zajistit, aby se nevracely do fondu.

A nakonec automatické zařazení transakce obvykle nefunguje, pokud není implementováno na stejné úrovni, ke které se sdružování provádí. Poskytovatelé, kteří podporují automatické zařazení transakce, by měli podporovat zakázání tohoto zařazení tím, že vystaví vlastnost DBPROP_INIT_OLEDBSERVICES a zakáže zařazení, pokud je DBPROPVAL_OS_TXNENLISTMENT zrušení výběru.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)
