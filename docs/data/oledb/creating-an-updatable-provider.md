---
title: "Vytvoření aktualizovatelného zprostředkovatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d65bce2b262b7582f9194eb8047d71ce06f3ca16
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="creating-an-updatable-provider"></a>Vytvoření aktualizovatelného zprostředkovatele
Visual C++ podporuje aktualizovatelní zprostředkovatelé nebo poskytovatelů, které můžete aktualizovat (zapisovat na) úložišti. Toto téma popisuje postup vytvoření aktualizovatelní zprostředkovatelé pomocí šablony technologie OLE DB.  
  
 Toto téma předpokládá, že začínáte funkčního zprostředkovatele. Existují dva kroky k vytvoření aktualizovatelného zprostředkovatele. Nejdřív musíte rozhodnout, jak bude zprostředkovatel provádět změny do úložiště dat; jestli konkrétně změny jsou okamžitě provést nebo odložení až do vydání příkazu pro aktualizaci. V části "[vytváření zprostředkovatelů aktualizovat](#vchowmakingprovidersupdatable)" popisuje změny a nastavení, je třeba provést v kódu zprostředkovatele.  
  
 Dále můžete musí ujistěte, že váš poskytovatel obsahuje všechny funkce pro podporu nic, co může vydat příjemce. Pokud chce příjemce aktualizovat úložiště dat, musí obsahovat kód, který dál data do úložiště dat zprostředkovatele. Může například použít běhové knihovny jazyka C nebo MFC k provádění těchto operací na datovém zdroji. V části "[zápisu do zdroje dat](#vchowwritingtothedatasource)" popisuje, jak k zápisu do zdroje dat, pracují s **NULL** výchozích hodnot a nastavení příznaku sloupce.  
  
> [!NOTE]
>  UpdatePV je příkladem aktualizovatelného zprostředkovatele. UpdatePV je stejný jako MyProv, ale s podporou.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Tvorba aktualizovat  
 Klíč k tvorbě aktualizovatelného zprostředkovatele je pochopení, jaké operace, které má váš poskytovatel k plnění úložiště dat a jak chcete, aby zprostředkovatel k provádění těchto operací. Konkrétně závažný problém je, jestli se mají provést okamžitě nebo odložení aktualizace do úložiště dat (zpracovat v dávce) až do vydání příkazu pro aktualizaci.  
  
 Musíte napřed rozhodnout, zda dědění z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl` ve vaší třídě řádků. V závislosti na tom, které z těchto rozhodnete implementovat, bude mít vliv funkce tři metody: `SetData`, **InsertRows**, a `DeleteRows`.  
  
-   Pokud dědí od [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), volání těchto tří metod změní okamžitě úložišti.  
  
-   Pokud dědí od [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), metody odložení změny do úložiště dat, dokud zavoláte **aktualizace**, `GetOriginalData`, nebo **vrátit zpět**. Pokud aktualizace zahrnuje několik změn, provádějí se v dávkovém režimu (Všimněte si, dávkování změny přidat režijní náklady na značnou část paměti).  
  
 Všimněte si, že `IRowsetUpdateImpl` je odvozena z `IRowsetChangeImpl`. Proto `IRowsetUpdateImpl` poskytuje možnost změny plus možnost dávky.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Chcete-li podporovat ve zprostředkovateli  
  
1.  Ve třídě řádků dědit z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl`. Tyto třídy poskytují příslušná rozhraní pro Změna úložiště dat:  
  
     **Přidání IRowsetChange**  
  
     Přidat `IRowsetChangeImpl` do vašeho řetězce dědičnosti v této podobě:  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Také přidat `COM_INTERFACE_ENTRY(IRowsetChange)` k `BEGIN_COM_MAP` části ve vaší třídě řádků.  
  
     **Přidání IRowsetUpdate**  
  
     Přidat `IRowsetUpdate` do vašeho řetězce dědičnosti v této podobě:  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Byste měli odebrat `IRowsetChangeImpl` řádek z vašeho řetězce dědičnosti. Jedinou výjimkou je k výše zmíněné musí obsahovat kód pro `IRowsetChangeImpl`.  
  
