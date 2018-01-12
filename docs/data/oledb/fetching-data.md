---
title: "Načítání dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b18847666d4f0f57d23e9b179e3e186a1b3ff736
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fetching-data"></a>Načítání dat
Po otevření zdroj dat, relace a objektu sady řádků, můžete načíst data. V závislosti na typu přistupujícího objektu, který používáte může být potřeba navázat sloupce.  
  
### <a name="to-fetch-data"></a>Pro načtení dat.  
  
1.  Otevřete sadu řádků pomocí odpovídající **otevřete** příkaz.  
  
2.  Pokud používáte `CManualAccessor`, vazby výstupní sloupce, pokud jste tak již neučinili. Chcete-li vytvořit vazbu sloupce, volejte `GetColumnInfo`a poté vytvořit přistupující objekt s vazbami, jak je znázorněno v následujícím příkladu:  
  
    ```  
    // From the DBViewer Sample CDBTreeView::OnQueryEdit  
    // Get the column information  
    ULONG ulColumns       = 0;  
    DBCOLUMNINFO* pColumnInfo  = NULL;  
    LPOLESTR pStrings      = NULL;  
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)  
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);  
    struct MYBIND* pBind = new MYBIND[ulColumns];  
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);  
    for (ULONG l=0; l<ulColumns; l++)  
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);  
    rs.Bind();  
    ```  
  
3.  Zápis `while` smyčky načíst data. Ve smyčce, volání `MoveNext` posunutí kurzoru a otestovat návratovou hodnotu S_OK, jak je znázorněno v následujícím příkladu:  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  V rámci `while` smyčky, může načíst data podle typu Vašeho přistupujícího objektu.  
  
    -   Pokud použijete [CAccessor](../../data/oledb/caccessor-class.md) třída, byste měli mít záznam uživatele, který obsahuje datové členy. Dostanete svá data pomocí těchto datových členů, jak je znázorněno v následujícím příkladu:  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   Pokud použijete `CDynamicAccessor` nebo `CDynamicParameterAccessor` třídu, můžete načíst data pomocí funkce přístupem `GetValue` a `GetColumn`, jak je znázorněno v následujícím příkladu. Pokud chcete určit typ dat, kterou používáte, použijte `GetType`.  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the dynamic accessor functions to retrieve your data.  
  
            ULONG ulColumns = rs.GetColumnCount();  
            for (ULONG i=0; i<ulColumns; i++)  
            {  
                rs.GetValue(i);  
            }  
        }  
        ```  
  
    -   Pokud používáte `CManualAccessor`, musíte zadat vlastní datové členy, vazby sami a přistupovat k nim přímo, jak je znázorněno v následujícím příkladu:  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)