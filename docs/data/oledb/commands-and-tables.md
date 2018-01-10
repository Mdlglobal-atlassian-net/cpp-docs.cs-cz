---
title: "Příkazy a tabulky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c42422c156a51cac161f0cc75dfd1947b92eb20e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="commands-and-tables"></a>Příkazy a tabulky
Příkazy a tabulky umožňují přístup sady řádků; To znamená otevřete sady řádků, spuštěním příkazů a navázat sloupce. [CCommand](../../data/oledb/ccommand-class.md) a [CTable](../../data/oledb/ctable-class.md) třídy vytváření instancí objektů příkazu a tabulky, v uvedeném pořadí. Tyto třídy jsou odvozeny od [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) jak je znázorněno na následujícím obrázku.  
  
 ![CCommand a CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
Příkaz a tabulka třídy  
  
 V předchozí tabulce `TAccessor` může být jakéhokoli typu přístupového objektu uvedený v [typy přistupujícího objektu](../../data/oledb/accessors-and-rowsets.md). *TRowset* může být jakýkoli typ řádků uvedený v [typy sady řádků](../../data/oledb/accessors-and-rowsets.md). *TMultiple* Určuje typ výsledku (jeden nebo více sadu výsledků).  
  
 [Průvodce příjemcem knihovny ATL technologie OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md) umožňuje určit, zda má objekt příkazu nebo tabulky.  
  
-   Pro zdroje dat bez příkazy, můžete použít `CTable` třídy. Obvykle použijete ji pro jednoduché sady řádků, který zadejte žádné parametry a vyžadují žádné více výsledků. Tato třída jednoduchých otevře tabulky ve zdroji dat pomocí názvu tabulky, který určíte.  
  
-   Pro zdroje dat, které podporují příkazy, můžete použít `CCommand` třídy místo. K provedení příkazu, volání [otevřete](../../data/oledb/ccommand-open.md) na této třídě. Jako alternativu můžete volat `Prepare` Příprava příkaz, který chcete spustit více než jednou.  
  
     **CCommand** má tři argumenty šablony: typ přístupového objektu typu řádků a výsledný typ (`CNoMultipleResults`, ve výchozím nastavení, nebo `CMultipleResults`). Pokud zadáte `CMultipleResults`, `CCommand` třídy podporuje **IMultipleResults** rozhraní a zpracovává více sad řádků. [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) příklad ukazuje způsob zpracování více výsledků.  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)