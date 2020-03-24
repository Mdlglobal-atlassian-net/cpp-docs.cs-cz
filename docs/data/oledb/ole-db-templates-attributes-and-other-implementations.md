---
title: OLE DB – šablony, atributy a jiné implementace technologie
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 722bfdf02dc89e061351fd2a87b5d019db10da6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209882"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB – šablony, atributy a jiné implementace technologie

## <a name="atl-ole-db-templates"></a>Šablony OLE DB ATL

OLE DB šablony, které jsou součástí knihovny ATL (Active Template Library), usnadňují použití technologie vysoce výkonného OLE DB databáze tím, že poskytuje třídy, které implementují mnoho běžně používaných OLE DB rozhraní. Společně s touto knihovnou šablon přichází Průvodce podporu vytváření OLE DBch aplikací Starter.

Tato knihovna šablon obsahuje dvě části:

- **Šablony OLE DB příjemců** Slouží k implementaci klienta aplikace OLE DB (příjemce).

- **Šablony poskytovatele OLE DB** Slouží k implementaci aplikace OLE DB serveru (poskytovatele).

Chcete-li použít šablony OLE DB, měli byste být obeznámeni se C++ šablonami, com a rozhraními OLE DB. Pokud nejste obeznámeni s OLE DB, přečtěte si téma referenční informace o [programátorech OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Další informace najdete zde:

- Přečtěte si témata o [šablonách zákazníků OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) nebo [šablonách poskytovatelů OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Vytvořte poskytovatele [OLE DBho příjemce](../../data/oledb/creating-an-ole-db-consumer.md) nebo [OLE DB](../../data/oledb/creating-an-ole-db-provider.md).

- Podívejte se na seznam [OLE DB třídy příjemce](../../data/oledb/ole-db-consumer-templates-reference.md) nebo [třídy poskytovatelů OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).

- Viz seznam [ukázek šablon OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB).

- Viz [Referenční příručka OLE DB programátora](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (v Windows SDK).

## <a name="ole-db-attributes"></a>Atributy OLE DB

[Atributy příjemce OLE DB](../../windows/ole-db-consumer-attributes.md) poskytují pohodlný způsob, jak vytvářet OLE DB spotřebitelé. Atributy OLE DB vloží kód založený na [šablonách spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) a vytvoří pracovní OLE DB příjemce a poskytovatelé. Pokud potřebujete určit funkčnost, kterou atributy nepodporují, můžete použít šablony OLE DB ve spojení s atributy ve vašem kódu.

## <a name="mfc-ole-db-classes"></a>MFC – třídy OLE DB

Knihovna MFC má jednu třídu, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), která v ovládacích prvcích zobrazuje záznamy databáze. Zobrazení je formulářové zobrazení, které je přímo propojeno s objektem `CRowset` a zobrazuje pole objektu `CRowset` v ovládacích prvcích šablony dialogového okna. Poskytuje také výchozí implementaci pro přechod na první, další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu, který je aktuálně zobrazen. Další informace najdete v tématu `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Rozhraní OLE DB SDK

V případech, kdy šablony OLE DB nepodporují OLE DB funkcionality, je nutné použít rozhraní OLE DB samotné. Další informace najdete v tématu [OLE DB reference programátora](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) v Windows SDK.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)
