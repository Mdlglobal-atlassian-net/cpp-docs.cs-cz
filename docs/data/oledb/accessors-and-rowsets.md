---
title: Přístupové objekty a sady řádků
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 45180b3ac2647c9f4f5d25a1322794552bd79004
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212378"
---
# <a name="accessors-and-rowsets"></a>Přístupové objekty a sady řádků

Chcete-li nastavit a načíst data, OLE DB šablony používají přistupující objekt a sadu řádků prostřednictvím třídy [CAccessorRowset –](../../data/oledb/caccessorrowset-class.md) . Tato třída může zpracovávat více přístupových objektů různých typů.

## <a name="accessor-types"></a>Přístupové typy

Všechny přistupující objekty jsou odvozeny z [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase` poskytuje parametry i vazby sloupců.

Následující obrázek ukazuje typy přistupujícího objektu.

![Přístupové typy](../../data/oledb/media/vcaccessortypes.gif "Přístupové typy")<br/>
Přístupové třídy

- [CAccessor –](../../data/oledb/caccessor-class.md) Tento přistupující objekt použijte, když znáte strukturu zdroje databáze v době návrhu. `CAccessor` staticky váže záznam databáze, který obsahuje vyrovnávací paměť, ke zdroji dat.

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Tento přistupující objekt použijte, pokud neznáte strukturu databáze v době návrhu. `CDynamicAccessor` volá `IColumnsInfo::GetColumnInfo` k získání informací o sloupci databáze. Vytváří a spravuje přistupující objekt a vyrovnávací paměť.

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) Pomocí tohoto přístupového objektu můžete zpracovat neznámé typy příkazů. Při přípravě příkazů může `CDynamicParameterAccessor` získat informace o parametrech z rozhraní `ICommandWithParameters`, pokud poskytovatel podporuje `ICommandWithParameters`.

- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA –](../../data/oledb/cdynamicstringaccessora-class.md)a [CDynamicStringAccessorW –](../../data/oledb/cdynamicstringaccessorw-class.md) používají tyto třídy, pokud neznáte žádné znalosti schématu databáze. `CDynamicStringAccessorA` načítá data jako řetězce ANSI; `CDynamicStringAccessorW` načítá data jako řetězce Unicode.

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) S touto třídou můžete použít libovolné typy dat, které chcete, pokud poskytovatel může typ převést. Zpracovává jak sloupce výsledků, tak parametry příkazu.

Následující tabulka shrnuje podporu v OLE DB typy přistupujícího objektu šablony.

|Typ přístupového objektu|Dynamické|Zpracovává parametry.|Buffer|Více přístupových objektů|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|Ne|Ano|Uživatel|Ano|
|`CDynamicAccessor`|Ano|Ne|Šablony OLE DB|Ne|
|`CDynamicParameterAccessor`|Ano|Ano|Šablony OLE DB|Ne|
|`CDynamicStringAccessor[A,W]`|Ano|Ne|Šablony OLE DB|Ne|
|`CManualAccessor`|Ano|Ano|Uživatel|Ano|

## <a name="rowset-types"></a>Typy sady řádků

Šablony OLE DB podporují tři druhy sad řádků (viz předchozí obrázek): jednoduché sady řádků (implementované pomocí [CRowset](../../data/oledb/crowset-class.md)), hromadné sady řádků (implementované pomocí [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) a sady řádků pole (implementované [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Jednoduché sady řádků načítají jeden popisovač řádku při volání `MoveNext`. Hromadné sady řádků mohou načíst více popisovačů řádků. Sady řádků pole jsou sady řádků, ke kterým lze přistupovat pomocí syntaxe pole.

Následující obrázek ukazuje typy sady řádků.

![Obrázek RowsetType](../../data/oledb/media/vcrowsettypes.gif "Obrázek RowsetType")<br/>
Třídy sady řádků

[Sady řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) přistupují k datům v úložišti dat, ale místo toho mají přístup k informacím o úložišti dat, nazývaném metadata. Sady řádků schématu jsou obvykle používány v situacích, ve kterých není struktura databáze známá v době kompilace a musí být získána za běhu.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)
