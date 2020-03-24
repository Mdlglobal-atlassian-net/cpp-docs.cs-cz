---
title: Databázové třídy ATL (šablony OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 76e9f49d4b394d0c807ca1f3d103ff325ded8a09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213496"
---
# <a name="atl-database-classes-ole-db-templates"></a>Databázové třídy ATL (šablony OLE DB)

Společnost Microsoft poskytuje několik implementací OLE DB, sadu rozhraní COM, která poskytuje jednotný přístup k datům v různých zdrojích informací a formátech.

Šablony OLE DB jsou C++ šablony v knihovně ATL, které usnadňují použití databázové technologie OLE DB tím, že poskytují třídy, které implementují mnoho běžně používaných OLE DB rozhraní.

Tato knihovna šablon obsahuje dvě části:

- [Šablony OLE DB příjemců](../data/oledb/ole-db-consumer-templates-cpp.md) Slouží k implementaci klienta aplikace OLE DB (příjemce).

- [Šablony poskytovatele OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) Slouží k implementaci aplikace OLE DB serveru (poskytovatele).

Kromě toho [Atributy příjemce OLE DB](../windows/ole-db-consumer-attributes.md) poskytují pohodlný způsob, jak vytvářet OLE DB spotřebitelé. Atributy OLE DB vkládají kód založený na šablonách spotřebitelů OLE DB k vytváření pracovních OLE DBch uživatelů.

Všimněte si, že knihovna MFC obsahuje jednu třídu, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), která v ovládacích prvcích zobrazuje záznamy databáze. Zobrazení je formulářové zobrazení, které je přímo propojeno s objektem `CRowset` a zobrazuje pole objektu `CRowset` v ovládacích prvcích šablony dialogového okna.

Další informace najdete v tématu [OLE DB programování](../data/oledb/ole-db-programming.md) a [OLE DB Programátorská příručka](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Viz také

[Vytvoření příjemce OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Vytvoření zprostředkovatele OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Referenční dokumentace k šablonám zprostředkovatelů OLE DB](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Ukázky šablon OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
