---
title: "Použití více přístupových objektů pro sadu řádků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 41f5ae4381dd2505b2136e796c1b8832eaa75246
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Použití více přístupových objektů pro sadu řádků
Existují tři základní scénáře, ve kterých budete muset použít několik přístupových objektů:  
  
-   **Více sad řádků pro čtení a zápis.** V tomto scénáři můžete mít tabulku s primární klíč. Chcete mít možnost číst všechny sloupce v řádku, včetně primární klíč. Chcete být schopni zapisovat data pro všechny sloupce kromě primárního klíče (protože nemůže zapisovat do sloupec primárního klíče). V takovém případě můžete nastavit dva přístupové objekty:  
  
    -   Přistupující objekt 0 obsahuje všechny sloupce.  
  
    -   Přistupující objekt 1 obsahuje všechny sloupce kromě primární klíč.  
  
-   **Výkon.** V tomto scénáři obsahovat jeden nebo více sloupců velké množství dat, například grafiky, zvuk nebo video soubory. Pokaždé, když přesunete na řádek, pravděpodobně nechcete načíst sloupec se souborem velkého množství dat, protože je to proto by zpomalit výkon aplikace.  
  
     Můžete nastavit samostatné přistupující objekty, ve kterých první přistupující objekt obsahuje všechny sloupce kromě toho s velkého množství dat a automaticky; načítá data z těchto sloupců Toto je automatický přistupující objekt. Druhý přistupující objekt načítá pouze se sloupcem obsahující velkého množství dat, ale nenačítá data z tohoto sloupce automaticky. Můžete mít další metody aktualizace nebo načítání velkých dat na vyžádání.  
  
    -   Přistupující objekt 0 je automatický přistupující objekt; načte všechny sloupce kromě toho s velkými datovými.  
  
    -   Přistupující objekt 1 není automatický přistupující objekt; načítá sloupec s velkými datovými.  
  
     Argument automaticky použijte k určení, zda je přistupující objekt automaticky.  
  
-   **Více sloupců ISequentialStream.** V tomto scénáři máte více než jeden sloupec obsahující `ISequentialStream` data. Každý přistupující objekt je však omezená na jedno `ISequentialStream` datového proudu. Pokud chcete tento problém vyřešit, nastavte několik přístupových objektů, každý obsahující jeden `ISequentialStream` ukazatel.  
  
 Obvykle vytvoříte přistupující objekty pomocí [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra. Můžete také [db_accessor](../../windows/db-accessor.md) atribut. (Přístupové objekty jsou popsány dále v [uživatelských záznamů](../../data/oledb/user-records.md).) Makra nebo atribut určete, zda přistupující objekt je automatický nebo přistupujícího objektu bez automaticky:  
  
-   V automatickém přistupujícím objektu přesunout metody **MoveFirst**, `MoveLast`, `MoveNext`, a `MovePrev` načíst data pro všechny sloupce zadané automaticky. Přistupující objekt 0 by měl být automatický přistupující objekt.  
  
-   V přistupujícím objektem bez automatické načtení není proběhnout, dokud nebude explicitně volání metody, jako **aktualizace**, **vložit**, **načíst**, nebo **odstranit**. Ve scénářích popsané výše nemusí chcete načíst všechny sloupce při každém přesunu. Můžete umístit jeden nebo více sloupců v samostatných přistupujícího objektu a je nutné zajistit splnění přistupujícím objektem bez automaticky, jak je uvedeno níže.  
  
 Následující příklad používá několik přístupových objektů číst a zapisovat do tabulky úlohy databázi systému SQL Server pubs použití více přístupových objektů. Toto je nejběžnější použití více přístupových objektů; viz výše "více sad řádků pro čtení a zápis" scénář.  
  
 Třídy uživatelského záznamu je následující. Nastavuje dva přistupující objekty: přistupující objekt 0 obsahuje pouze sloupec primárního klíče (ID) a přistupující objekt 1 obsahuje jiné sloupce.  
  
```  
class CJobs  
{  
public:  
    enum {  
        sizeOfDescription = 51  
    };  
  
    short nID;  
    char szDescription[ sizeOfDescription ];  
    short nMinLvl;  
    short nMaxLvl;  
  
    DWORD dwID;  
    DWORD dwDescription;  
    DWORD dwMinLvl;  
    DWORD dwMaxLvl;  
  
BEGIN_ACCESSOR_MAP(CJobs, 2)  
    // Accessor 0 is the automatic accessor  
    BEGIN_ACCESSOR(0, true)  
        COLUMN_ENTRY_STATUS(1, nID, dwID)  
    END_ACCESSOR()  
    // Accessor 1 is the non-automatic accessor  
    BEGIN_ACCESSOR(1, true)  
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)  
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)  
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)  
    END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
 Hlavní kód je následující. Volání metody `MoveNext` automaticky načte data z ID sloupec primárního klíče pomocí přistupující objekt 0. Poznámka: Jak **vložit** metoda téměř end používá přistupující objekt 1 předejdete zápis do sloupec primárního klíče.  
  
```  
int main(int argc, char* argv[])  
{  
    // Initalize COM  
    ::CoInitialize(NULL);  
  
    // Create instances of the data source and session  
    CDataSource source;  
    CSession session;  
    HRESULT hr = S_OK;  
  
    // Set initialization properties  
    CDBPropSet dbinit(DBPROPSET_DBINIT);  
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));  
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));  
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));  
  
    hr = source.Open("SQLOLEDB.1", &dbinit);  
    if (hr == S_OK)  
    {  
        hr = session.Open(source);  
        if (hr == S_OK)  
        {  
            // Ready to fetch/access data  
            CTable<CAccessor<CJobs>> jobs;  
  
            // Set properties for making the rowset a read/write cursor  
            CDBPropSet dbRowset(DBPROPSET_ROWSET);  
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);  
            dbRowset.AddProperty(DBPROP_UPDATABILITY,  
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |  
                DBPROPVAL_UP_DELETE);  
  
            hr = jobs.Open(session, "jobs", &dbRowset);  
            if (hr == S_OK)  
            {  
                // Calling MoveNext automatically retrieves ID  
                // (using accessor 0)  
                while(jobs.MoveNext() == S_OK)  
                   printf_s("Description = %s\n", jobs.szDescription);  
  
                hr = jobs.MoveFirst();  
                if (hr == S_OK)  
                {  
                    jobs.nID = 25;  
                    strcpy_s(&jobs.szDescription[0],  
                             jobs.sizeOfDescription,  
                             "Developer");  
                    jobs.nMinLvl = 10;  
                    jobs.nMaxLvl = 20;  
  
                    jobs.dwDescription = DBSTATUS_S_OK;  
                    jobs.dwID = DBSTATUS_S_OK;  
                    jobs.dwMaxLvl = DBSTATUS_S_OK;  
                    jobs.dwMinLvl = DBSTATUS_S_OK;  
  
                    // Insert method uses accessor 1  
                    // (to avoid writing to the primary key column)  
                    hr = jobs.Insert(1);     
                }  
                jobs.Close();  
            }  
            session.Close();  
        }  
        source.Close();  
    }  
  
    // Uninitialize COM  
    ::CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)   
 [Uživatelské záznamy](../../data/oledb/user-records.md)