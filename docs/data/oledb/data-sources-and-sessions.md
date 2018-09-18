---
title: Zdroje dat a relace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 07c7a395f111d4473eed5f85a1329e85358f5d0c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037668"
---
# <a name="data-sources-and-sessions"></a>Zdroje dat a relace

Následující obrázek ukazuje třídy, které podporují připojení k a přístup ke zdroji dat. Každá třída je založen na standardní součástí implementace technologie OLE DB.  
  
![Datové zdroje a relace třídy](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
Zdroj dat a relace tříd  
  
Třídy jsou:  
  
- [CDataSource –](../../data/oledb/cdatasource-class.md) této třídy vytváří instanci objektu zdroje dat, které vytváří a spravuje připojení ke zdroji dat pomocí zprostředkovatele OLE DB. Zdroj dat trvá informace, jako je adresu a ověřovací informace o zdroji dat v podobě připojovacího řetězce.  
  
     Je také vhodné poznamenat, že pomocná třída [CEnumerator](../../data/oledb/cenumerator-class.md) se často používá před žádné připojení k získání seznamu dostupných zprostředkovatelů registrován v systému. To umožňuje vybrat jako zdroj dat poskytovatele. Například **vlastnosti propojení dat** dialogové okno používá k naplnění seznamu zprostředkovatelů na tuto třídu **poskytovatelé** kartu. Je ekvivalentní `SQLBrowseConnect` nebo `SQLDriverConnect` funkce.  
  
- [CSession](../../data/oledb/csession-class.md) této třídy vytváří instanci objektu relace, který reprezentuje relaci jeden přístup ke zdroji dat. Však můžete vytvořit více relací na datovém zdroji. Pro každou relaci můžete vytvořit sady řádků, příkazy a dalších objektů pro přístup k datům z datového zdroje. Relace nezpracovává transakce.  
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)