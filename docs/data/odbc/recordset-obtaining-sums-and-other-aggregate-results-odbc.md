---
title: 'Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: 9ebbe78191d0c4140baf3557637ba2103886577d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368658"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje, jak získat souhrnné výsledky pomocí následujících klíčových slov [SQL:](../../data/odbc/sql.md)

- **SOUČET** Vypočítá součet hodnot ve sloupci s číselným datovým typem.

- **MIN** Extrahuje nejmenší hodnotu ve sloupci s číselným datovým typem.

- **MAX** Extrahuje největší hodnotu ve sloupci s číselným datovým typem.

- **Avg** Vypočítá průměrnou hodnotu všech hodnot ve sloupci s číselným datovým typem.

- **POČET** Spočítá počet záznamů ve sloupci libovolného datového typu.

Tyto funkce SQL slouží k získání statistických informací o záznamech ve zdroji dat, nikoli k extrahování záznamů ze zdroje dat. Sada záznamů, která je vytvořena, se obvykle skládá z jednoho záznamu (pokud jsou všechny sloupce agregace), který obsahuje hodnotu. (Pokud jste použili klauzuli **GROUP BY,** může existovat více než jeden záznam.) Tato hodnota je výsledkem výpočtu nebo extrakce prováděné funkcí SQL.

> [!TIP]
> Chcete-li přidat **klauzuli** SQL GROUP BY (a případně **klauzuli HAVING)** `m_strFilter`do příkazu SQL, přidejte ji na konec . Příklad:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Počet záznamů, které používáte k získání souhrnných výsledků, můžete omezit filtrováním a řazením sloupců.

> [!CAUTION]
> Některé operátory agregace vrátit jiný datový typ ze sloupců, přes které jsou agregace.

- **SUMA** a **AVG** může vrátit další větší datový `int` typ (například volání s vrátí **LONG** nebo **double).**

- **COUNT** obvykle vrátí **long** bez ohledu na typ cílového sloupce.

- **MAX** a **MIN** vrátí stejný datový typ jako sloupce, které vypočítají.

     Například průvodce **přidáním třídy** vytvoří `long` `m_lSales` tak, aby vyhovoval sloupci `double m_dblSumSales` Prodej, ale je třeba jej nahradit datovým členem, aby se přizpůsobil agregovanému výsledku. Prohlédněte si následující příklad.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Chcete-li získat souhrnný výsledek pro sadu záznamů

1. Vytvořte sadu záznamů, jak je popsáno v [přidání příjemce knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) obsahující sloupce, ze kterých chcete získat souhrnné výsledky.

1. Upravte funkci [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) pro sadu záznamů. Nahraďte řetězec představující název sloupce (druhý argument volání funkce [RFX)](../../data/odbc/record-field-exchange-using-rfx.md) řetězcem představujícím funkci agregace ve sloupci. Například nahraďte:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     textem:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Otevřete sadu záznamů. Výsledek operace agregace je ponechán `m_dblSumSales`v .

> [!NOTE]
> Průvodce ve skutečnosti přiřadí názvy datových členů bez maďarských předpon. Průvodce by například `m_Sales` vytvořil pro sloupec Prodej, `m_lSales` nikoli název použitý dříve pro ilustraci.

Pokud používáte [cRecordView](../../mfc/reference/crecordview-class.md) třídy k zobrazení dat, je třeba změnit volání funkce DDX pro zobrazení nové hodnoty datového člena; v tomto případě, změna z:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

Do:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
