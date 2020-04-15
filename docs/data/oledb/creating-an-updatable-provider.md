---
title: Vytvoření aktualizovatelného zprostředkovatele
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365561"
---
# <a name="creating-an-updatable-provider"></a>Vytvoření aktualizovatelného zprostředkovatele

Visual C++ podporuje aktualizovatelné zprostředkovatele nebo zprostředkovatele, kteří mohou aktualizovat (zapisovat) úložiště dat. Toto téma popisuje, jak vytvořit aktualizovatelné zprostředkovatele pomocí šablon TECHNOLOGIE OLE DB.

Toto téma předpokládá, že začínáte s funkčnízprostředkovatele. Existují dva kroky k vytvoření aktualizovatelného zprostředkovatele. Musíte se nejprve rozhodnout, jak bude zprostředkovatel provádět změny v úložišti dat; konkrétně zda změny mají být provedeny okamžitě nebo odloženo, dokud není vydán příkaz aktualizace. Část["Vytváření zprostředkovatelů aktualizovatelných"](#vchowmakingprovidersupdatable)popisuje změny a nastavení, které je třeba provést v kódu zprostředkovatele.

Dále je nutné se ujistit, že váš poskytovatel obsahuje všechny funkce pro podporu všeho, co spotřebitel může požadovat. Pokud chce příjemce aktualizovat úložiště dat, zprostředkovatel musí obsahovat kód, který uchovává data do úložiště dat. Můžete například použít c run-time library nebo mfc k provedení těchto operací na zdroj dat. Část[Zápis do zdroje dat](#vchowwritingtothedatasource)popisuje, jak zapisovat do zdroje dat, řešit hodnoty NULL a výchozí hodnoty a nastavit příznaky sloupců.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) je příkladem aktualizovatelného zprostředkovatele. UpdatePV je stejný jako MyProv, ale s aktualizovatelnou podporou.

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Vytváření aktualizovatelných zprostředkovatelů

Klíčem k tomu, aby zprostředkovatel aktualizovatelný je pochopení, jaké operace chcete, aby váš poskytovatel provádět v úložišti dat a jak chcete, aby zprostředkovatel provádět tyto operace. Konkrétně hlavní problém je, zda aktualizace úložiště dat mají být provedeny okamžitě nebo odložené (dávkové) až do vydání příkazu aktualizace.

Musíte se nejprve rozhodnout, zda dědit z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl` ve třídě řádků. V závislosti na tom, kterou z nich se rozhodnete implementovat, bude ovlivněna funkce tří metod: `SetData`, `InsertRows`, a `DeleteRows`.

- Pokud dědíte z [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), volání těchto tří metod okamžitě změní úložiště dat.

- Pokud dědíte z [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), metody odložit změny `Update` `GetOriginalData`úložiště `Undo`dat, dokud volat , , nebo . Pokud aktualizace zahrnuje několik změn, jsou prováděny v dávkovém režimu (všimněte si, že dávkové změny mohou přidat značné nároky na paměť).

Všimněte `IRowsetUpdateImpl` si, `IRowsetChangeImpl`že je odvozen od . To `IRowsetUpdateImpl` znamená, že vám umožňuje změnit schopnost plus dávkové schopnosti.

### <a name="to-support-updatability-in-your-provider"></a>Podpora aktualizovatelnosti ve vašem poskytovateli

1. Ve třídě sady řádků `IRowsetChangeImpl` dědí z nebo `IRowsetUpdateImpl`. Tyto třídy poskytují vhodná rozhraní pro změnu úložiště dat:

   **Přidání IRowsetChange**

   Přidejte `IRowsetChangeImpl` do řetězce dědičnosti pomocí tohoto formuláře:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Přidejte `COM_INTERFACE_ENTRY(IRowsetChange)` také `BEGIN_COM_MAP` do oddílu ve třídě sady řádků.

   **Přidání aktualizace IRowsetUpdate**

   Přidejte `IRowsetUpdate` do řetězce dědičnosti pomocí tohoto formuláře:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Měli byste `IRowsetChangeImpl` odebrat řádek z řetězce dědičnosti. Tato jedna výjimka z výše uvedené směrnice `IRowsetChangeImpl`musí obsahovat kód pro .

1. Do mapy COM přidejte`BEGIN_COM_MAP ... END_COM_MAP`následující položky ( ):

   |  Pokud implementujete   |           Přidat do mapy COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Pokud implementujete | Přidat do mapy sady vlastností |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Do příkazu přidejte do mapy sady`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`vlastností následující položky ( ):

   |  Pokud implementujete   |                                             Přidat do mapy sady vlastností                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. V mapě sady vlastností byste měli také zahrnout všechna následující nastavení, která jsou uvedena níže:

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

   Hodnoty použité v těchto voláních maker najdete v Souboru Atldb.h pro ID vlastností a hodnoty (pokud se Atldb.h liší od online dokumentace, atldb.h nahrazuje dokumentaci).

   > [!NOTE]
   > Mnoho nastavení `VARIANT_FALSE` `VARIANT_TRUE` a jsou vyžadovány šablony TECHNOLOGIE OLE DB; Specifikace TECHNOLOGIE OLE DB říká, že mohou číst a zapisovat, ale šablony TECHNOLOGIE OLE DB mohou podporovat pouze jednu hodnotu.

   **Pokud implementujete IRowsetChangeImpl**

   Pokud implementujete `IRowsetChangeImpl`, je nutné nastavit následující vlastnosti na zprostředkovatele. Tyto vlastnosti se používají především `ICommandProperties::SetProperties`k vyžádání rozhraní prostřednictvím .

   - `DBPROP_IRowsetChange`: Nastavení tohoto `DBPROP_IRowsetChange`nastavení se automaticky nastaví .

   - `DBPROP_UPDATABILITY`: Bitová maska určující `IRowsetChange`podporované `SetData` `DeleteRows`metody `InsertRow`na : , , nebo .

   - `DBPROP_CHANGEINSERTEDROWS`: Spotřebitel `IRowsetChange::DeleteRows` může `SetData` volat nebo pro nově vložené řádky.

   - `DBPROP_IMMOBILEROWS`: Sada řádků nezmění pořadí vložených nebo aktualizovaných řádků.

   **Pokud implementujete IRowsetUpdateImpl**

   Pokud provádíte `IRowsetUpdateImpl`, musíte nastavit následující vlastnosti na zprostředkovatele, `IRowsetChangeImpl` kromě nastavení všech vlastností pro dříve uvedené:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: Musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: Musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: Musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: Musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: Musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Pokud podporujete oznámení, můžete mít také některé další vlastnosti; naleznete v `IRowsetNotifyCP` části pro tento seznam.

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Zápis do zdroje dat

Chcete-li číst ze zdroje `Execute` dat, volání funkce. Chcete-li zapisovat `FlushData` do zdroje dat, zavolejte funkci. (V obecném smyslu vyprázdnění znamená uložit změny provedené v tabulce nebo indexu na disk.)

```cpp
FlushData(HROW, HACCESSOR);
```

Popisovač řádku (HROW) a popisovač přistupujícího zařízení (HACCESSOR) argumenty umožňují určit oblast zápisu. Obvykle zapisujete jedno datové pole najednou.

Metoda `FlushData` zapisuje data ve formátu, ve kterém byla původně uložena. Pokud tuto funkci nepřepíšete, bude poskytovatel fungovat správně, ale změny nebudou vyprázdněny do úložiště dat.

### <a name="when-to-flush"></a>Kdy vyprázdnit

Šablony zprostředkovatele volání FlushData vždy, když data je třeba zapsat do úložiště dat; k tomu obvykle (ale ne vždy) dochází v důsledku volání následujících funkcí:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`(pokud jsou do řádku vložena nová data)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Jak to funguje

Příjemce provede volání, které vyžaduje flush (například Update) a toto volání je předán zprostředkovateli, který vždy provede následující:

- Volání `SetDBStatus` vždy, když máte stav hodnotu vázána.

- Zkontroluje příznaky sloupce.

- Volání `IsUpdateAllowed`.

Tyto tři kroky pomáhají zajistit zabezpečení. Pak poskytovatel `FlushData`volá .

### <a name="how-to-implement-flushdata"></a>Jak implementovat FlushData

Chcete-li implementovat `FlushData`, je třeba vzít v úvahu několik otázek:

Ujistěte se, že úložiště dat může zpracovávat změny.

Zpracování hodnot NULL.

### <a name="handling-default-values"></a>Zpracování výchozích hodnot.

Chcete-li `FlushData` implementovat vlastní metodu, musíte:

- Přejděte do třídy sady řádků.

- Do třídy sady řádků vložte deklaraci:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Poskytnout implementaci `FlushData`.

Dobrá implementace `FlushData` ukládá pouze řádky a sloupce, které jsou skutečně aktualizovány. Parametry HROW a HACCESSOR můžete použít k určení aktuálního řádku a sloupce, které jsou uloženy pro optimalizaci.

Obvykle je největší výzvou práce s vlastním nativním úložištěm dat. Pokud je to možné, zkuste:

- Způsob zápisu do úložiště dat udržujte co nejjednodušší.

- Zpracování hodnot NULL (volitelné, ale doporučeno).

- Zpracování výchozích hodnot (volitelné, ale doporučeno).

Nejlepší věc, kterou musíte udělat, je mít skutečné zadané hodnoty v úložišti dat pro hodnoty NULL a výchozí hodnoty. Nejlepší je, pokud můžete extrapolovat tato data. Pokud ne, doporučujeme nepovolit hodnoty NULL a výchozí hodnoty.

Následující příklad ukazuje, jak `FlushData` `RUpdateRowset` je implementována ve třídě v `UpdatePV` ukázce (viz Rowset.h v ukázkovém kódu):

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

Aby poskytovatel mohl zpracovávat změny, musíte nejprve zajistit, aby úložiště dat (například textový soubor nebo videosoubor) mělo k dispozici zařízení, která umožňují provádět změny. Pokud tomu tak není, měli byste vytvořit tento kód odděleně od projektu zprostředkovatele.

### <a name="handling-null-data"></a>Zpracování dat NULL

Je možné, že koncový uživatel odešle data NULL. Při zápisu hodnoty NULL do polí ve zdroji dat může dojít k potenciálním problémům. Představte si, že objednávka-přičemž aplikace, která přijímá hodnoty pro město a PSČ; mohl přijmout jednu nebo obě hodnoty, ale ani jedno, protože v takovém případě by doručení nebylo možné. Proto je třeba omezit určité kombinace hodnot NULL v polích, které mají smysl pro vaši aplikaci.

Jako vývojář zprostředkovatele je třeba zvážit, jak budou tato data ukládat, jak budete tato data číst z úložiště dat a jak je zadáváte uživateli. Konkrétně je třeba zvážit, jak změnit stav dat sady řádků ve zdroji dat (například DataStatus = NULL). Můžete se rozhodnout, jakou hodnotu vrátit, když spotřebitel přistupuje k poli obsahujícímu hodnotu NULL.

Podívejte se na kód v updatePV vzorku; ukazuje, jak zprostředkovatel může zpracovat data NULL. V UpdatePV zprostředkovatel ukládá data NULL zápisem řetězce "NULL" v úložišti dat. Při čtení dat NULL z úložiště dat, vidí, že řetězec a potom vyprázdní vyrovnávací paměti, vytvoření řetězce NULL. Má také `IRowsetImpl::GetDBStatus` přepsání, ve kterém vrátí DBSTATUS_S_ISNULL pokud je tato hodnota dat prázdná.

### <a name="marking-nullable-columns"></a>Označení sloupců s možnou hodnotou Null

Pokud také implementujete sady řádků `IDBSchemaRowsetImpl`schématu (viz ), vaše implementace by měla určit v DBSCHEMA_COLUMNS sada řádků (obvykle označeny ve vašem zprostředkovateli CxxxSchemaColSchemaRowset), že sloupec je nullable.

Je také třeba zadat, že všechny sloupce s možnou `GetColumnInfo`hodnotou null obsahují hodnotu DBCOLUMNFLAGS_ISNULLABLE ve vaší verzi .

V implementaci šablon OLE DB, pokud se vám nepodaří označit sloupce jako nullable, zprostředkovatel předpokládá, že musí obsahovat hodnotu a neumožní spotřebiteli odeslat hodnoty null.

Následující příklad ukazuje, `CommonGetColInfo` jak je funkce implementována v CUpdateCommand (viz UpProvRS.cpp) v UpdatePV. Všimněte si, jak mají sloupce tento DBCOLUMNFLAGS_ISNULLABLE pro sloupce s možnou hodnotou null.

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

Stejně jako u dat NULL máte odpovědnost za změnu výchozích hodnot.

Výchozí `FlushData` a `Execute` je vrátit S_OK. Proto pokud tuto funkci nepřepíšete, změny se zobrazí jako úspěšné (S_OK budou vráceny), ale nebudou přeneseny do úložiště dat.

V `UpdatePV` ukázce (v souboru `SetDBStatus` Rowset.h) metoda zpracovává výchozí hodnoty následujícím způsobem:

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

### <a name="column-flags"></a>Příznaky sloupců

Pokud podporujete výchozí hodnoty ve sloupcích, je třeba \<nastavit\>pomocí metadat ve třídě zprostředkovatele SchemaRowset třídy. Nastavte `m_bColumnHasDefault = VARIANT_TRUE`.

Máte také odpovědnost nastavit příznaky sloupce, které jsou určeny pomocí typu s výčtu DBCOLUMNFLAGS. Příznaky sloupce popisují vlastnosti sloupce.

Například ve `CUpdateSessionColSchemaRowset` třídě `UpdatePV` v (v Session.h) je první sloupec nastaven takto:

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

Tento kód mimo jiné určuje, že sloupec podporuje výchozí hodnotu 0, aby byl zapisovatelný a aby všechna data ve sloupci měla stejnou délku. Pokud chcete, aby data ve sloupci měla proměnnou délku, tento příznak byste nenastavili.

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele TECHNOLOGIE OLE DB](creating-an-ole-db-provider.md)
