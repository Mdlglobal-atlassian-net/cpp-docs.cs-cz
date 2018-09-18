---
title: Povolení a zákaz služeb OLE DB | Dokumentace Microsoftu
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
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6edd507edc21d58d17435b1d31d918a965db624a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100731"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB

OLE DB služby Component Manager porovná vlastnosti určené spotřebitele, které jsou podporovány poskytovatelem k určení, zda mohou být volány jednotlivé komponenty služby, tím se uspokojí rozšířené funkce požadoval uživatel. Například pokud aplikace požaduje posuvný kurzoru a zprostředkovatel podporuje pouze dopředné kurzor, služba Component Manager vyvolá komponentu služby klientský kurzor stroj posuvný nakonfigurovánu. Pokud aplikace se spoléhá na rozšířené funkce podporované ve výchozím nastavení pro poskytovatele řádků a aplikace není nastaveno explicitně vlastnosti, které chcete požádat o funkce, funkce nemusí zobrazit v dané sadě řádků vrácených klienta Modul kurzoru. Pokud chcete interoperabilní, by měla aplikace vždy nastavit vlastnosti explicitní žádost o rozšířené funkce místech.  
  
V některých případech může být potřeba zakázat jednotlivých služeb OLE DB pro práci i se stávajícími aplikacemi, které počítají informace o vlastnosti zprostředkovatele. Služby rozhraní OLE DB poskytují možnost zakázat jednotlivé služby nebo všech služeb, a to na základě připojení pomocí připojení nebo pro všechny aplikace pomocí jednoho zprostředkovatele.  
  
## <a name="see-also"></a>Viz také  

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)