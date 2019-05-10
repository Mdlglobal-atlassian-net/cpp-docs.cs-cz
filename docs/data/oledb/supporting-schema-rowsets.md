---
title: Podpora sad řádků schématu
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 09af59d97ab87c66a0a7096e72cc7b92bc3a5dbf
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525274"
---
# <a name="supporting-schema-rowsets"></a>Podpora sad řádků schématu

Sady řádků schématu umožní uživatelům získat informace o úložišti dat bez znalosti jeho základní strukturu nebo schéma. Úložiště dat může mít například tabulky, které jsou uspořádány do uživatelem definované hierarchie, aby se žádný způsob, jak zajistit znalosti o schématu s výjimkou tím, že jeho čtení. (Jako například průvodců aplikace Visual C++ pomocí sad řádků schématu generovat přístupové objekty pro spotřebitele.) Objekt relace poskytovatele umožňující příjemci k tomu zveřejňuje metody na [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) rozhraní. V aplikacích Visual C++, použijte [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) třídu pro implementaci `IDBSchemaRowset`.

`IDBSchemaRowsetImpl` podporuje následující způsoby:

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) kontroluje platnost omezení pro sadu řádků schématu.

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementuje funkci objektu modelu COM pro objekt zadaný parametrem šablony.

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) Určuje, která omezení podpory pro sadu řádků schématu konkrétní.

- [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) vrací sadu řádků schématu (zděděno z rozhraní).

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) vrátí seznam sad řádků schématu přístupné `IDBSchemaRowsetImpl::GetRowset` (zděděno z rozhraní).

## <a name="atl-ole-db-provider-wizard-support"></a>Podpora průvodce pro zprostředkovatele ATL OLE DB

::: moniker range="vs-2019"

Průvodce zprostředkovatele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="vs-2017"

**Průvodce zprostředkovatelem ATL OLE DB** vytvoří tři třídy schématu v hlavičkovém souboru relace:

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

Tyto třídy reagovat na žádosti uživatelů pro informace o schématu; Všimněte si, že specifikaci OLE DB vyžaduje podporovat tyto tři sady řádků schématu:

- **C**<em>ShortName</em>**SessionTRSchemaRowset** zpracovává požadavky pro informace o tabulce (DBSCHEMA_TABLES sadu řádků schématu).

- **C**<em>ShortName</em>**SessionColSchemaRowset** zpracovává požadavky pro informace o sloupcích (sada řádků schématu DBSCHEMA_COLUMNS). Průvodce poskytuje ukázková implementace pro tyto třídy, které vracejí informace o schématu pro zprostředkovatele DOS.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** zpracovává požadavky schématu informace o typu zprostředkovatele rozhraní (DBSCHEMA_PROVIDER_TYPES sadu řádků schématu). Výchozí implementace zadaným průvodcem vrátí hodnotu S_OK.

Můžete přizpůsobit tyto třídy pro zpracování informací o schématu pro poskytovatele:

- V **C**<em>ShortName</em>**SessionTRSchemaRowset**, musíte vyplnit pole katalogu, tabulky a popis (`trData.m_szType`, `trData.m_szTable`a `trData.m_szDesc`). V příkladu generované v Průvodci se používá pouze jeden řádek (tabulka). Ostatní zprostředkovatelé může vrátit více než jednou tabulkou.

- V **C**<em>ShortName</em>**SessionColSchemaRowset**, předejte název tabulky jako `DBID`.

::: moniker-end

## <a name="setting-restrictions"></a>Nastavení omezení

