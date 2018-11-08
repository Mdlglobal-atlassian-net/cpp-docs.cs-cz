---
title: Povolení a zákaz služeb OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: c5eaff8b3b37096eeca8777b6ba8bb91e01d7cd2
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265201"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB

OLE DB služby Component Manager porovná příjemce na vlastnostech podporovaných zprostředkovatelem k určení, zda k rozšířené funkce požadoval uživatel může použít jednotlivé komponenty služby byly zadány vlastnosti. Pokud aplikace požaduje posuvný kurzoru a zprostředkovatel podporuje pouze dopředné kurzor, služby Component Manager používá klientský kurzor stroj součást služby posuvný nakonfigurovánu. Pokud aplikace se spoléhá na rozšířené funkce podporované ve výchozím nastavení pro poskytovatele řádků a aplikace nebude explicitně nastavit vlastnosti pro žádost o funkci, funkci nemusí zobrazit v dané sadě řádků vrácených klienta Modul kurzoru. Pokud chcete interoperabilní, by měla aplikace vždy nastavit vlastnosti explicitní žádost o rozšířené funkce místech.

V některých případech může být potřeba zakázat jednotlivých služeb OLE DB pro práci i se stávajícími aplikacemi, které počítají informace o vlastnosti zprostředkovatele. Služby rozhraní OLE DB poskytují možnost zakázat jednotlivé služby nebo všech služeb, a to na základě připojení pomocí připojení nebo pro všechny aplikace pomocí jednoho zprostředkovatele.

## <a name="see-also"></a>Viz také

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)