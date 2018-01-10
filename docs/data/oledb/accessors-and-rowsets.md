---
title: "Přístupové objekty a sady řádků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cf47597ac38ae2944fc41bd686552e5d15c96b39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accessors-and-rowsets"></a>Přístupové objekty a sady řádků
Nastavit a načíst data, používat šablony technologie OLE DB přistupující objekt a sadu řádků, prostřednictvím [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) třídy. Tato třída může zpracovávat několik přístupových objektů různých typů.  
  
## <a name="accessor-types"></a>Typy přistupujícího objektu  
 Všechny přístupové objekty jsou odvozeny od [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase`poskytuje parametr a vazba sloupce.  
  
 Následující obrázek znázorňuje typy přistupujícího objektu.  
  
 ![Typy přistupujícího objektu](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")  
Třídy přistupujícího objektu  
  
-   [CAccessor](../../data/oledb/caccessor-class.md) použijte tento přistupující objekt, když víte struktura zdroje databáze v době návrhu. `CAccessor`staticky váže záznam v databázi, která obsahuje vyrovnávací paměti, ke zdroji dat.  
  
-   [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) použijte tento přistupující objekt, pokud si nejste jisti struktura databáze v době návrhu. `CDynamicAccessor`volání `IColumnsInfo::GetColumnInfo` získat informace o sloupci databáze. Vytváří a spravuje přistupující objekt a vyrovnávací paměť.  
  
-   [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) použijte tento přistupující objekt pro zpracování Neznámý příkaz typy. Při přípravě příkazy, `CDynamicParameterAccessor` můžete získat informace o parametrech z `ICommandWithParameters` rozhraní, pokud zprostředkovatel podporuje `ICommandWithParameters`.  
  
-   [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md), a [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) použijte tyto třídy, když nemáte žádné informace o schématu databáze. `CDynamicStringAccessorA`načte data jako řetězce ANSI; `CDynamicStringAccessorW` načítá data jako řetězce Unicode.  
  
-   [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) s touto třídou, můžete použít libovolnou datové typy, je-li zprostředkovatel můžete převést typ. Zpracovává výsledek sloupců a parametry příkazu.  
  
 Následující tabulka shrnuje podporu v typy přistupujícího objektu šablony technologie OLE DB.  
  
|Typ přístupového objektu|dynamické|Zpracovává parametry|Vyrovnávací paměti|Několik přístupových objektů|  
|-------------------|-------------|--------------------|------------|------------------------|  
|`CAccessor`|Ne|Ano|Uživatel|Ano|  
|`CDynamicAccessor`|Ano|Ne|Šablony OLE DB|Ne|  
|`CDynamicParameterAccessor`|Ano|Ano|Šablony OLE DB|Ne|  
|`CDynamicStringAccessor[A,W]`|Ano|Ne|Šablony OLE DB|Ne|  
|`CManualAccessor`|Ano|Ano|Uživatel|Ano|  
  
## <a name="rowset-types"></a>Typy sady řádků  
 Šablony technologie OLE DB podporují tři druhy sady řádků (viz předchozí obrázek): jeden sady řádků (implementované [CRowset](../../data/oledb/crowset-class.md)), hromadné sady řádků (implementované [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) a pole (implementována sady řádků podle [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Načítání jednoduché sady řádků na jeden řádek zpracování při `MoveNext` je volána. Hromadné sady řádků můžete získat více popisovačů řádků. Sady řádků v polích jsou sady řádků, které je přístupné pomocí syntaxe pro pole.  
  
 Následující obrázek ukazuje typy sady řádků.  
  
 ![Obrázek %{rowsettype/](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")  
Třídy sady řádků  
  
 [Schéma sad řádků](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) nechcete přístup k datům v data ukládat, ale místo toho přístup k informacím o úložišti dat, který se nazývá metadata. Schéma sad řádků se obvykle používá v situacích, ve kterých není znám. v době kompilace struktura databáze a musí být získána za běhu.  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)