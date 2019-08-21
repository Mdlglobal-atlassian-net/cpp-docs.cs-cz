---
title: Implementace jednoduchého příjemce
ms.date: 08/19/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 2f290f2a17c51682c75fbc09118757e5fd12c4f7
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630754"
---
# <a name="implementing-a-simple-consumer"></a>Implementace jednoduchého příjemce

::: moniker range="vs-2019"

Průvodce příjemcem OLE DB ATL není v aplikaci Visual Studio 2019 a novějších k dispozici. Tuto funkci můžete přesto přidat ručně. Další informace najdete v tématu [Vytvoření příjemce bez použití Průvodce](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Následující témata ukazují, jak upravit soubory vytvořené **průvodcem aplikací knihovny MFC** a průvodcem **OLE DB příjemce ATL** pro vytvoření jednoduchého příjemce. Tento příklad má následující části:

- [Načítání dat s příjemcem](#retrieve) ukazuje, jak implementovat kód ve spotřebiteli, který čte všechna data, řádek po řádku, z tabulky databáze.

- [Přidání podpory záložek příjemci](#bookmark) ukazuje, jak přidat podporu záložky pro příjemce.

> [!NOTE]
> Pomocí aplikace příjemce popsané v této části můžete testovat `MyProv` poskytovatele a `Provider` Sample Providers.

> [!NOTE]
> Chcete-li vytvořit aplikaci příjemce k `MyProv` testování (stejný poskytovatel popsaný v tématu [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)), je nutné zahrnout podporu záložky, jak je popsáno v tématu [Přidání podpory záložky pro příjemce](#bookmark).

## <a name="retrieve" ></a>Načítání dat s příjemcem

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Postup úpravy konzolové aplikace pro použití OLE DB příjemce

1. V `MyCons.cpp`změňte hlavní kód vložením tučného textu následujícím způsobem:

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "pch.h" // "stdafx.h" in Visual Studio 2017 and earlier
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

## <a name="bookmark" ></a>Přidání podpory záložky pro příjemce

Záložka je sloupec, který jednoznačně identifikuje řádky v tabulce. Obvykle se jedná o klíčový sloupec, ale ne vždy. je specifický pro konkrétního poskytovatele. V této části se dozvíte, jak přidat podporu záložek. K tomu je třeba v rámci třídy záznamu uživatele provést následující kroky:

- Vytvořte instanci záložek. Jedná se o objekty typu [CBookmark](../../data/oledb/cbookmark-class.md).

- Vyžádejte od poskytovatele `DBPROP_IRowsetLocate` sloupec záložky nastavením vlastnosti.

- Přidejte položku záložky k mapě sloupce pomocí makra [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) .

Předchozí kroky poskytují podporu záložky a objekt záložky, se kterým chcete pracovat. Tento příklad kódu ukazuje záložku následujícím způsobem:

- Otevřete soubor pro zápis.

- Výstupní sada řádků data do řádku souboru podle řádku.

- Přesuňte kurzor sady řádků na záložku tím, že zavoláte [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).

- Vypíše výstup řádku s záložkou a připojí ho ke konci souboru.

> [!NOTE]
> Použijete-li tuto aplikaci příjemce k otestování `Provider` ukázkové aplikace poskytovatele, ponechte podporu záložky popsanou v této části.

### <a name="to-instantiate-the-bookmark"></a>Vytvoření instance záložky

1. Přistupující objekt musí uchovávat objekt typu [CBookmark](../../data/oledb/cbookmark-class.md). Parametr *nSize* určuje velikost vyrovnávací paměti záložky v bajtech (obvykle 4 pro 32 bitové platformy a 8 pro 64-bit Platforms). Přidejte následující deklaraci do datových členů sloupce v třídě záznamu uživatele:

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

### <a name="to-request-a-bookmark-column-from-the-provider"></a>Požadavek na sloupec záložky od poskytovatele

1. Do `GetRowsetProperties` metody ve třídě záznamu uživatele přidejte následující kód:

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Přidání položky záložky na mapu sloupců

1. Přidejte následující položku do mapy sloupce v třídě záznamu uživatele:

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>Použití záložky v hlavním kódu

1. `MyCons.cpp` V souboru z konzolové aplikace, kterou jste vytvořili dříve, změňte hlavní kód pro čtení následujícím způsobem. Chcete-li použít záložky, je nutné, aby hlavní kód vytvořil instanci svého vlastního`myBookmark`objektu Bookmark (); Jedná se o jinou záložku jako v přistupujícím objektu (`m_bookmark`).

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

Další informace o záložkách najdete v tématu [použití záložek](../../data/oledb/using-bookmarks.md). Příklady záložek jsou také zobrazeny v části [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).

::: moniker-end

## <a name="see-also"></a>Viz také:

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
