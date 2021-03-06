---
title: Použití více přístupových objektů pro sadu řádků
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: d1ab314edeebedef4cff14cd5364a7ca16c74769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216379"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Použití více přístupových objektů pro sadu řádků

Existují tři základní scénáře, ve kterých je potřeba použít několik přístupových objektů:

- **Více sad řádků pro čtení a zápisu.** V tomto scénáři máte tabulku s primárním klíčem. Chcete být schopni číst všechny sloupce v řádku, včetně primární klíč. Chcete být schopni zapisovat data pro všechny sloupce kromě primárního klíče (protože nelze zapisovat do sloupec primárního klíče). V takovém případě můžete nastavit dva přistupující objekty:

  - Přistupující objekt 0 obsahuje všechny sloupce.

  - Přistupující objekt 1 obsahuje všechny sloupce kromě primární klíč.

- **Výkon.** V tomto scénáři jste jeden nebo více sloupců velké množství dat, například grafika, zvuk nebo video soubory. Pokaždé, když se přesunete na řádek, pravděpodobně nechcete načíst sloupec se souborem velkých objemů dat, protože to uděláte tak by zpomalit výkon vaší aplikace.

  Můžete nastavit samostatný přístupové objekty, ve kterých první přistupující objekt obsahuje všechny sloupce kromě toho s velkými daty a automaticky; načítá data z těchto sloupců první přistupující objekt je automaticky přistupujícího objektu. Druhý přístupový objekt načte pouze sloupec obsahující velkých objemů dat, ale jeho nenačítá data z tohoto sloupce automaticky. Může mít jiné metody, aktualizaci nebo načítání velkých dat na vyžádání.

  - Přistupující objekt 0 je automatické přistupující objekt; načte všechny sloupce kromě toho s velkými daty.

  - Přístupový objekt automatické; není přístupového objektu 1 načte sloupec s velkými daty.

  Argument automaticky použijte k určení, zda je automaticky přistupujícího objektu.

- **Více ISequentialStream sloupců.** V tomto scénáři jste více než jeden sloupec podniku `ISequentialStream` data. Každý přistupující objekt je však omezená na jednu `ISequentialStream` datového proudu. Pokud chcete tento problém vyřešit, nastavte několik přístupových objektů, každý mají jedno `ISequentialStream` ukazatele.

Obvykle vytvoříte pomocí přístupových objektů [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra. Můžete také použít [db_accessor](../../windows/db-accessor.md) atribut. (Přístupové objekty jsou popsány dále v [uživatelských záznamů](../../data/oledb/user-records.md).) Makra nebo atribut určete, jestli má přistupující objekt automatické nebo přístupový objekt bez automaticky:

- Automatické přístupového objektu, přesunutí metody `MoveFirst`, `MoveLast`, `MoveNext`, a `MovePrev` načíst data pro všechny sloupce zadané automaticky. Přistupující objekt 0 by měla být automatická přistupujícího objektu.

- V přístupový objekt bez automatické načítání nedojde, dokud explicitně volání metody, jako `Update`, `Insert`, `Fetch`, nebo `Delete`. Ve scénářích je popsáno výše nebudete chtít načíst všechny sloupce v každém přesunu. Můžete umístit jeden nebo více sloupců v samostatných přístupového objektu a zkontrolujte, zda neautomatický přistupující objekt, jak je znázorněno níže.

Následující příklad používá několik přístupových objektů číst a zapisovat do tabulky databáze pubs systému SQL Server, použití více přístupových objektů úloh. V tomto příkladu je nejběžnější použití více přístupových objektů; Podívejte se na výše uvedeném scénáři "více sad řádků pro čtení a zápisu".

Třída uživatelského záznamu je následujícím způsobem. Nastaví dva přistupující objekty: přístupový objekt 0 obsahuje pouze sloupec primárního klíče (ID) a přístupového objektu 1 obsahuje další sloupce.

```cpp
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

Hlavní kódu vypadá takto. Volání `MoveNext` automaticky načte data z ID sloupec primárního klíče pomocí přístupového objektu 0. Poznámka: Jak `Insert` metoda poblíž používá koncový přístupového objektu 1, aby zápis na sloupec primárního klíče.

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
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

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)<br/>
[Uživatelské záznamy](../../data/oledb/user-records.md)
