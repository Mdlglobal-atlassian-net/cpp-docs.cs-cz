---
title: Příjemci a zprostředkovatelé technologie OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: f5940ca65e42787c3156a9537cb3f3f6694339c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031310"
---
# <a name="ole-db-consumers-and-providers"></a>Příjemci a zprostředkovatelé technologie OLE DB

Architektura technologie OLE DB využívá model příjemci a zprostředkovatelé. Příjemce provede žádostí o data. Poskytovatel reaguje na tyto žádosti o umístění dat v tabelárním formátu a jeho vrácením příjemci. Každé volání, které může spotřebitel musí být implementované ve zprostředkovateli.

Technicky definované příjemce je jakýkoli systém nebo aplikace, kód (ne tedy nutně komponentu technologie OLE DB), který přistupuje k datům prostřednictvím rozhraní OLE DB. Rozhraní jsou implementované ve zprostředkovateli. Zprostředkovatel je proto softwarová součást, která implementuje rozhraní technologie OLE DB pro zapouzdření přístup k datům a zveřejníte ho na jiné objekty (tedy spotřebitelé).

Příjemce pro role, volá metody v rozhraní OLE DB; zprostředkovatele OLE DB implementuje rozhraní potřebných OLE DB.

Protože tyto role není vždy dávat smysl, zejména v situacích, n vrstvá se vyhnete OLE DB podmínky klientem a serverem. Vzhledem k tomu, že příjemce může být součást na vrstvu, která slouží jiné součásti, volání klienta komponenty by bylo matoucí. Navíc zprostředkovatele někdy pracuje jako ovladač databáze, než server.

## <a name="see-also"></a>Viz také:

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)