---
title: OLE DB – šablony, atributy a jiné implementace technologie
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 079ec68afe2e538a40920fb2c6524f8d5b8aae89
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520634"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB – šablony, atributy a jiné implementace technologie

## <a name="atl-ole-db-templates"></a>Šablony knihovny ATL technologie OLE DB

Šablony technologie OLE DB, které jsou součástí knihovny ATL (knihovnu Active Template Library), ujistěte se, databázové technologie OLE DB výkonné usnadňuje používání tím, že poskytuje třídy, které implementují mnoho běžně používaných rozhraní OLE DB. Spolu se tato šablona obsahuje knihovny podpora průvodce pro vytváření aplikací OLE DB starter.

Tato šablona knihovny obsahuje dvě části:

- **OLE DB – šablony příjemce** používaný k implementaci aplikace klienta (příjemce) technologie OLE DB.

- **Šablony zprostředkovatele technologie OLE DB** používaný k implementaci aplikace serveru (poskytovatel) technologie OLE DB.

Použití šablony technologie OLE DB, byste měli vědět, jak šablon jazyka C++, COM a rozhraní OLE DB. Pokud nejste obeznámeni s OLE DB, přečtěte si téma [OLE DB referenční informace pro programátory](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Další informace můžete:

- Přečtěte si témata o [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md) nebo [šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Vytvoření [příjemce technologie OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) nebo [zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md).

- Zobrazit seznam [třídy příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) nebo [třídy zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).

- Zobrazit seznam [OLE DB – Ukázky šablon](https://github.com/Microsoft/VCSamples).

- Zobrazit [referenční informace pro OLE DB programátory](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (ve Windows SDK).

## <a name="ole-db-attributes"></a>Atributy technologie OLE DB

[Atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md) poskytují pohodlný způsob, jak vytvořit příjemci knihovny OLE DB. OLE DB atributy vloží kód založený na [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-reference.md) k vytvoření a zprostředkovatele pracovní technologie OLE DB. Pokud je třeba zadat funkce nepodporované atributy, můžete použít šablony technologie OLE DB ve spojení s atributy ve vašem kódu.

## <a name="mfc-ole-db-classes"></a>Třídy MFC OLE DB

Knihovna MFC má jednu třídu, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), který zobrazuje záznamy databáze v ovládacích prvcích. Zobrazení je připojený přímo k zobrazení formuláře `CRowset` objektu a pole se zobrazí `CRowset` objektu v ovládacích prvcích šablony dialogového okna. Také poskytuje výchozí implementaci pro přechod na první další, předchozí nebo poslední záznam a rozhraní pro aktualizace záznamu aktuálně pro zobrazení. Další informace naleznete v tématu `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Rozhraní OLE DB SDK

V případech, kdy šablony technologie OLE DB nepodporují funkci OLE DB budete muset použít samotné rozhraní OLE DB. Další informace najdete v tématu [OLE DB referenční informace pro programátory](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)