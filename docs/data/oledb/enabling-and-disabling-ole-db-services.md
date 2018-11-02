---
title: Povolení a zákaz služeb OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 65b02eb130dcbaa8c3233bd6e0ba6930df2ed5cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509990"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB

OLE DB služby Component Manager porovná vlastnosti určené spotřebitele, které jsou podporovány poskytovatelem k určení, zda mohou být volány jednotlivé komponenty služby, tím se uspokojí rozšířené funkce požadoval uživatel. Například pokud aplikace požaduje posuvný kurzoru a zprostředkovatel podporuje pouze dopředné kurzor, služba Component Manager vyvolá komponentu služby klientský kurzor stroj posuvný nakonfigurovánu. Pokud aplikace se spoléhá na rozšířené funkce podporované ve výchozím nastavení pro poskytovatele řádků a aplikace není nastaveno explicitně vlastnosti, které chcete požádat o funkce, funkce nemusí zobrazit v dané sadě řádků vrácených klienta Modul kurzoru. Pokud chcete interoperabilní, by měla aplikace vždy nastavit vlastnosti explicitní žádost o rozšířené funkce místech.

V některých případech může být potřeba zakázat jednotlivých služeb OLE DB pro práci i se stávajícími aplikacemi, které počítají informace o vlastnosti zprostředkovatele. Služby rozhraní OLE DB poskytují možnost zakázat jednotlivé služby nebo všech služeb, a to na základě připojení pomocí připojení nebo pro všechny aplikace pomocí jednoho zprostředkovatele.

## <a name="see-also"></a>Viz také

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)