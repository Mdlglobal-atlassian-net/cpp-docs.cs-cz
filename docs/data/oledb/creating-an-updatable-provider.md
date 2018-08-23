---
title: Vytvoření aktualizovatelného zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/16/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fffc1ceef1f67dadde61190ccb12ce1cd5b7ba9b
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42465595"
---
# <a name="creating-an-updatable-provider"></a>Vytvoření aktualizovatelného zprostředkovatele

Jazyk Visual C++ podporuje aktualizovatelné zprostředkovatele nebo zprostředkovatele, které můžete aktualizovat (zápis do) úložiště. Toto téma popisuje, jak vytvořit aktualizovatelní zprostředkovatelé pomocí šablony technologie OLE DB.  
  
 Toto téma předpokládá, že začínáte s funkční zprostředkovatele. Existují dva kroky k vytvoření aktualizovatelného zprostředkovatele. Nejprve musíte rozhodnout, jak poskytovatel provede změny úložiště dat; Určuje, zda konkrétně změny jsou okamžitě provést nebo odložena až do vydání příkazu k aktualizaci. V části "[provádění aktualizovat poskytovatele](#vchowmakingprovidersupdatable)" popisuje změny a nastavení, musíte udělat v kódu zprostředkovatele.  
  
 V dalším kroku je nutné zajistit, aby že váš poskytovatel obsahuje všechny funkce pro podporu všechno, co ho může požádat příjemce. Pokud chce aktualizujte úložiště dat příjemce, musí obsahovat kód, který přenese data do úložiště dat zprostředkovatele. Například můžete provádět tyto operace na zdroj dat použít knihovny Run-Time jazyka C nebo MFC. V části "[zápisu do zdroje dat](#vchowwritingtothedatasource)" popisuje, jak zapsat do zdroje dat, řešení s hodnotou NULL a výchozí hodnoty a nastavit příznaky sloupce.  
  
> [!NOTE]
>  [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) je příkladem aktualizovatelného zprostředkovatele. UpdatePV je stejný jako MyProv, ale s podporou.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Vytváření zprostředkovatelů aktualizovat  

 Klíčem k tvorbě aktualizovatelného zprostředkovatele se ke zjištění, jaké operace, které má váš poskytovatel provádět v úložišti dat a jak chcete poskytovatele provádět tyto operace. Konkrétně je závažný problém, jestli jsou aktualizace do úložiště dat provést okamžitě, nebo odloženo (dávkované) až do vydání příkazu k aktualizaci.  
  
 Je třeba nejprve rozhodnout, jestli se má dědit z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl` ve své třídě sady řádků. V závislosti na tom, který z nich rozhodnete implementovat, bude mít vliv funkce tři metody: `SetData`, `InsertRows`, a `DeleteRows`.  
  
- Pokud je zděděn z [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), tyto tři metody volání okamžitě změní úložišti.  
  
- Pokud je zděděn z [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), metody odložit změny do úložiště dat, dokud nezavoláte `Update`, `GetOriginalData`, nebo `Undo`. Pokud aktualizace zahrnuje několik změn, jsou provedeny v dávkovém režimu (Poznámka: dávkování změny můžete přidat režijní náklady na značnou paměť).  
  
 Všimněte si, že `IRowsetUpdateImpl` je odvozena z `IRowsetChangeImpl`. Proto `IRowsetUpdateImpl` umožňuje změnit možnosti a funkce služby batch.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Chcete-li podporovat ve zprostředkovateli  
  
1. Ve své třídě řádků dědit z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl`. Tyto třídy poskytují vhodné rozhraní pro Změna úložiště dat:  
  
     **Přidání IRowsetChange**  
  
     Přidat `IRowsetChangeImpl` k použití této formy řetězec dědičnosti:  
  
    ```cpp  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Přidejte také `COM_INTERFACE_ENTRY(IRowsetChange)` k `BEGIN_COM_MAP` oddílu ve své třídě sady řádků.  
  
     **Přidání IRowsetUpdate**  
  
     Přidat `IRowsetUpdate` k použití této formy řetězec dědičnosti:  
  
    ```cpp  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Měli byste odebrat `IRowsetChangeImpl` řádek z vašeho řetězu dědičnosti. Jedinou výjimkou je to výše zmíněné musí obsahovat kód `IRowsetChangeImpl`.  
  
