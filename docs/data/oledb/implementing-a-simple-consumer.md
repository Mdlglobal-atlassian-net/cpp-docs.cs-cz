---
title: Implementace jednoduchého příjemce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 841d982090503a1e72b1d6798a5f0eecdb543fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-a-simple-consumer"></a>Implementace jednoduchého příjemce
Následující témata ukazují, jak upravit soubory vytvořené Průvodce aplikací knihovny MFC a průvodce příjemcem knihovny ATL technologie OLE DB pro vytvoření jednoduchého příjemce. V tomto příkladu má následující části:  
  
-   "Načítání dat pomocí příjemce" ukazuje, jak pro implementaci kódu v příjemci, který načte všechna data po řádcích z databázové tabulky.  
  
-   "Přidání podpory záložky k příjemce" ukazuje, jak přidat podporu záložky k příjemce.  
  
-   "Přidání podpory jazyka XML k příjemce" ukazuje, jak změnit kód příjemce, můžete data načtená řádků jako XML data.  
  
> [!NOTE]
>  Aplikaci příjemce, které jsou popsané v této části můžete použít k testování ukázkové zprostředkovatele MyProv a zprostředkovatele.  
  
> [!NOTE]
>  Chcete-li sestavit aplikaci příjemce, abyste otestovali MyProv (stejný zprostředkovatel popsané v [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)), musí obsahovat podpora záložek, jak je popsáno v "Přidání podpory záložky k příjemce".  
  
> [!NOTE]
>  K vytvoření aplikace příjemce k testování zprostředkovatele, vynechte podpora záložek popsané v "Přidávání záložek podporují příjemci" a přejít na "Přidání podpory XML příjemci".  
  
## <a name="retrieving-data-with-the-consumer"></a>Načítání dat pomocí příjemce  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Chcete-li upravit aplikaci konzoly, aby používala příjemce technologie OLE DB  
  
1.  V MyCons.cpp změňte kód hlavní vložením bold text následujícím způsobem:  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
 HRESULT hr = CoInitialize(NULL);   // Instantiate rowset   CProducts rs;   hr = rs.OpenAll();   ATLASSERT(SUCCEEDED(hr ) );   hr = rs.MoveFirst();   // Iterate through the rowset   while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row      printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",             rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );      hr = rs.MoveNext();   }   rs.Close();   rs.ReleaseCommand();   CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="adding-bookmark-support-to-the-consumer"></a>Přidání podpory záložky k příjemce  
 Záložka je sloupec, který jednoznačně identifikuje řádky v tabulce. Obvykle je sloupec klíče, ale ne vždy; je specifický pro zprostředkovatele. V této části se dozvíte, jak přidat podporu záložky. To pokud chcete udělat, musíte udělat následující ve třídě záznam uživatele:  
  
-   Vytvořit instanci záložky. Jedná se o objekty typu [CBookmark](../../data/oledb/cbookmark-class.md).  
  
-   Požádat o sloupec záložky od zprostředkovatele nastavením **DBPROP_IRowsetLocate** vlastnost.  
  
-   Přidání položky záložky do mapy sloupce s použitím [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) makro.  
  
 Předchozí kroky poskytují podpora záložek a objekt záložku, se kterým chcete pracovat. Tento příklad kódu ukazuje záložku takto:  
  
-   Otevření souboru pro zápis.  
  
-   Výstupní data řádků do souboru po řádcích.  
  
-   Přesunutí kurzoru řádků na záložku voláním [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).  
  
-   Výstup řádek označený záložkou připojen na konec souboru.  
  
> [!NOTE]
>  Pokud použijete tuto aplikaci příjemce k testování zprostředkovatele zprostředkovatele ukázkovou aplikaci, vynechte podpora záložek popsaných v této části.  
  
#### <a name="to-instantiate-the-bookmark"></a>Chcete-li vytvořit instanci záložky  
  
1.  Přistupující objekt musí obsahovat objekt typu [CBookmark](../../data/oledb/cbookmark-class.md). `nSize` Parametr určuje velikost vyrovnávací paměti záložky v bajtech (obvykle 4 pro 32bitovou platformu) a 8 pro 64bitové platformy. Přidejte následující deklarace sloupec datových členů v třídě záznam uživatele:  
  
    ```  
    //////////////////////////////////////////////////////////////////////  
    // Products.h  
    class CProductsAccessor  
    {  
    public:  
       CBookmark<4> m_bookmark;   // Add bookmark declaration  
       LONG m_ProductID;  
       ...  
    ```  
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>K žádosti o sloupec záložky od zprostředkovatele  
  
1.  Přidejte následující kód v `GetRowsetProperties` metodu v třídě záznamů uživatele:  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Chcete-li přidat položky záložky do mapy sloupce  
  
1.  Přidejte následující položku na mapu sloupce ve třídě záznam uživatele:  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>Chcete-li používat záložky v hlavním kódu  
  
1.  V souboru MyCons.cpp z konzolové aplikace, které jste vytvořili změňte hlavní kód tímto. Použití záložek, kód hlavní musí vytvořit instanci vlastního objektu záložky (`myBookmark`); to je jiná záložka než v přistupujícího objektu (`m_bookmark`).  
  
    ```  
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
             myBookmark = rs.bookmark;  
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
  
 Další informace o záložky najdete v tématu [pomocí záložky](../../data/oledb/using-bookmarks.md). Příklady záložek jsou také uvedené v [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).  
  
## <a name="adding-xml-support-to-the-consumer"></a>Přidání podpory jazyka XML k příjemce  
 Jak je popsáno v [přístup k datům XML](../../data/oledb/accessing-xml-data.md), existují dva způsoby, jak načíst XML data ze zdroje dat: pomocí [CStreamRowset](../../data/oledb/cstreamrowset-class.md) nebo pomocí [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md). Tento příklad používá `CStreamRowset`, který je efektivnější, ale vyžaduje, abyste měli na počítači, na kterém spustíte této ukázkové aplikaci SQL Server 2000.  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>Chcete-li upravit třídu příkazu dědění z CStreamRowset  
  
1.  V aplikaci příjemce, který jste dříve vytvořili, změňte vaše `CCommand` deklarace k určení `CStreamRowset` jako třídu řádků takto:  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>Chcete-li upravit kód hlavní načíst a výstupní XML data  
  
1.  V souboru MyCons.cpp z konzolové aplikace, které jste vytvořili změňte hlavní kód tímto:  
  
    ```  
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
  
       // Add variable declarations for the Read method to handle sequential stream data  
       CHAR buffer[1001];  // Pointer to buffer into which data stream is read  
       ULONG cbRead;       // Actual number of bytes read from the data stream  
  
       hr = rs.OpenAll();  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // The following loop reads 1000 bytes of the data stream at a time   
       // until it reaches the end of the data stream  
       for (;;)  
       {  
          // Read sequential stream data into buffer  
    HRESULT hr = rs.m_spStream->Read(buffer, 1000, &cbRead);  
          if (FAILED (hr))  
             break;  
          // Output buffer to file  
          buffer[cbRead] = 0;  
          outfile << buffer;  
          // Test for end of data stream  
          if (cbRead < 1000)  
             break;  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)