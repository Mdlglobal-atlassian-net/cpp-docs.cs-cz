---
title: Datoví členové stavu pole v přístupových objektech generovaných průvodcem
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 61ee867f664b6b0d885e35f6d58840b37ce322b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210909"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Datoví členové stavu pole v přístupových objektech generovaných průvodcem

::: moniker range="vs-2019"

Průvodce příjemcem OLE DB ATL není v aplikaci Visual Studio 2019 a novějších k dispozici. Tuto funkci můžete přesto přidat ručně. Další informace najdete v tématu [Vytvoření příjemce bez použití Průvodce](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Při vytváření příjemce pomocí **průvodce OLE DB příjemce ATL** vygeneruje průvodce datový člen v třídě záznamu uživatele pro každé pole, které zadáte v mapě sloupce. Každý datový člen je typu `DWORD` a obsahuje hodnotu stavu odpovídající příslušnému poli.

Například pro datový člen *m_OwnerID*průvodce vygeneruje další datový člen pro stav pole (*dwOwnerIDStatus*) a druhý pro délku pole (*dwOwnerIDLength*). Také generuje mapu sloupce s položkami COLUMN_ENTRY_LENGTH_STATUS.

Zobrazuje se v následujícím kódu:

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
> Pokud upravíte třídu záznamu uživatele nebo zapíšete vlastního příjemce, musí se datové proměnné nacházet před proměnnými stav a délka.

Hodnoty stavu můžete použít pro účely ladění. Pokud kód generovaný **průvodcem OLE DB příjemce ATL** generuje chyby kompilace, například DB_S_ERRORSOCCURRED nebo DB_E_ERRORSOCCURRED, měli byste se nejprve podívat na aktuální hodnoty datových členů stavu pole. Ty, které mají nenulové hodnoty, odpovídají problematickým sloupcům.

Hodnoty stavu můžete použít také k nastavení hodnoty NULL konkrétního pole. To vám pomůže v případech, kdy chcete odlišit hodnotu pole jako hodnotu NULL, nikoli nula. Můžete se rozhodnout, jestli je NULL platnou hodnotou nebo speciální hodnotou a rozhodnout, jak ji má aplikace zpracovat. OLE DB definuje DBSTATUS_S_ISNULL jako správný způsob určení obecné hodnoty NULL. Pokud příjemce čte data a hodnota je null, pole stav je nastaveno na DBSTATUS_S_ISNULL. Pokud chce příjemce nastavit hodnotu NULL, příjemce nastaví hodnotu stavu na DBSTATUS_S_ISNULL před voláním zprostředkovatele.

Pak otevřete OLEDB. h a vyhledejte DBSTATUSENUM. Pak můžete porovnat číselnou hodnotu nenulového stavu s hodnotami výčtu DBSTATUSENUM. Pokud název výčtu není dostačující, abychom vám sdělili, co je chybné, přečtěte si téma **stav** v části **hodnoty dat vazby** v [příručce OLE DB Programmer 's Guide](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Toto téma obsahuje tabulky hodnot stavu používaných při získávání nebo nastavování dat. Informace o délkových hodnotách naleznete v tématu **Length (délka** ) ve stejné části.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Načtení délky nebo stavu sloupce

Můžete načíst délku sloupce s proměnlivou délkou nebo stav sloupce (pro kontrolu DBSTATUS_S_ISNULL například):

- Chcete-li získat délku, použijte makro COLUMN_ENTRY_LENGTH.

- Chcete-li získat stav, použijte makro COLUMN_ENTRY_STATUS.

- K získání obou použijte COLUMN_ENTRY_LENGTH_STATUS, jak je znázorněno níže:

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

- Pak přejděte na délku a/nebo stav, jak je znázorněno níže:

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

Když použijete `CDynamicAccessor`, bude se pro vás automaticky svázat délka a stav. Pro načtení hodnot Length a status použijte členské funkce `GetLength` a `GetStatus`.

::: moniker-end

## <a name="see-also"></a>Viz také

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
