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
ms.openlocfilehash: 38a458eb6634d5075315c9c0bbd2cb215bc76eda
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075907"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

V tomto tématu se dozvíte, jak získat agregované výsledky pomocí následujících klíčových slov [SQL](../../data/odbc/sql.md) :

- **Součet** Vypočítá celkový součet hodnot ve sloupci s číselným datovým typem.

- **Minimální** počet Extrahuje nejmenší hodnotu ve sloupci s číselným datovým typem.

- **Maximální počet** Extrahuje největší hodnotu ve sloupci s číselným datovým typem.

- **Průměrná doba** Vypočítá průměrnou hodnotu všech hodnot ve sloupci s číselným datovým typem.

- **Počet** Spočítá počet záznamů ve sloupci libovolného datového typu.

Tyto funkce SQL slouží k získání statistických informací o záznamech ve zdroji dat, nikoli k extrakci záznamů ze zdroje dat. Vytvořená sada záznamů se obvykle skládá z jednoho záznamu (pokud jsou všechny sloupce agregovany), který obsahuje hodnotu. (Pokud jste použili klauzuli **Group by** , může existovat více než jeden záznam.) Tato hodnota je výsledkem výpočtu nebo extrakce prováděná funkcí SQL.

> [!TIP]
>  Chcete-li přidat klauzuli SQL **Group by** (a případně klauzuli **having** ) do příkazu SQL, přidejte ji na konec `m_strFilter`. Příklad:

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

Pomocí filtrování a řazení sloupců můžete omezit počet záznamů, které používáte k získání agregovaných výsledků.

> [!CAUTION]
>  Některé agregační operátory vracejí jiný datový typ ze sloupců, na jejichž agregaci jsou agregovány.

- **Sum** a **AVG** mohou vracet další větší datový typ (například volání pomocí `int` vrátí **Long** nebo **Double**).

- **Počet** obvykle vrátí hodnotu **Long** bez ohledu na typ cílového sloupce.

- **Max** a **min** vrátí stejný datový typ jako vypočítané sloupce.

     Například Průvodce **přidáním třídy** vytvoří `long` `m_lSales` pro přizpůsobení sloupce Sales, ale je nutné jej nahradit datovým členem `double m_dblSumSales`, aby odpovídal agregovanému výsledku. Prohlédněte si následující příklad.

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Získání agregovaného výsledku pro sadu záznamů

1. Vytvořte sadu záznamů, jak je popsáno v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) obsahující sloupce, ze kterých chcete získat agregované výsledky.

1. Upravte funkci [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) pro sadu záznamů. Nahraďte řetězec reprezentující název sloupce (druhý argument volání funkce [RFX](../../data/odbc/record-field-exchange-using-rfx.md) ) řetězcem, který představuje agregační funkci na sloupci. Například nahraďte:

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     textem:

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. Otevřete sadu záznamů. Výsledek operace agregace je ponechán v `m_dblSumSales`.

> [!NOTE]
>  Průvodce vlastně přiřadí názvy datových členů bez maďarské předpony. Průvodce by například vytvořil `m_Sales` pro sloupec Sales místo toho, aby název `m_lSales` používal dříve pro ilustraci.

Pokud k zobrazení dat používáte třídu [CRecordView](../../mfc/reference/crecordview-class.md) , je nutné změnit volání funkce DDX, aby se zobrazila nová hodnota datového členu. v takovém případě se změní z:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

Komu:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)