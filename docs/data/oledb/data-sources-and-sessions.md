---
title: Zdroje dat a relace
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 0514f6a9285936c85608f08774c1d377fd72d6ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211052"
---
# <a name="data-sources-and-sessions"></a>Zdroje dat a relace

Následující obrázek znázorňuje třídy, které podporují připojení ke zdroji dat a přístup k němu. Každá třída je založena na standardní implementaci OLE DB komponenty.

![Třídy zdroje dat a relace](../../data/oledb/media/vcdatasourcesessionclasses.gif "Třídy zdroje dat a relace") <br/>
Třídy zdroje dat a relace

Třídy jsou:

- [CDataSource](../../data/oledb/cdatasource-class.md) Tato třída vytvoří instanci objektu zdroje dat, která vytvoří a spravuje připojení ke zdroji dat prostřednictvím poskytovatele OLE DB. Zdroj dat přebírá informace, jako je adresa zdroje dat a ověřovací informace, ve formě připojovacího řetězce.

   Také je potřeba poznamenat, že pomocná třída [CEnumerator –](../../data/oledb/cenumerator-class.md) se často používá předtím, než se naváže jakékoli připojení, aby se získal seznam dostupných zprostředkovatelů registrovaných v systému. To umožňuje vybrat poskytovatele jako zdroj dat. Například dialogové okno **Vlastnosti datového propojení** používá tuto třídu k naplnění seznamu zprostředkovatelů na kartě **poskytovatelé** . Je rovna funkci `SQLBrowseConnect` nebo `SQLDriverConnect`.

- [CSession](../../data/oledb/csession-class.md) Tato třída vytvoří instanci objektu Session, která představuje jednu relaci přístupu ke zdroji dat. Pro zdroj dat však můžete vytvořit více relací. Pro každou relaci můžete vytvořit sady řádků, příkazy a další objekty pro přístup k datům ze zdroje dat. Relace zpracovává transakce.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)
