---
title: Načítají se Data | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1dca3cc2d51f0e165e9b17d9fe630752a427590f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339153"
---
# <a name="fetching-data"></a>Načítání dat
Po otevření zdroje dat, relace a rozhraní objektu sady řádků, můžete načíst data. V závislosti na typu přístupový objekt, který používáte můžete potřebovat pro vytvoření vazby sloupce.  
  
### <a name="to-fetch-data"></a>K načtení dat  
  
1.  Otevřete v sadě řádků pomocí odpovídající **otevřít** příkazu.  
  
2.  Pokud používáte `CManualAccessor`, vytvořit vazbu výstupní sloupce, pokud jste tak již neučinili. Chcete-li vytvořit vazbu sloupce, zavolejte `GetColumnInfo`a pak vytvořte přístupový objekt s vazbami, jak je znázorněno v následujícím příkladu:  
  
    ```cpp  
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
  
3.  Zápis `while` smyčky, aby se načetla data. Ve smyčce, volání `MoveNext` předem kurzor a otestovat návratová hodnota S_OK, jak je znázorněno v následujícím příkladu:  
  
    ```cpp  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  V rámci `while` smyčky, můžete načíst data podle typu přístupového objektu.  
  
    -   Pokud používáte [CAccessor](../../data/oledb/caccessor-class.md) třídy, měli byste mít záznam uživatele, který obsahuje datové členy. Dostanete svá data pomocí těchto datových členů, jak je znázorněno v následujícím příkladu:  
  
        ```cpp  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   Pokud používáte `CDynamicAccessor` nebo `CDynamicParameterAccessor` třídy, můžete načíst data pomocí funkce přístupu k `GetValue` a `GetColumn`, jak je znázorněno v následujícím příkladu. Pokud chcete určit typ dat používáte, použijte `GetType`.  
  
        ```cpp  
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
  
    -   Pokud používáte `CManualAccessor`, je nutné zadat vlastní datové členy, navázat je sami a k nim přistupovat přímo, jak je znázorněno v následujícím příkladu:  
  
        ```cpp  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)