Důležitý koncept v Podpora sad řádků schématu se nastavování omezení, které provedete pomocí `SetRestrictions`. Omezení povolit uživatelům načítat pouze odpovídající řádky (například vyhledat všechny sloupce v tabulce "MyTable"). Omezení jsou volitelné a v případě, ve které nejsou podporovány (výchozí), vždy vrátí se všechna data. Příklad poskytovatele, který nepodporuje omezení, najdete v článku [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku.

## <a name="setting-up-the-schema-map"></a>Nastavení mapování schématu

Mapa schématu, jako je například tento v Session.h v UpdatePV nastavení:

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Pro podporu `IDBSchemaRowset`, musí podporovat DBSCHEMA_TABLES DBSCHEMA_COLUMNS a DBSCHEMA_PROVIDER_TYPES. Můžete přidat další sady řádků schématu na vašem uvážení.

Deklarovat třídu sady řádků schématu s `Execute` metody, jako `CUpdateSessionTRSchemaRowset` v `UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` dědí z `IDBSchemaRowsetImpl`, takže má metody zpracování omezení. Pomocí `CSchemaRowsetImpl`, deklarujte tři podřízené třídy (uvedené v mapě schématu výše): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, a `CUpdateSessionPTSchemaRowset`. Každá z těchto podřízených tříd má `Execute` metoda, která zpracovává jeho odpovídající sadu omezení (kritéria vyhledávání). Každý `Execute` metoda srovnává hodnoty *cRestrictions* a *rgRestrictions* parametry. Zobrazit popis těchto parametrů v [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

Další informace o tom, které odpovídají omezení řádků konkrétní schématu naleznete v tabulce sada řádků schématu GUID v [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v **OLE DB referenční informace pro programátory** v sadě Windows SDK .

Například pokud se podporuje omezení TABLE_NAME na DBSCHEMA_TABLES, provedli byste následující:

Nejprve vyhledat DBSCHEMA_TABLES a podívejte se, že podporuje čtyři omezení (v pořadí).

|Omezení sady řádků schématu|Hodnota omezení|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (binární 1)|
|TABLE_SCHEMA|0x2 (binární 10)|
|TABLE_NAME|0x4 (binární 100)|
|TABLE_TYPE|0x8 (binární 1000)|

V dalším kroku je jeden bit pro každé omezení. Vzhledem k tomu, že chcete podporovat pouze TABLE_NAME, vracel 0x4 v `rgRestrictions` elementu. Pokud je Podporovaná TABLE_CATALOG a TABLE_NAME, vracel 0x5 (binární 101).

Ve výchozím nastavení implementace, vrátí hodnotu 0 (nepodporuje žádné omezení) u všech žádostí. UpdatePV je příkladem zprostředkovatele, který nepodporuje omezení.

### <a name="example"></a>Příklad

Tento kód je převzatý z [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku. `UpdatePv` podporuje tři požadované sady řádků schématu: DBSCHEMA_TABLES DBSCHEMA_COLUMNS a DBSCHEMA_PROVIDER_TYPES. Jako příklad toho, jak implementovat podporu schématu ve zprostředkovateli Toto téma vás provede implementací DBSCHEMA_TABLE sady řádků.

> [!NOTE]
> Vzorový kód se mohou lišit od zde; uvedeného vzorový kód by měl považovat za aktuálnější verzi.

Prvním krokem při přidávání podpory schématu je určit, která omezení budete podporovat. Pokud chcete zjistit, která omezení jsou k dispozici pro vaši sadu řádků schématu, podívejte se na specifikaci OLE DB pro definici `IDBSchemaRowset`. Následující definici hlavní zobrazí tabulku obsahující název sady řádků schématu, počet omezení a omezení sloupce. Vyberte sadu řádků schématu, které chcete podporovat a poznamenejte si počet omezení a omezení sloupce. Například DBSCHEMA_TABLES podporuje čtyři omezení (TABLE_CATALOG TABLE_SCHEMA, TABLE_NAME a TABLE_TYPE):

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

Bit představuje každý sloupec omezení. Pokud chcete zajistit podporu omezení (to znamená, můžete zadávat dotazy pomocí ní), nastavte tento bit na hodnotu 1. Pokud nechcete, aby pro podporu omezení, nastavte tento bit na hodnotu nula. Z řádku kódu výše `UpdatePV` podporuje omezení TABLE_NAME a TABLE_TYPE pro DBSCHEMA_TABLES řádků. Toto jsou třetí (bitová maska 100) a čtvrtý omezení (bitová maska 1000). Proto bitové masky pro `UpdatePv` 1100 (nebo 0x0C):

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

Následující `Execute` funkce je podobné těm v pravidelných sady řádků. Budete mít tři argumenty: *pcRowsAffected*, *cRestrictions*, a *rgRestrictions*. *PcRowsAffected* proměnná je výstupní parametr, že zprostředkovatel může vrátit počet řádků v sadě řádků schématu. *CRestrictions* parametr je vstupní parametr obsahující počet omezení uživatelem je předána zprostředkovateli. *RgRestrictions* je parametr pole hodnot typu VARIANT, které obsahují hodnoty omezení.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

*CRestrictions* je proměnná založená na celkovém počtu omezení pro sadu řádků schématu, bez ohledu na to, zda je zprostředkovatel podporuje. Protože UpdatePv podporuje dvě omezení (třetí a čtvrtý), tento kód jenom vyhledá *cRestrictions* hodnotu větší než nebo rovna hodnotě tři.

Hodnota pro omezení TABLE_NAME je uložena v *rgRestrictions [2]* (třetí omezení v pole s nulovým základem je opět, 2). Zkontrolujte, že omezení není VT_EMPTY ve skutečnosti se na ně. Všimněte si, že není roven VT_EMPTY VT_NULL. VT_NULL Určuje platnou hodnotu omezení.

`UpdatePv` Definice název tabulky není plně kvalifikovaná cesta název do textového souboru. Extrahuje hodnotu omezení a poté otevřete soubor a ujistěte se, že soubor skutečně existuje. Pokud soubor neexistuje, vrátí hodnotu S_OK. To může zdát trochu zpětně ale jaký kód je ve skutečnosti sděluje příjemce je, že nebyly žádné podporované tabulky pomocí zadaného názvu. Vrátit hodnotu S_OK znamená, že se kód správně spustil.

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

Podpora čtvrtý omezení (TABLE_TYPE) je podobný třetí omezení. Zkontrolujte, zda hodnota není VT_EMPTY. Toto omezení vrátí pouze typ tabulky tabulky. Chcete-li určit platné hodnoty pro DBSCHEMA_TABLES, podívejte **dodatku B** z **OLE DB referenční informace pro programátory** v části sady řádků tabulky.

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

Toto je ve skutečnosti vytvoříte položku řádku v sadě řádků. Proměnná `trData` odpovídá `CTABLESRow`, struktuře definované v šablonách OLE DB poskytovatele. `CTABLESRow` odpovídá definici sady řádků tabulky v **dodatku B** specifikace OLE DB. Máte jenom jeden řádek přidat, protože najednou může podporovat jenom jedna tabulka.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` Nastaví pouze tři sloupce: TABLE_NAME TABLE_TYPE a popis. Poznamenejte si sloupců, které vrací informace, protože tyto informace budete potřebovat, Pokud implementujete `GetDBStatus`:

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

`GetDBStatus` Funkce je důležitá pro správné fungování sady řádků schématu. Protože data pro každý sloupec nevracejte v sadě řádků tabulky, budete muset určit sloupce, které vrátí data pro a které ne.

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

Protože vaše `Execute` funkce vrátí data pro pole TABLE_NAME TABLE_TYPE a popis z řádků tabulky, můžete se podívat **dodatku B** specifikace OLE DB a určit (podle počtu shora) že jsou to řadové číslovky 3, 4 a 6. Pro každý z těchto sloupců vrátí DBSTATUS_S_OK. Pro všechny ostatní sloupce vrátí DBSTATUS_S_ISNULL. Je důležité se vraťte tento stav, protože příjemce je nemusí umět, že se vrátíte hodnotu NULL nebo něco jiného. Znovu si všimněte, že není shodná s prázdnou hodnotu NULL.

Další informace o rozhraní OLE DB schématu sady řádků, najdete v článku [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) rozhraní v **OLE DB referenční informace pro programátory**.

Informace o tom, jak můžou zákazníci používají `IDBSchemaRowset` metody, naleznete v tématu [získávání metadat pomocí sad řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Příklad poskytovatele, který podporuje sad řádků schématu, najdete v článku [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku.

## <a name="see-also"></a>Viz také:

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)