2.  Přidejte následující do mapy modelu COM (**BEGIN_COM_MAP... END_COM_MAP**):  
  
    |Pokud implementujete|Přidat mapu modelu COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  V příkazu, přidejte následující vaší mapy sady vlastností (**BEGIN_PROPSET_MAP... END_PROPSET_MAP**):  
  
    |Pokud implementujete|Přidejte do mapy sady vlastností|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  V mapě sada vlastností byste měli taky zahrnout všechny z následujících nastavení jak jsou zobrazeny níže:  
  
    ```  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     Můžete najít hodnoty používané v těchto volání makro podle Atldb.h pro ID vlastnosti a hodnoty (Pokud Atldb.h se liší od online dokumentaci, nahrazuje Atldb.h dokumentaci).  
  
    > [!NOTE]
    >  Řadu **VARIANT_FALSE** a `VARIANT_TRUE` vyžaduje nastavení šablony technologie OLE DB; specifikace OLE DB říká můžou být pro čtení a zápis, ale šablony technologie OLE DB podporuje pouze jednu hodnotu.  
  
     **Pokud implementujete IRowsetChangeImpl**  
  
     Pokud implementujete `IRowsetChangeImpl`, musíte nastavit následující vlastnosti na svého poskytovatele. Tyto vlastnosti se primárně používají k žádostem rozhraní prostřednictvím **ICommandProperties::SetProperties**.  
  
    -   `DBPROP_IRowsetChange`: Nastavení tomto automaticky nastaví **DBPROP_IRowsetChange**.  
  
    -   `DBPROP_UPDATABILITY`: Bitová maska určí podporované metody na `IRowsetChange`: `SetData`, `DeleteRows`, nebo `InsertRow`.  
  
    -   `DBPROP_CHANGEINSERTEDROWS`: Příjemce může volat **IRowsetChange::DeleteRows** nebo `SetData` pro nově vložené řádky.  
  
    -   `DBPROP_IMMOBILEROWS`: Sada řádků nebude pořadí vložené nebo aktualizované řádky.  
  
     **Pokud implementujete IRowsetUpdateImpl**  
  
     Pokud implementujete `IRowsetUpdateImpl`, musíte nastavit následující vlastnosti na zprostředkovateli, navíc k nastavení všechny vlastnosti pro `IRowsetChangeImpl` dříve uvedených:  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`: Musí být READ_ONLY a VARIANT_TRUE.  
  
    -   `DBPROP_OWNUPDATEDELETE`: Musí být READ_ONLY a VARIANT_TRUE.  
  
    -   `DBPROP_OTHERINSERT`: Musí být READ_ONLY a VARIANT_TRUE.  
  
    -   `DBPROP_OTHERUPDATEDELETE`: Musí být READ_ONLY a VARIANT_TRUE.  
  
    -   `DBPROP_REMOVEDELETED`: Musí být READ_ONLY a VARIANT_TRUE.  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Pokud podporujete oznámení, také může mít některé další vlastnosti; Projděte část o `IRowsetNotifyCP` pro tento seznam.  
  
     Například jak jsou nastaveny vlastnosti, najdete v části vlastnost nastavena mapy **CUpdateCommand** (v Rowset.h) v [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
##  <a name="vchowwritingtothedatasource"></a> Zápis do zdroje dat  
 Čtení ze zdroje dat, volání **Execute** funkce. K zápisu do zdroje dat, volání `FlushData` funkce. (V obecném smyslu vyprázdnění způsob, jak uložit změny provedené u tabulky nebo indexu na disk.)  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 Popisovač řádku (*HROW*) a popisovač přistupujícího objektu (*HACCESSOR*) argumenty umožňují určit oblast pro zápis. Obvykle zapisovat pouze jedno datové pole v čase.  
  
 `FlushData` Metoda zapisuje data ve formátu, ve kterém byla původně uložena. Pokud není přepsat tuto funkci, poskytovatel bude správně fungovat, ale nebude vyprázdněna změny do úložiště dat.  
  
### <a name="when-to-flush"></a>Když k vyprázdnění  
 Šablony zprostředkovatele volají `FlushData` vždy, když data potřebují zapisovat do úložiště dat; to obvykle (ale ne vždy) dojde v důsledku volání následující funkce:  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** (Pokud je nová data, která se přidá řádek)  
  
-   **IRowsetUpdate::Update**  
  
### <a name="how-it-works"></a>Jak to funguje  
 Příjemce provede volání vyžadující vyprázdnění (například **aktualizace**) a toto volání je předána zprostředkovateli, který vždy provede následující akce:  
  
-   Volání `SetDBStatus` vždy, když máte vázanou hodnotu stavu (najdete v části *odkaz programátory technologie OLE DB*, 6 kapitoly *datové části: stav*).  
  
-   Zkontrolujte příznaky sloupce.  
  
-   Volání `IsUpdateAllowed`.  
  
 Tyto tři kroky pomáhají zajistit zabezpečení. Potom volání zprostředkovatele `FlushData`.  
  
### <a name="how-to-implement-flushdata"></a>Jak implementovat FlushData  
 K implementaci `FlushData`, je nutné vzít v úvahu několik výhrad:  
  
-   Zajistěte, aby úložiště dat může zpracovávat změny,  
  
-   Zpracování **NULL** hodnoty.  
  
-   Zpracování výchozí hodnoty.  
  
 K implementaci vlastní `FlushData` metoda, potřebujete:  
  
-   Přejděte do vaší třídy sady řádků.  
  
-   Třídy v sadě řádků put deklaraci:  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   Zadejte implementaci `FlushData`.  
  
 Správná implementace `FlushData` ukládá pouze řádky a sloupce, které jsou ve skutečnosti aktualizované. Můžete použít *HROW* a *HACCESSOR* parametry k určení aktuální řádků a sloupců optimalizace.  
  
 Obvykle největší výzvou pracuje s vlastními nativní data store. Pokud je to možné zkuste:  
  
-   Zachovat metodu zápisu do vašeho úložiště co nejjednodušší.  
  
-   Zpracování **NULL** hodnot (nepovinné ale doporučené).  
  
-   Zpracování výchozí hodnoty (nepovinné ale doporučené).  
  
 Nejlepším krokem je mít skutečné hodnoty zadané ve vašem úložišti dat pro **NULL** a výchozí hodnoty. Je doporučeno lze odvodit data. Pokud ne, je doporučeno tak, aby **NULL** a výchozí hodnoty.  
  
 Následující příklad ukazuje způsob `FlushData` je implementována ve `RUpdateRowset` třídy v [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázkové (viz Rowset.h v ukázkovém kódu):  
  
```cpp
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
...  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");  
  
    USES_CONVERSION;  
    enum {  
        sizeOfString = 256,  
        sizeOfFileName = MAX_PATH  
    };  
    FILE*    pFile = NULL;  
    TCHAR    szString[sizeOfString];  
    TCHAR    szFile[sizeOfFileName];  
    errcode  err = 0;  
  
    ObjectLock lock(this);  
  
    // From a filename, passed in as a command text,   
    // scan the file placing data in the data array.  
    if (m_strCommandText == (BSTR)NULL)  
    {  
        ATLTRACE( "RRowsetUpdate::FlushData -- "  
                  "No filename specified\n");  
        return E_FAIL;  
    }  
  
    // Open the file  
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));  
    if ((szFile[0] == _T('\0')) ||   
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))  
    {  
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");  
        return DB_E_NOTABLE;  
    }  
  
    // Iterate through the row data and store it.  
    for (long l=0; l<m_rgRowData.GetSize(); l++)  
    {  
        CAgentMan am = m_rgRowData[l];  
  
        _putw((int)am.dwFixed, pFile);  
  
        if (_tcscmp(&am.szCommand[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
  
        if (_tcscmp(&am.szText[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
  
        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
  
        if (_tcscmp(&am.szText2[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
    }  
  
    if (fflush(pFile) == EOF || fclose(pFile) == EOF)  
    {  
        ATLTRACE("RRowsetUpdate::FlushData -- "  
                 "Couldn't flush or close file\n");  
    }  
  
    return S_OK;  
}  
```  
  
### <a name="handling-changes"></a>Zpracování změny  
 Ke zprostředkovateli zpracovávat změny musíte nejprve a ujistěte se, že má zařízení, která vám umožní provádět změny v něm data store (například textový soubor nebo soubor videa). Pokud ne, měli byste vytvořit tento kód samostatně z projektu zprostředkovatele.  
  
### <a name="handling-null-data"></a>Zpracování dat pro hodnotu NULL.  
 Je možné, že koncový uživatel odešle **NULL** data. Při psaní **NULL** hodnoty polí ve zdroji dat, může být potenciální problémy. Představte si pořízení pořadí aplikace, která přijímá hodnoty pro město a PSČ; může přijmout nebo obě hodnoty, ale ne žádnou, protože v takovém případě by bylo možné doručení. Je proto nutné omezit určité kombinace **NULL** hodnot v polích, které dávají smysl pro vaši aplikaci.  
  
 Jako vývojář zprostředkovatele budete muset zvážit, jak budete ukládat data, jak bude číst data z úložiště dat a jak můžete určit, že pro uživatele. Konkrétně musí zvážit způsob změnit stav dat dat ve zdroji dat (například DataStatus = **NULL**). Rozhodněte, jakou má vrátit, pokud přistupuje k příjemce, pole obsahující hodnotu **NULL** hodnotu.  
  
 Podívejte se na kód v [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázku; ukazuje, jak zpracovávat zprostředkovatele **NULL** data. V UpdatePV zprostředkovatel ukládá **NULL** data zápisem řetězce "NULL" v úložišti. Při čtení **NULL** úložiště dat z data, vidí tento řetězec a pak vyprázdní vyrovnávací paměť, vytváření **NULL** řetězec. Je také přepsání `IRowsetImpl::GetDBStatus` v která vrací **DBSTATUS_S_ISNULL** v případě, že hodnota dat je prázdná.  
  
### <a name="marking-nullable-columns"></a>Označení sloupce s možnou hodnotou Null  
 Pokud implementujete sad řádků schématu (najdete v části `IDBSchemaRowsetImpl`), vaše implementace musí určit v **DBSCHEMA_COLUMNS** sady řádků (obvykle označený ve zprostředkovateli podle **C***xxx*** SchemaColSchemaRowset**), že je sloupec s možnou hodnotou Null.  
  
 Musíte také určit, že všechny sloupce s možnou hodnotou NULL obsahovat **DBCOLUMNFLAGS_ISNULLABLE** hodnotu ve vaší verzi `GetColumnInfo`.  
  
 Implementace šablony OLE DB Pokud se nepodaří označení sloupce jako s možnou hodnotou Null, zprostředkovatel předpokládá, že musí obsahovat hodnotu a neumožní příjemce do něj poslat hodnoty null.  
  
 Následující příklad ukazuje jak **CommonGetColInfo** funkce je implementována v **CUpdateCommand** (viz UpProvRS.cpp) v UpdatePV. Všimněte si, jak to mít sloupce **DBCOLUMNFLAGS_ISNULLABLE** pro sloupce s možnou hodnotou Null.  
  
```cpp
/////////////////////////////////////////////////////////////////////////////  
// CUpdateCommand (in UpProvRS.cpp)  
  
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)  
{  
    static ATLCOLUMNINFO _rgColumns[6];  
    ULONG ulCols = 0;  
  
    if (bBookmark)  
    {  
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,  
                            sizeof(DWORD), DBTYPE_BYTES,  
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,  
                            DBCOLUMNFLAGS_ISBOOKMARK)  
        ulCols++;  
    }  
  
    // Next set the other columns up.  
    // Add a fixed length entry for OLE DB conformance testing purposes  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,  
                        10, 255, GUID_NULL, CAgentMan, dwFixed,   
                        DBCOLUMNFLAGS_WRITE |   
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)  
    ulCols++;  
  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,  
                        255, 255, GUID_NULL, CAgentMan, szCommand,  
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,   
                        255, 255, GUID_NULL, CAgentMan, szText,   
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,  
                        255, 255, GUID_NULL, CAgentMan, szCommand2,   
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,  
                        255, 255, GUID_NULL, CAgentMan, szText2,   
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
  
    if (pcCols != NULL)  
    {  
        *pcCols = ulCols;  
    }  
  
    return _rgColumns;  
}  
```  
  
### <a name="default-values"></a>Výchozí hodnoty  
 Stejně jako u **NULL** data, máte odpovědnost zabývat se změnou výchozích hodnot.  
  
 Výchozí `FlushData` a **Execute** vrácení `S_OK`. Proto pokud není přepsat tuto funkci, změny se zobrazí, úspěšné (`S_OK` bude vrácen), ale nebudou přenášeny do úložiště dat.  
  
 V [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázku (v Rowset.h), `SetDBStatus` metoda zpracovává výchozí hodnoty takto:  
  
```  
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,  
                            ATLCOLUMNINFO* pColInfo)  
{  
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);  
  
    void* pData = NULL;  
    char* pDefaultData = NULL;  
    DWORD* pFixedData = NULL;  
  
    switch (*pdbStatus)  
    {  
        case DBSTATUS_S_DEFAULT:  
            pData = (void*)&m_rgRowData[pRow->m_iRowset];  
            if (pColInfo->wType == DBTYPE_STR)  
            {  
                pDefaultData = (char*)pData + pColInfo->cbOffset;  
                strcpy_s(pDefaultData, "Default");  
            }  
            else  
            {  
                pFixedData = (DWORD*)((BYTE*)pData +   
                                          pColInfo->cbOffset);  
                *pFixedData = 0;  
                return S_OK;  
            }  
            break;  
        case DBSTATUS_S_ISNULL:  
        default:  
            break;  
    }  
    return S_OK;  
}  
```  
  
### <a name="column-flags"></a>Příznaky sloupce  
 Pokud vaše sloupce podporují výchozí hodnoty, budete muset nastavit použití metadat v  **\< ***třída zprostředkovatele***> SchemaRowset** třídy. Nastavit *m_bColumnHasDefault* = `VARIANT_TRUE`.  
  
 Máte také nastavit příznaky sloupce, které jsou určeny pomocí **DBCOLUMNFLAGS** výčtového typu. Příznaky sloupce popisují charakteristiku sloupce.  
  
 Například v `CUpdateSessionColSchemaRowset` třídy v [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) (v Session.h), je první sloupec nastavit takto:  
  
```  
// Set up column 1  
trData[0].m_ulOrdinalPosition = 1;  
trData[0].m_bIsNullable = VARIANT_FALSE;  
trData[0].m_bColumnHasDefault = VARIANT_TRUE;  
trData[0].m_nDataType = DBTYPE_UI4;  
trData[0].m_nNumericPrecision = 10;  
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |  
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;  
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));  

m_rgRowData.Add(trData[0]);  
```  
  
 Tento kód určuje, mimo jiné, že sloupec podporuje výchozí hodnotu 0, aby byl lze zapisovat, a že všechna data ve sloupci mají stejnou délku. Pokud chcete data ve sloupci tak, aby měl proměnné délky, nebude tento příznak nastavit.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)