---
title: Povolení a zákaz služeb OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210961"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB

Služba OLE DB Service Component Manager porovnává vlastnosti zadané uživatelem s vlastnostmi podporovanými poskytovatelem k určení, zda lze jednotlivé součásti služby použít k uspokojení rozšířených funkcí požadovaných příjemcem. Například pokud aplikace požaduje posuvný kurzor a poskytovatel podporuje pouze jenom dopředný kurzor, nástroj Service Component Manager používá komponentu služby Klient Cursor Engine k zajištění rolovací funkce. Pokud se aplikace spoléhá na rozšířené funkce podporované ve výchozím nastavení v sadě řádků poskytovatele a aplikace explicitně nenastaví vlastnosti tak, aby požadovala tuto funkčnost, funkce se nemusí zobrazit na sadě řádků vrácené klientem. Modul kurzoru. Aby bylo možné vzájemně fungovat, aplikace by měly vždy nastavit vlastnosti tak, aby explicitně vyžadovaly rozšířenou funkčnost v případě potřeby.

V některých případech může být nutné zakázat jednotlivé OLE DB služby, aby fungovaly dobře se stávajícími aplikacemi, které vedou k odhadu charakteristik zprostředkovatele. Služba OLE DB Services nabízí možnost zakázat jednotlivé služby nebo všechny služby, a to buď na základě připojení, nebo u všech aplikací, které používají jednoho poskytovatele.

## <a name="see-also"></a>Viz také

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)
