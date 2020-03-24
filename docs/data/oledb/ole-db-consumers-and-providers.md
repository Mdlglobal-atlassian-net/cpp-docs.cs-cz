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
ms.openlocfilehash: d57ded9d084971c3562fc7f22e6a1a12a4e3368d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210072"
---
# <a name="ole-db-consumers-and-providers"></a>Příjemci a zprostředkovatelé technologie OLE DB

Architektura OLE DB používá model uživatelů a poskytovatelů. Příjemce vytvoří požadavky na data. Poskytovatel reaguje na tyto požadavky tím, že umístí data do tabulkového formátu a vrátí je příjemci. Jakékoli volání, které může příjemce provádět, musí být implementované ve zprostředkovateli.

Technicky definovaná, příjemce je libovolný systémový nebo aplikační kód (nemusí nutně být OLE DB komponenta), která přistupuje k datům prostřednictvím OLE DB rozhraní. Rozhraní jsou implementována ve zprostředkovateli. Proto poskytovatel je jakákoli softwarová součást, která implementuje OLE DB rozhraní pro zapouzdření přístupu k datům a jejich zpřístupnění jiným objektům (tj. spotřebitelům).

Pro role příjemce volá metody na OLE DB rozhraní; poskytovatel OLE DB implementuje požadovaná OLE DB rozhraní.

OLE DB se vyhnout podmínkám klienta a serveru, protože tyto role nikdy nezpůsobují smysl, zejména v n-vrstvé situaci. Vzhledem k tomu, že příjemce může být komponenta na úrovni, která obsluhuje jinou komponentu, by mohla být zavolána klientské součásti. Kromě toho poskytovatel někdy funguje podobně jako ovladač databáze než server.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)
