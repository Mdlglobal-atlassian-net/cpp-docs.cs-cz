---
title: Vytvoření aktualizovatelného zprostředkovatele
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 2811cd56bdc87282b9d4395a9a79ba9b333dadee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211390"
---
# <a name="creating-an-updatable-provider"></a>Vytvoření aktualizovatelného zprostředkovatele

Vizuál C++ podporuje aktualizovatelné zprostředkovatele nebo poskytovatele, kteří můžou aktualizovat (zapisovat do) úložiště dat. Toto téma popisuje, jak vytvořit aktualizovatelné zprostředkovatele pomocí šablon OLE DB.

V tomto tématu se předpokládá, že začínáte s funkčním zprostředkovatelem. Existují dva kroky pro vytvoření aktualizovatelného zprostředkovatele. Nejprve musíte určit, jak bude poskytovatel provádět změny v úložišti dat; konkrétně bez ohledu na to, jestli se změny mají provést hned nebo odložit, dokud se nevydá příkaz k aktualizaci. Oddíl "[vytváření aktualizovatelných zprostředkovatelů](#vchowmakingprovidersupdatable)" popisuje změny a nastavení, které je třeba provést v kódu poskytovatele.

V dalším kroku se musíte ujistit, že váš poskytovatel obsahuje všechny funkce pro podporu cokoli, co si ho příjemce může vyžádat. Pokud chce příjemce aktualizovat úložiště dat, poskytovatel musí obsahovat kód, který uchovává data v úložišti dat. Například můžete použít knihovnu run-time jazyka C nebo MFC k provedení takových operací na zdroji dat. Oddíl "[zápis do zdroje dat](#vchowwritingtothedatasource)" popisuje, jak zapisovat do zdroje dat, pracovat s hodnotami null a výchozích hodnot a nastavit příznaky sloupců.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) je příkladem aktualizovatelného zprostředkovatele. UpdatePV je stejná jako MyProv, ale s aktualizovatelnou podporou.

##  <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Vytváření aktualizovatelných zprostředkovatelů

Klíč k provedení aktualizovatelného zprostředkovatele je porozumění operacím, které chcete, aby poskytovatel prováděl v úložišti dat a jak chcete, aby poskytovatel prováděl tyto operace. Konkrétně závažná chyba je, jestli se aktualizace úložiště dat mají dělat hned nebo odložit (v dávce) až do vydání příkazu Update.

Musíte se nejprve rozhodnout, zda má být děděna z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl` ve vaší třídě sady řádků. V závislosti na tom, které z těchto možností implementujete, budou ovlivněny funkce tří metod: `SetData`, `InsertRows`a `DeleteRows`.

- Pokud dědíte z [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), volání těchto tří metod okamžitě změní úložiště dat.

- Pokud převezmete z [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), metody odloží změny do úložiště dat, dokud nebudete volat `Update`, `GetOriginalData`nebo `Undo`. Pokud aktualizace zahrnuje několik změn, provedou se v dávkovém režimu (Všimněte si, že dávkové změny můžou znamenat značnou režii v paměti).

Všimněte si, že `IRowsetUpdateImpl` jsou odvozeny z `IRowsetChangeImpl`. Proto `IRowsetUpdateImpl` poskytuje možnost změny a funkce dávky.

### <a name="to-support-updatability-in-your-provider"></a>Podpora možností aktualizace ve zprostředkovateli

1. V třídě sady řádků dědí z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl`. Tyto třídy poskytují vhodná rozhraní pro změnu úložiště dat:

   **Přidání IRowsetChange**

   Pomocí tohoto formuláře přidejte `IRowsetChangeImpl` do svého řetězce dědičnosti:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Přidejte také `COM_INTERFACE_ENTRY(IRowsetChange)` do oddílu `BEGIN_COM_MAP` ve vaší třídě sady řádků.

   **Přidání IRowsetUpdate**

   Pomocí tohoto formuláře přidejte `IRowsetUpdate` do svého řetězce dědičnosti:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > `IRowsetChangeImpl` řádek byste měli odebrat z řetězce dědičnosti. Tato výjimka z výše zmíněné směrnice musí zahrnovat kód pro `IRowsetChangeImpl`.

