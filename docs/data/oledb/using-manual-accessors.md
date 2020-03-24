---
title: Použití ručních přístupových objektů
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: a6c0e5236702229a61a828344ba5d0d288898aee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209323"
---
# <a name="using-manual-accessors"></a>Použití ručních přístupových objektů

Při zpracování neznámého příkazu je třeba provést čtyři věci:

- Určení parametrů

- Provedení příkazu

- Určení výstupních sloupců

- Podívejte se, jestli existují vícenásobné návratové sady řádků.

Chcete-li provést tyto akce pomocí OLE DBch zákaznických šablon, použijte třídu `CManualAccessor` a postupujte podle těchto kroků:

1. Otevřete `CCommand` objekt `CManualAccessor` jako parametr šablony.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Zadejte dotaz na relaci rozhraní `IDBSchemaRowset` a použijte sadu řádků parametrů procedury. Pokud `IDBSchemaRowset` rozhraní není k dispozici, dotaz na rozhraní `ICommandWithParameters`. Pro informace zavolejte `GetParameterInfo`. Pokud není k dispozici žádné rozhraní, můžete předpokládat, že neexistují žádné parametry.

1. Pro každý parametr zavolejte `AddParameterEntry` pro přidání parametrů a jejich nastavení.

1. Otevřete sadu řádků, ale nastavte parametr vazby na **hodnotu false**.

1. Voláním `GetColumnInfo` načtěte výstupní sloupce. K přidání výstupního sloupce do vazby použijte `AddBindEntry`.

1. Zavolejte `GetNextResult` k určení, zda jsou k dispozici více sad řádků. Opakujte kroky 2 až 5.

Příklad ručního přístupového objektu naleznete v tématu `CDBListView::CallProcedure` v ukázce [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
