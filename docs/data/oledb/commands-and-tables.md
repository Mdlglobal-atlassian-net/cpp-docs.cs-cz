---
title: Příkazy a tabulky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3d045035ad757286b30b4adecf2f04f4dfbfd25
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340192"
---
# <a name="commands-and-tables"></a>Příkazy a tabulky
Příkazy a tabulky umožňují přístup k sady řádků; To znamená otevřete sady řádků, spusťte příkazy a vytvořit vazbu sloupce. [CCommand](../../data/oledb/ccommand-class.md) a [CTable](../../data/oledb/ctable-class.md) třídy instance objektů příkazu a tabulky, v uvedeném pořadí. Tyto třídy odvozovat z [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) jak je znázorněno na následujícím obrázku.  
  
 ![CCommand – a CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
Příkaz a tabulka třídy  
  
 V předchozí tabulce `TAccessor` může být libovolný typ přístupového objektu uvedené v [typy přístupového objektu](../../data/oledb/accessors-and-rowsets.md). *TRowset* může být jakékoli sady řádků se objeví v [typy sady řádků](../../data/oledb/accessors-and-rowsets.md). *TMultiple* Určuje typ výsledku (jeden nebo více sada výsledků).  
  
 [Průvodce příjemcem ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md) umožňuje určit, zda má objekt příkazu nebo tabulky.  
  
-   Pro zdroje dat bez příkazy, můžete použít `CTable` třídy. Můžete obvykle použít pro jednoduché sady řádků, které určují žádné parametry a vyžadují žádné více výsledků. Tato jednoduchá třída otevře tabulku ve zdroji dat pomocí názvu tabulky, který zadáte.  
  
-   U zdrojů dat, které podporují příkazy můžete použít `CCommand` namísto třídy. Chcete-li spustit příkaz, zavolejte [otevřít](../../data/oledb/ccommand-open.md) na této třídě. Jako alternativu můžete volat `Prepare` Příprava příkaz, který chcete spustit více než jednou.  
  
     `CCommand` má tři argumenty šablony: typ přístupového objektu, typ sady řádků a typ výsledku (`CNoMultipleResults`, ve výchozím nastavení, nebo `CMultipleResults`). Pokud zadáte `CMultipleResults`, `CCommand` třídy podporuje `IMultipleResults` rozhraní a zpracovává více sad řádků. [DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) příklad ukazuje, jak zpracovat více výsledků.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)