---
title: Použití ručních přístupových objektů
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 8b969b7bb939d8e7d2217234795b564e8d137208
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651760"
---
# <a name="using-manual-accessors"></a>Použití ručních přístupových objektů

Existují čtyři kroky, které při zpracování Neznámý příkaz:

- Určuje parametry

- Spusťte příkaz

- Určení výstupní sloupce

- Zkontrolujte, jestli více vrácení sad řádků

Chcete-li to všechno s šablony příjemce technologie OLE DB, použijte `CManualAccessor` třídy a postupujte podle těchto kroků:

1. Otevřít `CCommand` objekt s `CManualAccessor` jako parametr šablony.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Dotaz na relaci `IDBSchemaRowset` rozhraní a používat parametry procedury sady řádků. Pokud `IDBSchemaRowset` rozhraní není k dispozici, dotázat `ICommandWithParameters` rozhraní. Volání `GetParameterInfo` informace. Pokud je k dispozici žádná rozhraní, můžete předpokládat, že neexistují žádné parametry.

1. Pro každý parametr volání `AddParameterEntry` přidat parametry a jejich nastavení.

1. Otevřít v sadě řádků, ale nastavit vazbu parametru **false**.

1. Volání `GetColumnInfo` načíst výstupní sloupce. Použití `AddBindEntry` Přidat výstupní sloupec do vazby.

1. Volání `GetNextResult` k určení, zda jsou k dispozici více sad řádků. Opakujte kroky 2 až 5.

Příklad ruční přistupujícího objektu, najdete v části `CDBListView::CallProcedure` v [DBVIEWER](https://github.com/Microsoft/VCSamples) vzorku.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)