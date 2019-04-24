---
title: Zdroje dat a relace
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 2c11230d106b50e8120dfa9f4e283e97700d2739
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175999"
---
# <a name="data-sources-and-sessions"></a>Zdroje dat a relace

Následující obrázek ukazuje třídy, které podporují připojení k a přístup ke zdroji dat. Každá třída je založen na standardní součástí implementace technologie OLE DB.

![Datové zdroje a relace třídy](../../data/oledb/media/vcdatasourcesessionclasses.gif "datové zdroje a relace třídy") <br/>
Zdroj dat a relace tříd

Třídy jsou:

- [CDataSource –](../../data/oledb/cdatasource-class.md) této třídy vytváří instanci objektu zdroje dat, které vytváří a spravuje připojení ke zdroji dat pomocí zprostředkovatele OLE DB. Zdroj dat trvá informace, jako je adresu a ověřovací informace o zdroji dat v podobě připojovacího řetězce.

   Je také vhodné poznamenat, že pomocná třída [CEnumerator](../../data/oledb/cenumerator-class.md) se často používá před žádné připojení k získání seznamu dostupných zprostředkovatelů registrován v systému. To umožňuje vybrat jako zdroj dat poskytovatele. Například **vlastnosti propojení dat** dialogové okno používá k naplnění seznamu zprostředkovatelů na tuto třídu **poskytovatelé** kartu. To odpovídá `SQLBrowseConnect` nebo `SQLDriverConnect` funkce.

- [CSession](../../data/oledb/csession-class.md) této třídy vytváří instanci objektu relace, který reprezentuje relaci jeden přístup ke zdroji dat. Však můžete vytvořit více relací na datovém zdroji. Pro každou relaci můžete vytvořit sady řádků, příkazy a dalších objektů pro přístup k datům z datového zdroje. Relace nezpracovává transakce.

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)