1. Přidejte následující do mapy COM (`BEGIN_COM_MAP ... END_COM_MAP`):

   |  Pokud implementujete   |           Přidat k mapě modelu COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Pokud implementujete | Přidat k mapě sady vlastností |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. V příkazu přidejte následující do mapy sady vlastností (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):

   |  Pokud implementujete   |                                             Přidat k mapě sady vlastností                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. V mapě sady vlastností byste měli také zahrnout všechna následující nastavení, jak jsou uvedena níže:

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

   Hodnoty používané v těchto voláních makra můžete najít tak, že v Atldb. h vyhledáte ID a hodnoty vlastností (Pokud se Atldb. h liší od online dokumentace, Atldb. h nahrazuje dokumentaci).

   > [!NOTE]
   > Mnohé z nastavení `VARIANT_FALSE` a `VARIANT_TRUE` jsou vyžadovány šablonami OLE DB; Specifikace OLE DB říká, že může být pro čtení a zápis, ale šablony OLE DB můžou podporovat jenom jednu hodnotu.

   **Pokud implementujete IRowsetChangeImpl**

   Pokud implementujete `IRowsetChangeImpl`, musíte na svém poskytovateli nastavit následující vlastnosti. Tyto vlastnosti se primárně používají k vyžádání rozhraní prostřednictvím `ICommandProperties::SetProperties`.

   - `DBPROP_IRowsetChange`: Toto nastavení automaticky nastaví `DBPROP_IRowsetChange`.

   - `DBPROP_UPDATABILITY`: Bitová maska, která určuje podporované metody pro `IRowsetChange`: `SetData`, `DeleteRows`nebo `InsertRow`.

   - `DBPROP_CHANGEINSERTEDROWS`: příjemce může pro nově vložené řádky volat `IRowsetChange::DeleteRows` nebo `SetData`.

   - `DBPROP_IMMOBILEROWS`: sada řádků nebude přeuspořádat vložené nebo aktualizované řádky.

   **Pokud implementujete IRowsetUpdateImpl**

   Pokud implementujete `IRowsetUpdateImpl`, musíte kromě nastavení všech vlastností `IRowsetChangeImpl` uvedených v tomto poskytovateli nastavit následující vlastnosti:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: musí být READ_ONLY a VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Pokud budete podporovat oznámení, můžete také mít i některé další vlastnosti. seznam najdete v části `IRowsetNotifyCP`.

##  <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Zápis do zdroje dat

Chcete-li číst ze zdroje dat, zavolejte funkci `Execute`. Chcete-li zapisovat do zdroje dat, zavolejte funkci `FlushData`. (Obecně platí, že vyprázdní znamená, že se změny provedené v tabulce nebo indexu uloží na disk.)

```cpp
FlushData(HROW, HACCESSOR);
```

Argumenty popisovač řádku (HROW) a popisovač přistupujícího objektu (HACCESSOR) umožňují zadat oblast, která se má zapsat. Obvykle napíšete jedno datové pole najednou.

Metoda `FlushData` zapisuje data ve formátu, ve kterém byla původně uložena. Pokud tuto funkci nepřepisujete, poskytovatel bude správně fungovat, ale změny nebudou vyprázdněny do úložiště dat.

### <a name="when-to-flush"></a>Kdy se má vyprázdnit

Šablony poskytovatele volají FlushData vždy, když je nutné zapsat data do úložiště dat; k tomu obvykle dochází (ale ne vždy) v důsledku volání následujících funkcí:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (pokud existují nová data, která se mají vložit do řádku)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Jak to funguje

Příjemce provede volání, které vyžaduje vyprázdnění (například aktualizace) a toto volání je předáno poskytovateli, který vždy provede následující:

- Volá `SetDBStatus` vždy, když máte vázanou hodnotu stavu.

- Kontroluje příznaky sloupce.

- Volá `IsUpdateAllowed`.

Tyto tři kroky vám pomůžou zajistit zabezpečení. Poté zprostředkovatel zavolá `FlushData`.

### <a name="how-to-implement-flushdata"></a>Jak implementovat FlushData

K implementaci `FlushData`musíte vzít v úvahu několik problémů:

Ujistěte se, že úložiště dat může zpracovávat změny.

Zpracování hodnot NULL.

### <a name="handling-default-values"></a>Zpracování výchozích hodnot.

Chcete-li implementovat vlastní metodu `FlushData`, je nutné provést následující kroky:

- Přejít do vaší třídy sady řádků.

- Do třídy sady řádků vložte deklaraci:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Poskytněte implementaci `FlushData`.

Dobrá implementace `FlushData` ukládá pouze řádky a sloupce, které jsou skutečně aktualizovány. Pomocí parametrů HROW a HACCESSOR lze určit aktuální řádek a sloupec, který je uložen pro optimalizaci.

Největší výzvou často funguje s vaším vlastním nativním úložištěm dat. Pokud je to možné, zkuste:

- Ponechte metodu zapisování do úložiště dat co nejjednodušší.

- Zpracování hodnot NULL (volitelné, ale doporučené).

- Zpracuje výchozí hodnoty (volitelné, ale doporučené).

Nejlepší je, aby v úložišti dat byly skutečné zadané hodnoty pro hodnoty NULL a výchozí hodnoty. Je to nejlepší, pokud tato data můžete odvodit. V takovém případě doporučujeme, abyste nepovolili hodnoty NULL a výchozí hodnoty.

