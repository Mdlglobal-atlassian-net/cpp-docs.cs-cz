---
title: Příjemci knihovny OLE DB a poskytovatelé | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4f52177e5fcb34470e606497297985d805a151f6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077592"
---
# <a name="ole-db-consumers-and-providers"></a>Příjemci a zprostředkovatelé technologie OLE DB

Architektura technologie OLE DB využívá model příjemci a zprostředkovatelé. Příjemce provede žádostí o data. Poskytovatel reaguje na tyto žádosti o umístění dat v tabelárním formátu a jeho vrácením příjemci. Každé volání, které může spotřebitel musí být implementované ve zprostředkovateli.

Technicky definované příjemce je jakýkoli systém nebo aplikace, kód (ne tedy nutně komponentu technologie OLE DB), který přistupuje k datům prostřednictvím rozhraní OLE DB. Rozhraní jsou implementované ve zprostředkovateli. Zprostředkovatel je proto softwarová součást, která implementuje rozhraní technologie OLE DB pro zapouzdření přístup k datům a zveřejníte ho na jiné objekty (tedy spotřebitelé).

Příjemce pro role, volá metody v rozhraní OLE DB; zprostředkovatele OLE DB implementuje rozhraní potřebných OLE DB.

Protože tyto role není vždy dávat smysl, zejména v situacích, n vrstvá se vyhnete OLE DB podmínky klientem a serverem. Vzhledem k tomu, že příjemce může být součást na vrstvu, která slouží jiné součásti, volání klienta komponenty by bylo matoucí. Navíc zprostředkovatele někdy pracuje jako ovladač databáze, než server.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)