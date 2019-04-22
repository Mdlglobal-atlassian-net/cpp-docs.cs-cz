---
title: Datoví členové stavu pole v přístupových objektech generovaných průvodcem
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: dd650b7cafef78e23c23ddfef791c88b6b93727f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025069"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Datoví členové stavu pole v přístupových objektech generovaných průvodcem

Při použití **průvodce příjemcem ATL OLE DB** vytvořte příjemce, vygeneruje průvodce datový člen třídy uživatelského záznamu pro každé pole, které jste zadali v mapě sloupců. Každý datový člen je typu `DWORD` a obsahuje stav hodnota odpovídající jeho odpovídající pole.

Například pro datový člen *m_OwnerID*, průvodce vygeneruje další datové členy stavu pole (*dwOwnerIDStatus*) a jinou pro délky pole (*dwOwnerIDLength*). Také vygeneruje mapu sloupců s COLUMN_ENTRY_LENGTH_STATUS položky.

To je ukázáno v následujícím kódu:

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

    DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
    SELECT \
        AuID, \
        Author, \
        YearBorn \
        FROM dbo.Authors")

    BEGIN_COLUMN_MAP(CAuthorsAccessor)
       COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
       COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
    END_COLUMN_MAP()
...
```

> [!NOTE]
> Pokud změníte název třídy záznamu uživatele nebo napsat vlastní příjemce, datových proměnných musí předcházet proměnné stavu a délky.

Můžete použít hodnoty stavu pro účely ladění. Pokud kód vytvořen **průvodce příjemcem ATL OLE DB** generuje chyby kompilace, jako je například DB_S_ERRORSOCCURRED nebo DB_E_ERRORSOCCURRED, měli byste nejdříve zkusit na aktuální hodnoty datoví členové stavu pole. Ty, které obsahují nenulové hodnoty odpovídají sloupcům problematické.

Hodnoty stavu můžete použít také k nastavení hodnoty NULL pro určité pole. To vám pomůže v případech, ve kterých chcete odlišit hodnotu pole jako hodnotu NULL, spíše než nula. Je jenom na vás rozhodnout, zda je platná hodnota nebo hodnota NULL a rozhodnout, jak vaše aplikace bude pracovat. OLE DB definuje DBSTATUS_S_ISNULL jako správný způsob určení na obecné hodnotě NULL. Pokud příjemce čte data a hodnota je null, pole stavu nastavená na DBSTATUS_S_ISNULL. Pokud uživatel chce nastavit hodnotu NULL, příjemce nastaví stav hodnotu DBSTATUS_S_ISNULL před voláním metody zprostředkovatele.

Dále otevřete Oledb.h a vyhledejte DBSTATUSENUM. Pak můžete porovnat číselnou hodnotu nenulovou stavu proti DBSTATUSENUM hodnot výčtu. Pokud název výčtu nestačí říct, co je špatně, přečtěte si téma **stav** tématu **vazby hodnoty dat** část [Příručka programátora technologie OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Toto téma obsahuje tabulky stav hodnot použitá při načtení nebo nastavení data. Informace o délce hodnot najdete v tématu **délka** tématu ve stejném oddílu.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Načítání délku nebo stav sloupce

Můžete získat délku sloupce s proměnlivou délkou nebo stav sloupce (Chcete-li zkontrolovat DBSTATUS_S_ISNULL, například):

- Chcete-li získat délku, použijte COLUMN_ENTRY_LENGTH – makro.

- Pokud chcete získat stav, použijte COLUMN_ENTRY_STATUS – makro.

- Obě získáte pomocí COLUMN_ENTRY_LENGTH_STATUS, jak je znázorněno:

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- Jak je znázorněno pak přístup k délku a/nebo stav:

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

Při použití `CDynamicAccessor`, délku a stav je vázána pro vás automaticky. Chcete-li načíst hodnoty délky a stavu, použijte `GetLength` a `GetStatus` členské funkce.

## <a name="see-also"></a>Viz také:

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)