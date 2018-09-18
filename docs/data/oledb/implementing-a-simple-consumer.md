---
title: Implementace jednoduchého příjemce | Dokumentace Microsoftu
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
ms.openlocfilehash: 681aa3ef5a1434ab191854f23a9e7bc908b65728
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082414"
---
# <a name="implementing-a-simple-consumer"></a>Implementace jednoduchého příjemce

Následující témata ukazují, jak upravit soubory vytvořené pomocí Průvodce aplikací knihovny MFC a průvodce příjemcem ATL OLE DB, vytvoření jednoduchého příjemce. V tomto příkladu má následující části:  
  
- "Načítání dat pomocí příjemce" ukazuje, jak implementovat kód v příjemci, který načte všechna data, řádek po řádku z databázové tabulky.  
  
- "Přidání podpory záložek příjemci" ukazuje, jak přidat podporu záložky příjemci.  
  
- "Přidání podpory jazyka XML příjemci" ukazuje, jak upravit uživatelský kód pro výstup dat načtení sady řádků jako XML data.  
  
> [!NOTE]
>  Aplikace příjemce popsané v této části můžete použít k testování ukázkové zprostředkovatele MyProv a poskytovatele.  
  
> [!NOTE]
>  Jak vytvořit webovou aplikaci otestovat MyProv příjemce (stejný zprostředkovatel je popsáno v [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)), musí obsahovat podporu záložku, jak je popsáno v "Přidání podpory záložek příjemci".  
  
> [!NOTE]
>  Jak vytvořit aplikaci příjemce otestujte, vynechte podpora záložek podle "Přidání záložky podporují příjemci" a přeskočte k "Přidání podpory XML příjemci".  
  
## <a name="retrieving-data-with-the-consumer"></a>Načítání dat pomocí příjemce  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Chcete-li změnit konzolovou aplikaci pro použití příjemce technologie OLE DB  
  
1. V MyCons.cpp změníte hlavní kód vložením tučným písmem následujícím způsobem:  
  
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
  
## <a name="adding-bookmark-support-to-the-consumer"></a>Přidání podpory záložek příjemci  

Záložka je sloupec, který jednoznačně identifikuje řádky v tabulce. Obvykle je klíčový sloupec, ale ne vždy; je specifický pro zprostředkovatele. Tato část ukazuje, jak přidat podporu záložky. Uděláte to tak, musíte provést následující akce v třídě záznam uživatele:  
  
- Vytvoření instance záložky. Jedná se o objekty typu [CBookmark](../../data/oledb/cbookmark-class.md).  
  
- Požádat o sloupec záložky v poskytovateli nastavením `DBPROP_IRowsetLocate` vlastnost.  
  
- Přidání položky záložky v mapování sloupců s použitím [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) – makro.  
  
V předchozích krocích vám poskytnou podporu záložky a objektu záložky, se kterým chcete pracovat. Tento příklad kódu ukazuje záložku, následujícím způsobem:  
  
- Otevřete soubor pro zápis.  
  
- Sada řádků výstupní data do souboru po řádcích.  
  
- Přesunout kurzor řádků na záložku voláním [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).  
  
- Výstup označenou záložkou a doplňujte řádek připojení na konec souboru.  
  
> [!NOTE]
>  Pokud pomocí této aplikace uživatelů otestovat vzorovou aplikaci zprostředkovatele poskytovatele, vynechte podpora záložek, které jsou popsané v této části.  
  
#### <a name="to-instantiate-the-bookmark"></a>K vytvoření instance na záložku  
  
1. Přistupujícím objektu musí obsahovat objekt typu [CBookmark](../../data/oledb/cbookmark-class.md). *NSize* parametr určuje velikost vyrovnávací paměti záložek v bajtech (obvykle 4 pro platformy 32 bitů) a 8 pro 64bitové platformy. Přidejte následující deklarace na datové členy sloupců ve třídě záznam uživatele:  
  
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
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>Požádat o sloupec záložky od poskytovatele  
  
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
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Chcete-li přidat položky záložky a mapováním sloupců  
  
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
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>Použití záložku v hlavním kódu  
  
1. V souboru MyCons.cpp z konzolové aplikace, kterou jste předtím vytvořili změňte hlavní kód trochu odlišná. Pokud chcete používat záložky, hlavní kód potřebuje k vytvoření instance objektu své vlastní záložky (`myBookmark`); to je jiná záložka od přístupového objektu (`m_bookmark`).  
  
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
  
Další informace o záložkách najdete v tématu [pomocí záložky](../../data/oledb/using-bookmarks.md). Příklady záložky jsou také uvedeny v [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).  
  
## <a name="adding-xml-support-to-the-consumer"></a>Přidání podpory jazyka XML pro příjemce  

Jak je popsáno v [přístup k datům XML](../../data/oledb/accessing-xml-data.md), existují dva způsoby, jak načíst XML data ze zdroje dat: použití [CStreamRowset](../../data/oledb/cstreamrowset-class.md) nebo pomocí [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md). Tento příklad používá `CStreamRowset`, což je mnohem efektivnější, ale je třeba SQL Server 2000 spuštěná na počítači, na kterém je spuštěn této ukázkové aplikaci.  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>Chcete-li změnit třídu příkazu dědit z CStreamRowset  
  
1. V příjemce aplikaci, kterou jste dříve vytvořili, změňte vaše `CCommand` pro určení `CStreamRowset` jako třídu řádků následujícím způsobem:  
  
    ```cpp  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>Chcete-li změnit hlavní kód pro načítání a výstupní XML data  
  
1. V souboru MyCons.cpp z konzolové aplikace, kterou jste předtím vytvořili změňte hlavní kód takto:  
  
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