Následující příklad ukazuje, jak je implementována `FlushData` ve třídě `RUpdateRowset` v ukázce `UpdatePV` (viz Rowset. h v ukázkovém kódu):

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

Aby mohl váš poskytovatel zpracovávat změny, musíte nejdřív zkontrolovat, že úložiště dat (například textový soubor nebo videosoubor) má zařízení, které vám umožní provádět na něm změny. Pokud tomu tak není, měli byste vytvořit tento kód odděleně od projektu poskytovatele.

### <a name="handling-null-data"></a>Zpracování dat s hodnotou NULL

Je možné, že koncový uživatel bude odesílat data NULL. Když zapisujete hodnoty NULL do polí ve zdroji dat, může docházet k potenciálním problémům. Představte si aplikaci s objednávkami, která přijímá hodnoty pro město a poštovní směrovací číslo. může přijmout buď jednu, nebo obě hodnoty, ale ne ani, protože v takovém případě by nebylo možné doručení způsobit. Proto je nutné omezit určité kombinace hodnot NULL v polích, která jsou vhodná pro vaši aplikaci.

Jako vývojář poskytovatele musíte zvážit, jak budete ukládat tato data, jak budete číst tato data z úložiště dat a jak je určíte pro uživatele. Konkrétně musíte zvážit, jak změnit stav dat dat sady řádků ve zdroji dat (například DataStatus = NULL). Rozhodnete, jaká hodnota se má vrátit, když spotřebitel přistupuje k poli obsahujícímu hodnotu NULL.

Podívejte se na kód v ukázce UpdatePV; ukazuje, jak může zprostředkovatel zpracovat data s hodnotou NULL. V UpdatePV poskytovatel ukládá prázdná data zápisem řetězce "NULL" v úložišti dat. Když čte data NULL z úložiště dat, uvidí tento řetězec a pak vyprázdní vyrovnávací paměť a vytvoří řetězec s hodnotou NULL. Má také přepsání `IRowsetImpl::GetDBStatus`, ve kterém vrátí DBSTATUS_S_ISNULL, pokud je tato hodnota dat prázdná.

### <a name="marking-nullable-columns"></a>Označení sloupců s možnou hodnotou null

Pokud implementujete i sady řádků schématu (viz `IDBSchemaRowsetImpl`), měla by vaše implementace určovat v DBSCHEMA_COLUMNS sadě řádků (obvykle označené poskytovatelem CxxxSchemaColSchemaRowset), že sloupec může mít hodnotu null.

Musíte také určit, že všechny sloupce s možnou hodnotou null obsahují hodnotu DBCOLUMNFLAGS_ISNULLABLE ve vaší verzi `GetColumnInfo`.

Pokud v implementaci šablon OLE DB neoznačíte sloupce jako Nullable, zprostředkovatel předpokládá, že musí obsahovat hodnotu a neumožní příjemci odesílat hodnoty null.

Následující příklad ukazuje, jak je funkce `CommonGetColInfo` implementována v CUpdateCommand (viz UpProvRS. cpp) v UpdatePV. Všimněte si, že tyto sloupce mají tento DBCOLUMNFLAGS_ISNULLABLE pro sloupce s možnou hodnotou null.

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

Stejně jako u dat s hodnotou NULL máte odpovědnost za to, abyste se zabývat měnícími se výchozími hodnotami.

Výchozí hodnotou `FlushData` a `Execute` je vrácení S_OK. Proto pokud tuto funkci nepřepisujete, změny se zobrazí jako úspěšné (S_OK budou vráceny), ale nebudou přeneseny do úložiště dat.

V ukázce `UpdatePV` (v Rowset. h) metoda `SetDBStatus` zpracovává výchozí hodnoty následujícím způsobem:

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

Pokud ve sloupcích podporujete výchozí hodnoty, je nutné ji nastavit pomocí metadat ve třídě poskytovatele \<\>třídy SchemaRowset. Nastavte `m_bColumnHasDefault = VARIANT_TRUE`.

Máte také odpovědnost za nastavení příznaků sloupců, které jsou zadány pomocí výčtového typu DBCOLUMNFLAGS. Příznaky sloupce popisují charakteristiky sloupců.

Například ve třídě `CUpdateSessionColSchemaRowset` v `UpdatePV` (v Session. h) se nastaví první sloupec tímto způsobem:

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

Tento kód určuje mimo jiné, že sloupec podporuje výchozí hodnotu 0, že je zapisovatelný a že všechna data ve sloupci mají stejnou délku. Pokud chcete, aby data ve sloupci měla proměnlivou délku, nemusíte tento příznak nastavit.

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele OLE DB](creating-an-ole-db-provider.md)
