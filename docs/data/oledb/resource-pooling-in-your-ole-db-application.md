---
title: Sdružování prostředků v aplikaci OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209761"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Sdružování prostředků v aplikaci OLE DB

Chcete-li v aplikaci využít sdružování, je nutné zajistit, aby OLE DB služby byly vyvolány tím, že získá zdroj dat prostřednictvím `IDataInitialize` nebo `IDBPromptInitialize`. Pokud přímo použijete `CoCreateInstance` k vyvolání poskytovatele založeného na identifikátoru CLSID poskytovatele, nejsou vyvolány žádné OLE DB služby.

Služba OLE DB Services udržuje fondy propojených zdrojů dat, pokud se používá odkaz na `IDataInitialize` nebo `IDBPromptInitialize`, nebo pokud se používá připojení. Fondy se taky udržují automaticky v prostředí služby COM+ 1,0 nebo Internetová informační služba (IIS). Pokud vaše aplikace využívá výhod sdružování mimo služby modelu COM+ 1,0 nebo prostředí IIS, měli byste mít odkaz na `IDataInitialize` nebo `IDBPromptInitialize` nebo podržet aspoň na jednom připojení. Aby se zajistilo, že se fond po uvolnění posledního připojení uvolní v rámci aplikace, ponechejte odkaz nebo ponechte připojení po dobu života vaší aplikace.

Služba OLE DB Services identifikuje fond, ze kterého se vykreslí připojení v době volání `Initialize`. Po vykreslení připojení z fondu se nedá přesunout do jiného fondu. Nepoužívejte proto v aplikaci změny inicializačních informací, jako je například volání `UnInitialize` nebo volání `QueryInterface` pro rozhraní specifické pro poskytovatele před voláním `Initialize`. Také připojení vytvořená s hodnotou výzvy jinou než DBPROMPT_NOPROMPT nejsou ve fondu. Inicializační řetězec načtený z připojení navázaného prostřednictvím výzvy se ale dá použít k vytvoření dalších sdružených připojení ke stejnému zdroji dat.

Někteří poskytovatelé musí vytvořit samostatné připojení pro každou relaci. Tato další připojení se musí samostatně zařadit do distribuované transakce, pokud existuje. Služba OLE DB Services ukládá do mezipaměti a znovu používá jednu relaci na zdroj dat, ale pokud aplikace požádá o více než jednu relaci současně z jednoho zdroje dat, může zprostředkovatel ukončit další připojení a provádět další zařazení transakcí, které není ve fondu. Je efektivnější vytvořit samostatný zdroj dat pro každou relaci ve fondu prostředí, než vytvořit více relací z jednoho zdroje dat.

Vzhledem k tomu, že objekty ADO automaticky využívají OLE DB služby, můžete k navázání připojení použít ADO a sdružování a zařazení se automaticky provádí.

## <a name="see-also"></a>Viz také

[Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)
