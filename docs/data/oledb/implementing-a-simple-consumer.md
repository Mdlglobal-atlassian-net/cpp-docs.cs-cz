---
title: Implementace jednoduchého příjemce
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 592a51dd77f7a2e115ee67a481e56dc558209253
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525072"
---
# <a name="implementing-a-simple-consumer"></a>Implementace jednoduchého příjemce

::: moniker range="vs-2019"

Průvodce spotřebitele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším. Funkce můžete přesto přidat ručně. Další informace najdete v tématu [vytvoření příjemce bez použití průvodce](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="vs-2017"

Následující témata ukazují, jak upravit soubory vytvořené **Průvodce aplikací knihovny MFC** a **průvodce příjemcem ATL OLE DB** k vytvoření jednoduchého příjemce. V tomto příkladu má následující části:

- [Načítání dat pomocí příjemce](#retrieve) ukazuje, jak implementovat kód v příjemci, který načte všechna data, řádek po řádku z databázové tabulky.

- [Přidání podpory záložky příjemci](#bookmark) ukazuje, jak přidat podporu záložky příjemci.

> [!NOTE]
> Aplikace příjemce popsané v této části můžete použít k testování `MyProv` a `Provider` ukázkový poskytovatelů.

> [!NOTE]
> Jak vytvořit aplikaci uživatelů otestovat `MyProv` (stejný zprostředkovatel je popsáno v [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)), musí obsahovat podporu záložku, jak je popsáno v [k přidání podpory záložek Příjemce](#bookmark).

## <a name="retrieve" ></a> Načítání dat pomocí příjemce

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Chcete-li změnit konzolovou aplikaci pro použití příjemce technologie OLE DB

1. V `MyCons.cpp`, změnit hlavní kód vložením tučným písmem následujícím způsobem:

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "stdafx.h"
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="bookmark" ></a> Přidání podpory záložek příjemci

Záložka je sloupec, který jednoznačně identifikuje řádky v tabulce. Obvykle je klíčový sloupec, ale ne vždy; je specifický pro zprostředkovatele. Tato část ukazuje, jak přidat podporu záložky. Uděláte to tak, musíte provést následující kroky v třídě záznamu uživatele:

- Vytvoření instance záložky. Jedná se o objekty typu [CBookmark](../../data/oledb/cbookmark-class.md).

- Požádat o sloupec záložky v poskytovateli nastavením `DBPROP_IRowsetLocate` vlastnost.

- Přidání položky záložky v mapování sloupců s použitím [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) – makro.

V předchozích krocích vám poskytnou podporu záložky a objektu záložky, se kterým chcete pracovat. Tento příklad kódu ukazuje záložku, následujícím způsobem:

- Otevřete soubor pro zápis.

- Sada řádků výstupní data do souboru po řádcích.

- Přesunout kurzor řádků na záložku voláním [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).

- Výstup označenou záložkou a doplňujte řádek připojení na konec souboru.

> [!NOTE]
> Pokud používáte k testování této aplikace příjemce `Provider` ukázkovou aplikaci zprostředkovatele, vynechte podpora záložek, které jsou popsané v této části.

### <a name="to-instantiate-the-bookmark"></a>K vytvoření instance na záložku

1. Přistupující objekt musí obsahovat objekt typu [CBookmark](../../data/oledb/cbookmark-class.md). *NSize* parametr určuje velikost vyrovnávací paměti záložek v bajtech (obvykle 4 pro platformy 32 bitů) a 8 pro 64bitové platformy. Přidejte následující deklarace na datové členy sloupců ve třídě záznam uživatele:

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>Požádat o sloupec záložky od poskytovatele

1. Přidejte následující kód `GetRowsetProperties` metody ve třídě záznamů uživatele:

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Chcete-li přidat položky záložky a mapováním sloupců

1. Přidejte následující položku do mapy sloupce ve třídě záznam uživatele:

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>Použití záložku v hlavním kódu

1. V `MyCons.cpp` soubor z konzolové aplikace dříve vytvořili, změňte hlavní kód trochu odlišná. Pokud chcete používat záložky, hlavní kód potřebuje k vytvoření instance objektu své vlastní záložky (`myBookmark`); to je jiná záložka od přístupového objektu (`m_bookmark`).

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

Další informace o záložkách najdete v tématu [pomocí záložky](../../data/oledb/using-bookmarks.md). Příklady záložky jsou také uvedeny v [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).

::: moniker-end

## <a name="see-also"></a>Viz také:

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
