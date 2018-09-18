---
title: Přístupové objekty a sady řádků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f8dc681e149d54742e4bf5e7ff44afeebe2292eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113094"
---
# <a name="accessors-and-rowsets"></a>Přístupové objekty a sady řádků

K nastavení a načtení dat, použijte šablony technologie OLE DB přístupový objekt a sady řádků prostřednictvím [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) třídy. Tato třída dokáže zpracovat víc přístupových objektů různých typů.  
  
## <a name="accessor-types"></a>Typy přístupového objektu  

Všechny přistupující objekty jsou odvozeny z [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase` poskytuje parametr a vazba sloupce.  
  
Následující obrázek znázorňuje typy přístupového objektu.  
  
![Typy přístupového objektu](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")  
Přístupový objekt třídy  
  
- [CAccessor –](../../data/oledb/caccessor-class.md) použijte tento přistupující objekt, když víte struktury zdroje databáze v době návrhu. `CAccessor` staticky váže záznam v databázi, která obsahuje vyrovnávací paměti, ke zdroji dat.  
  
- [CDynamicAccessor –](../../data/oledb/cdynamicaccessor-class.md) použijte tento přistupující objekt, pokud si nejste jisti struktura databáze v době návrhu. `CDynamicAccessor` volání `IColumnsInfo::GetColumnInfo` zobrazíte informace o sloupci databáze. Vytvoří a spravuje přistupující objekt a vyrovnávací paměti.  
  
- [CDynamicParameterAccessor –](../../data/oledb/cdynamicparameteraccessor-class.md) použijte tento přistupující objekt zpracovat Neznámý příkaz typy. Při přípravě příkazy `CDynamicParameterAccessor` můžete získat informace o parametru od `ICommandWithParameters` rozhraní, pokud zprostředkovatel podporuje `ICommandWithParameters`.  
  
- [CDynamicStringAccessor –](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md), a [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) použití těchto tříd, když nemají žádné informace o schématu databáze. `CDynamicStringAccessorA` načte data jako řetězce ANSI; `CDynamicStringAccessorW` načte data jako řetězce Unicode.  
  
- [CManualAccessor –](../../data/oledb/cmanualaccessor-class.md) pomocí této třídy, můžete použít libovolné datové typy, je-li poskytovatele můžete převést typ. Zpracovává sloupce výsledku a parametry příkazu.  
  
Následující tabulka shrnuje podporu typy přístupového objektu šablony technologie OLE DB.  
  
|Typ přístupového objektu|Dynamické|Zpracovává parametry|Vyrovnávací paměti|Několik přístupových objektů|  
|-------------------|-------------|--------------------|------------|------------------------|  
|`CAccessor`|Ne|Ano|Uživatel|Ano|  
|`CDynamicAccessor`|Ano|Ne|Šablony OLE DB|Ne|  
|`CDynamicParameterAccessor`|Ano|Ano|Šablony OLE DB|Ne|  
|`CDynamicStringAccessor[A,W]`|Ano|Ne|Šablony OLE DB|Ne|  
|`CManualAccessor`|Ano|Ano|Uživatel|Ano|  
  
## <a name="rowset-types"></a>Typy sady řádků  

Šablony technologie OLE DB podporují tři druhy sad řádků (viz předchozí obrázek): jednoduché sady řádků (implementované [CRowset](../../data/oledb/crowset-class.md)), hromadné sady řádků (implementované [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) a pole (implementováno sady řádků podle [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Jeden řádek zpracování při načtení jednoduché sady řádků `MoveNext` je volána. Hromadné sady řádků můžete načíst více popisovačů řádků. Sady řádků v polích jsou sady řádků, které lze přistupovat pomocí syntaxe pole.  
  
Následující obrázek znázorňuje typy sady řádků.  
  
![Obrázek %{rowsettype/](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")  
Třídy sady řádků  
  
[Sady řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) proveďte není přístup k datům v data ukládat, ale místo toho přístup k informacím o úložišti dat označovaném jako metadata. Sady řádků schématu se obvykle používá v situacích, ve kterých struktura databáze není v době kompilace znám a musí být získány v době běhu.  
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)