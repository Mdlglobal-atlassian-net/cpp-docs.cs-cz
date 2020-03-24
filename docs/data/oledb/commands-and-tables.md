---
title: Příkazy a tabulky
ms.date: 11/19/2018
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
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211520"
---
# <a name="commands-and-tables"></a>Příkazy a tabulky

Příkazy a tabulky umožňují přístup k sadě řádků; To znamená, že otevřete sady řádků, spustí příkazy a sváže sloupce. Třídy [CCommand](../../data/oledb/ccommand-class.md) a [CTable](../../data/oledb/ctable-class.md) vytvářejí instance příkazů a objektů tabulky v uvedeném pořadí. Tyto třídy jsou odvozeny z [CAccessorRowset –](../../data/oledb/caccessorrowset-class.md) , jak je znázorněno na následujícím obrázku.

![CCommand a CTable](../../data/oledb/media/vccommandstables.gif "CCommand a CTable")<br/>
Třídy příkazů a tabulek

V předchozí tabulce může být `TAccessor` kterýkoli typ přistupujícího objektu, který je uvedený v [typech přístupových](../../data/oledb/accessors-and-rowsets.md)objektů. `TRowset` může být libovolný typ sady řádků uvedený v [typech sady řádků](../../data/oledb/accessors-and-rowsets.md). `TMultiple` určuje typ výsledku (jednu nebo více sad výsledků).

[Průvodce příjemcem OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) umožňuje určit, zda chcete objekt nebo objekt tabulky.

- Pro zdroje dat bez příkazů můžete použít třídu `CTable`. Obecně se používá pro jednoduché sady řádků, které neurčují žádné parametry a nevyžadují žádné vícenásobné výsledky. Tato jednoduchá třída otevře tabulku ve zdroji dat pomocí názvu tabulky, kterou zadáte.

- Pro zdroje dat, které podporují příkazy, můžete místo toho použít třídu `CCommand`. Chcete-li spustit příkaz, zavolejte [otevřít](../../data/oledb/ccommand-open.md) na této třídě. Alternativně můžete volat `Prepare` pro přípravu příkazu, který chcete spustit více než jednou.

   `CCommand` má tři argumenty šablony: typ přistupujícího objektu, typ sady řádků a typ výsledku (`CNoMultipleResults`, ve výchozím nastavení nebo `CMultipleResults`). Zadáte-li `CMultipleResults`, třída `CCommand` podporuje rozhraní `IMultipleResults` a zpracovává více sad řádků. Ukázka [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) ukazuje, jak zpracovat více výsledků.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)