2.  Přidejte následující do mapy modelu COM (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |Pokud se rozhodnete implementovat|Přidejte do mapy modelu COM.|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  V příkazu, přidejte následující mapy set vlastnosti (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |Pokud se rozhodnete implementovat|Přidejte do mapy sady vlastností|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  V mapě sadu vlastností měli byste také zahrnout všechna následující nastavení, jak se objeví pod:  
  
    ```cpp  
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
  
     Můžete najít hodnoty použité v těchto volání makra vyhledáváním v Atldb.h identifikátory vlastnosti a hodnoty (Pokud Atldb.h se liší v online dokumentaci ke službě, nahrazuje Atldb.h dokumentaci).  
  
    > [!NOTE]
    >  Mnoho `VARIANT_FALSE` a `VARIANT_TRUE` vyžaduje nastavení šablony technologie OLE DB; specifikaci OLE DB uvádí, že můžou být r/w, ale šablony technologie OLE DB podporuje pouze jednu hodnotu.  
  
     **Pokud se rozhodnete implementovat IRowsetChangeImpl**  
  
     Pokud se rozhodnete implementovat `IRowsetChangeImpl`, musíte nastavit následující vlastnosti ve zprostředkovateli služby. Tyto vlastnosti se primárně používají k žádosti rozhraní prostřednictvím `ICommandProperties::SetProperties`.  
  
    - `DBPROP_IRowsetChange`: Nastavení tomto automaticky nastaví `DBPROP_IRowsetChange`.  
  
    - `DBPROP_UPDATABILITY`: Bitová maska zadání podporovaných metod na `IRowsetChange`: `SetData`, `DeleteRows`, nebo `InsertRow`.  
  
    - `DBPROP_CHANGEINSERTEDROWS`: Příjemce může volat `IRowsetChange::DeleteRows` nebo `SetData` nově vložených řádků.  
  
    - `DBPROP_IMMOBILEROWS`: Sada řádků nebude pořadí vložené nebo aktualizované řádky.  
  
     **Pokud se rozhodnete implementovat IRowsetUpdateImpl**  
  
     Pokud se rozhodnete implementovat `IRowsetUpdateImpl`, musíte nastavit následující vlastnosti ve zprostředkovateli služby, navíc k nastavením vlastností pro `IRowsetChangeImpl` výše uvedených:  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_OWNUPDATEDELETE`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_OTHERINSERT`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_OTHERUPDATEDELETE`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_REMOVEDELETED`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Pokud podporujete oznámení, může být také některé také další vlastnosti; naleznete v části `IRowsetNotifyCP` pro tento seznam.  
  
##  <a name="vchowwritingtothedatasource"></a> Zápis do zdroje dat.  
 Chcete-li načíst ze zdroje dat, zavolejte `Execute` funkce. Chcete-li zapsat do zdroje dat, zavolejte `FlushData` funkce. (V obecném smyslu vyprázdněte znamená, že se uložit změny provedené u tabulky nebo indexu na disk.)  

```cpp

FlushData(HROW, HACCESSOR);  

```

Popisovač (HACCESSOR) argumenty a popisovač řádku (HROW) vám umožňují určit oblast pro zápis. Obvykle můžete zapsat jednoho datového pole najednou.

`FlushData` Metoda zapisuje data ve formátu, ve kterém byla původně uložena. Pokud funkci nelze přepsat, váš poskytovatel bude program fungovat správně, ale změny se nebudou vyprázdní na úložiště dat.

### <a name="when-to-flush"></a>Když se nezdařil
Šablony zprostředkovatele volání FlushData pokaždé, když se data musí být zapsána do úložiště dat; obvykle (ale ne vždy) dochází k tomu následkem volání následující funkce:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (Pokud je nová data k vložení řádku)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Jak to funguje

Příjemce provede volání, která vyžaduje vyprázdnění (například aktualizace) a toto volání je předáno poskytovateli, což vždy provede následující akce:

- Volání `SetDBStatus` vždy, když budete mít stav hodnotu hranice.

- Ověří příznaky sloupce.

- Volání `IsUpdateAllowed`.

Tyto tři kroky zajistit zabezpečení. Potom volá zprostředkovatele `FlushData`.

### <a name="how-to-implement-flushdata"></a>Jak implementovat FlushData

K implementaci `FlushData`, je potřeba vzít v úvahu několik věcí:

Ujistěte se, že úložiště dat může zpracovat změny.

Zpracování hodnot NULL.

### <a name="handling-default-values"></a>Zpracování výchozích hodnot.

Implementovat vlastní metodu FlushData, budete muset:

- Přejděte do vaší třídy sady řádků.

- Třídy v sadě řádků vložit deklarace:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)  
   {  
      // Insert your implementation here and return an HRESULT.  
   }  
   ```

- Poskytnout implementaci položky `FlushData`.

Správná implementace FlushData – ukládá pouze řádky a sloupce, které jsou ve skutečnosti aktualizovány. Parametry HROW a HACCESSOR slouží k určení aktuální řádek a sloupec optimalizace.

Obvykle je největší výzvou práce s nativní datového úložiště. Pokud je to možné zkuste:

- Zachovejte metodu zápisu s vaším úložištěm dat co nejjednodušší.

- Zpracování hodnot NULL (volitelný, ale doporučené).

- Zpracujte výchozí hodnoty (volitelný, ale doporučené).

Nejlepší postup je, aby skutečné hodnoty zadané ve vašem úložišti dat pro hodnotu NULL a výchozí hodnoty. Je vhodné, pokud lze odvodit data. Pokud tomu tak není, je doporučeno umožňují hodnotu NULL a výchozí hodnoty.

Následující příklad ukazuje jak `FlushData` je implementována ve třídě RUpdateRowset v ukázce UpdatePV (viz Rowset.h ve vzorovém kódu):

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

### <a name="handling-changes"></a>Zpracování změn

Pro poskytovatele pro případ změn musíte nejprve zkontroluje, že má zařízení, které vám umožní provádět změny v něm vaše úložiště dat (například textový soubor nebo soubor videa). Pokud tomu tak není, měli byste tento kód samostatně vytvořit z projektu zprostředkovatele.

### <a name="handling-null-data"></a>Zpracování dat NULL

Je možné, že koncový uživatel odešle data hodnotu NULL. Při zápisu hodnot NULL do pole ve zdroji dat, může být potenciální problémy. Představte si pořizování pořadí aplikace, která přijímá hodnoty pro města a PSČ; by mohl přijmout nebo obě hodnoty, ale není ani jedno, protože v takovém případě doručení by jinak nebylo možné. Proto je nutné omezit určité kombinace hodnot NULL v polích, které dávají smysl pro vaši aplikaci.

Jako vývojář poskytovatele musíte zvážit jak budete ukládat data, jak budou číst data z úložiště dat a jak můžete zadat pro uživatele. Konkrétně musíte zvážit, jak chcete-li změnit stav dat z datové sady řádků ve zdroji dat (například DataStatus = NULL). Rozhodněte, jakou hodnotu má vrátit v případě příjemce přistupuje k poli, který obsahuje hodnotu NULL.

Prohlédněte si kód v ukázce UpdatePV; ukazuje, jak zprostředkovatele můžete zpracovávat data hodnotu NULL. V UpdatePV zprostředkovatel ukládá NULL data napsáním řetězec "NULL" dat v úložišti. Při čtení dat NULL z úložiště dat, uvidí tento řetězec a pak vyprázdní vyrovnávací paměť, vytváření řetězec s hodnotou NULL. Je také přepsání `IRowsetImpl::GetDBStatus` ve kterém se vrátí DBSTATUS_S_ISNULL, pokud tato hodnota dat je prázdný.

### <a name="marking-nullable-columns"></a>Označení sloupce s možnou hodnotou Null
Pokud implementujete sad řádků schématu (viz `IDBSchemaRowsetImpl`), vaše implementace by měl určit v sadě řádků DBSCHEMA_COLUMNS (obvykle označeny ve zprostředkovateli CxxxSchemaColSchemaRowset), že je sloupec s možnou hodnotou Null.

Musíte také určit, že všechny sloupce s možnou hodnotou NULL obsahovat hodnotu DBCOLUMNFLAGS_ISNULLABLE ve vaší verzi `GetColumnInfo`.

V implementaci šablon technologie OLE DB pro označení sloupce jako s možnou hodnotou Null, pokud zprostředkovatel předpokládá, že musí obsahovat hodnotu a neumožní příjemce do něj poslat hodnoty null.

Následující příklad ukazuje způsob, jakým `CommonGetColInfo` funkce je implementovaná v CUpdateCommand (viz UpProvRS.cpp) v UpdatePV. Všimněte si, jak sloupce, které mají tento DBCOLUMNFLAGS_ISNULLABLE pro sloupce s možnou hodnotou Null.

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

Jako s daty NULL, mají odpovědnost zabývat se změnou výchozích hodnot.

Ve výchozím nastavení FlushData a spouštět je vrátí hodnotu S_OK. Proto pokud funkci nelze přepsat, se položky objeví na úspěšné (se vrátí hodnotu S_OK), ale nebudou přenášeny do úložiště dat.

V ukázce UpdatePV (v Rowset.h) `SetDBStatus` obsluhovala výchozí hodnoty následujícím způsobem:

```cpp
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

Pokud podporujete výchozí hodnoty na sloupce, je nutné nastavit pomocí metadat \<třída zprostředkovatele\>SchemaRowset třídy. Nastavit `m_bColumnHasDefault` = VARIANT_TRUE.

Máte také nastavit příznaky sloupce, které jsou určeny pomocí DBCOLUMNFLAGS výčtového typu. Příznaky sloupce popisují vlastnosti sloupce.

Například v `CUpdateSessionColSchemaRowset` třídy v UpdatePV (v Session.h) z prvního sloupce nastavit tímto způsobem:

```cpp
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

Tento kód určuje, mimo jiné, že sloupec podporuje výchozí hodnotu 0, že být zapisovatelná, a že všechna data ve sloupci mít stejnou délku. Pokud chcete data ve sloupci mít proměnné délky, nebude tento příznak nastavit.

## <a name="see-also"></a>Viz také
[Vytvoření zprostředkovatele OLE DB](creating-an-ole-db-provider.md)