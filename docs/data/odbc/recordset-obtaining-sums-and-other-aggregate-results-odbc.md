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
ms.openlocfilehash: 7a63e6b0e4ac26fb2806d8505e3fcd8f5daf0f10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491582"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak získat agregované výsledky, použijte tento [SQL](../../data/odbc/sql.md) klíčová slova:

- **Součet** vypočítá celkový součet hodnot ve sloupci s číselným datovým typem.

- **MIN** extrahuje nejmenší hodnotu ve sloupci s číselným datovým typem.

- **Maximální počet** extrahuje největší hodnotu ve sloupci s číselným datovým typem.

- **AVG** vypočítá průměrnou hodnotu ze všech hodnot ve sloupci s číselným datovým typem.

- **POČET** spočítá záznamy ve sloupci libovolného datového typu.

Statistické informace o záznamy ve zdroji dat, a nikoli k extrakci záznamy ze zdroje dat použijete tyto funkce jazyka SQL. Sada záznamů, který je vytvořen obvykle obsahuje jediný záznam (pokud jsou všechny sloupce agregace), který obsahuje hodnotu. (Může existovat více než jeden záznam. Pokud jste použili **Group** klauzule.) Tato hodnota je výsledek výpočtu nebo extrakce prováděné funkce SQL.

> [!TIP]
>  Přidat SQL **GROUP BY** klauzuli (a případně **HAVING** klauzule) Chcete-li příkazu jazyka SQL, přidejte na konec `m_strFilter`. Příklad:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Můžete omezit počet záznamů, které můžete použít k získání agregované výsledky pomocí filtrování a řazení sloupců.

> [!CAUTION]
>  Některé možné použít operátory agregace vrátí jiný datový typ ze sloupců, po které se agregace.

- **Součet** a **AVG** může vrátit další větší datový typ (například voláním s `int` vrátí **dlouhé** nebo **double**).

- **POČET** obvykle vrací **dlouhé** bez ohledu na typ cílového sloupce.

- **Maximální počet** a **MIN** vrátit stejný datový typ jako sloupce se vypočítat.

     Například **přidat třídu** Průvodce vytvoří `long` `m_lSales` tak, aby vyhovovaly sloupec prodeje, ale muset nahraďte ho názvem `double m_dblSumSales` datový člen tak, aby vyhovovaly agregované výsledky. Podívejte se na téma v následujícím příkladu.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Získat výsledek agregace pro sady záznamů

1. Vytvoření sady záznamů, jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) obsahující sloupce, ze kterých chcete získat agregovat výsledky.

1. Upravit [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkce pro sady záznamů. Nahraďte řetězec představující název sloupce (druhým argumentem [RFX](../../data/odbc/record-field-exchange-using-rfx.md) volání funkce) řetězcem, který představuje funkci agregace ve sloupci. Například nahraďte:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     Pomocí:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Otevřete sadu záznamů. Výsledek operace agregace je ponechán v `m_dblSumSales`.

> [!NOTE]
>  Průvodce přiřadí skutečně názvy datových členů bez maďarské předpony. Například byste mohli vytvořit průvodce `m_Sales` pro sloupec prodejní místo `m_lSales` název předtím použili pro ilustraci.

Pokud používáte [CRecordView](../../mfc/reference/crecordview-class.md) tříd – zobrazit data, budete muset změnit volání funkce DDX zobrazíte nové hodnoty datového člena; v takovém případě ji z změnit:

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