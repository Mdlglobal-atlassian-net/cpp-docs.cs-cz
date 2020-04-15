---
title: Makra pro šablony zprostředkovatele OLE DB
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: 5d29b2548102b056a21ebfccb037af3a766788ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369810"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra pro šablony zprostředkovatele OLE DB

Makra zprostředkovatele šablon TECHNOLOGIE OLE DB nabízejí funkce v následujících kategoriích:

## <a name="property-set-map-macros"></a>Makra mapování sady vlastností

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Označuje začátek sady vlastností.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Označuje začátek sady vlastností.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Označuje začátek sady vlastností, která může být skryta nebo definována mimo rozsah zprostředkovatele.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Řetězy skupiny vlastností dohromady.|
|[END_PROPERTY_SET](#end_property_set)|Označuje konec sady vlastností.|
|[END_PROPSET_MAP](#end_propset_map)|Označuje konec mapy sady vlastností.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Nastaví určitou vlastnost v sadě vlastností na výchozí hodnotu.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Nastaví určitou vlastnost v sadě vlastností na hodnotu, kterou jste dodali. Také umožňuje nastavit příznaky a možnosti.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Nastaví určitou vlastnost v sadě vlastností na hodnotu, kterou jste dodali.|

## <a name="column-map-macros"></a>Makra mapování sloupců

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Označuje začátek položek mapy sloupce zprostředkovatele.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Označuje konec položek mapy sloupce zprostředkovatele.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Představuje konkrétní sloupec podporovaný zprostředkovatelem.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Můžete určit datový typ sloupce.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Můžete určit guid guid sady řádků velikosti sloupce, datového typu, přesnosti, měřítka a sady řádků schématu.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Můžete určit velikost sloupce.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Předpokládá, že typ sloupce je řetězec.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Stejně jako PROVIDER_COLUMN_ENTRY_LENGTH, ale také umožňuje určit datový typ sloupce, stejně jako velikost.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Předpokládá, že typ sloupce je řetězec znaků Unicode.|

## <a name="schema-rowset-macros"></a>Makra sady řádků schématu

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Označuje začátek mapy schématu.|
|[END_SCHEMA_MAP](#end_schema_map)|Označuje konec mapy schématu.|
|[SCHEMA_ENTRY](#schema_entry)|Přidruží identifikátor GUID ke třídě.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Označuje začátek vlastnosti nastavené v mapě sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*Identifikátor guid*<br/>
[v] Identifikátor GUID vlastnosti.

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Označuje začátek vlastnosti nastavené v mapě sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parametry

*Identifikátor guid*<br/>
[v] Identifikátor GUID vlastnosti.

*příznaky*<br/>
[v] UPROPSET_HIDDEN pro všechny sady vlastností, které nechcete vystavit nebo UPROPSET_PASSTHROUGH pro zprostředkovatele vystavení vlastnosti definované mimo rozsah zprostředkovatele.

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Označuje začátek položek mapy sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parametry

*Třída*<br/>
[v] Třída, ve které je tato sada vlastností zadána. Sadu vlastností lze zadat v následujících objektech technologie OLE DB:

- [Objekty zdroje dat](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Objekty relace](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Příkazy](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Příklad

Zde je ukázka mapy sady vlastností:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

Toto makro řetězy vlastnost í dohromady.

#### <a name="syntax"></a>Syntaxe

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parametry

*Třída chainclass*<br/>
[v] Název třídy řetězové vlastnosti. Jedná se o třídu generovanou Průvodcem projektem knihovny ATL, která již obsahuje mapu (například třídu objektu relace, příkazu nebo zdroje dat).

#### <a name="remarks"></a>Poznámky

Můžete zřetězit sadu vlastností z jiné třídy do vlastní třídy a pak přistupovat k vlastnostem přímo z vaší třídy.

> [!CAUTION]
> Toto makro používejte střídmě. Nesprávné použití může způsobit, že spotřebitel nezdaří testy shody technologie OLE DB.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Označuje konec sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*Identifikátor guid*<br/>
[v] Identifikátor GUID vlastnosti.

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

Označuje konec položek mapy sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

Představuje konkrétní vlastnost v sadě vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Parametry

*dwPropID*<br/>
[v] Hodnota [DBPROPID,](/previous-versions/windows/desktop/ms723882(v=vs.85)) kterou lze použít ve spojení s identifikátorem GUID sady vlastností k identifikaci vlastnosti.

#### <a name="remarks"></a>Poznámky

Toto makro nastaví `DWORD` hodnotu vlastnosti typu na výchozí hodnotu definovanou v databázi ATLDB. H. Chcete-li nastavit vlastnost na hodnotu podle vašeho výběru, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Chcete-li `VARTYPE` nastavit a [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) pro vlastnost současně, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

Představuje konkrétní vlastnost v sadě vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Parametry

*dwPropID*<br/>
[v] Hodnota [DBPROPID,](/previous-versions/windows/desktop/ms723882(v=vs.85)) kterou lze použít ve spojení s identifikátorem GUID sady vlastností k identifikaci vlastnosti.

*Vt*<br/>
[v] Položka `VARTYPE` této vlastnosti. (Definováno v wtypes.h)

*dwFlags*<br/>
[v] Hodnota [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) popisující tuto položku vlastnosti.

*Hodnotu*<br/>
[v] Hodnota vlastnosti `DWORD`typu .

*Možnosti*<br/>
Buď DBPROPOPTIONS_REQUIRED, nebo DBPROPOPTIONS_SETIFCHEAP. Za normálních okolností zprostředkovatel nemusí nastavit *možnosti,* protože je nastaven spotřebitelem.

#### <a name="remarks"></a>Poznámky

Pomocí tohoto makra můžete přímo určit `DWORD` hodnotu vlastnosti typu, možnosti a příznaky. Chcete-li pouze nastavit vlastnost na výchozí hodnotu definovanou v ATLDB. H, použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Chcete-li nastavit vlastnost na hodnotu podle vašeho výběru, bez nastavení možností nebo příznaků na něm, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

Představuje konkrétní vlastnost v sadě vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>Parametry

*dwPropID*<br/>
[v] Hodnota [DBPROPID,](/previous-versions/windows/desktop/ms723882(v=vs.85)) kterou lze použít ve spojení s identifikátorem GUID sady vlastností k identifikaci vlastnosti.

*Hodnotu*<br/>
[v] Hodnota vlastnosti `DWORD`typu .

#### <a name="remarks"></a>Poznámky

Pomocí tohoto makra můžete přímo určit `DWORD`hodnotu vlastnosti typu . Chcete-li nastavit vlastnost na výchozí hodnotu definovanou v ATLDB. H, použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Chcete-li nastavit hodnotu, příznaky a možnosti vlastnosti, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Označuje začátek položek mapy sloupce zprostředkovatele.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
[v] Název třídy, ke které tato mapa patří.

#### <a name="example"></a>Příklad

Zde je ukázka poskytovatele sloupcové mapy:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Označuje konec položek mapy sloupce zprostředkovatele.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Příklad

Viz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*Členské*<br/>
[v] Členská proměnná v `dataClass` odpovídající sloupci.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*Dbtype*<br/>
[v] Datový typ v [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Členské*<br/>
[v] Členská proměnná, `dataClass` ve které jsou uložena data.

#### <a name="remarks"></a>Poznámky

Umožňuje zadat datový typ sloupce.

#### <a name="example"></a>Příklad

Viz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*příznaky*<br/>
[v] Určuje způsob vrácení dat. Viz `dwFlags` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colVelikost*<br/>
[v] Velikost sloupce.

*Dbtype*<br/>
[v] Označuje datový typ hodnoty. Viz `wType` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Přesnost*<br/>
[v] Označuje přesnost, která má být používána při získávání dat, pokud *dbType* je DBTYPE_NUMERIC nebo DBTYPE_DECIMAL. Viz `bPrecision` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Měřítko*<br/>
[v] Označuje měřítko, které se má použít při získávání dat, pokud dbType je DBTYPE_NUMERIC nebo DBTYPE_DECIMAL. Viz `bScale` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Identifikátor guid*<br/>
Identifikátor GUID sady řádků schématu. Seznam sad řádků schématu a jejich identifikátorů GUID naleznete v sadě řádků schématu [iDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *referenční příručce programátora OLE DB.*

#### <a name="remarks"></a>Poznámky

Umožňuje určit identifikátor GUID sady řádků velikosti sloupce, datového typu, přesnosti, měřítka a sady řádků schématu.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*Velikost*<br/>
[v] Velikost sloupce v bajtů.

*Členské*<br/>
[v] Členská proměnná, ve `dataClass` které jsou uložena data sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje určit velikost sloupce.

#### <a name="example"></a>Příklad

Viz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*Členské*<br/>
[v] Členská proměnná ve třídě dat, která data ukládá.

#### <a name="remarks"></a>Poznámky

Toto makro použijte, pokud se předpokládá, že data sloupce jsou [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

#### <a name="example"></a>Příklad

Viz [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*Dbtype*<br/>
[v] Datový typ v [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Velikost*<br/>
[v] Velikost sloupce v bajtů.

*Členské*<br/>
[v] Členská proměnná ve třídě dat, která data ukládá.

#### <a name="remarks"></a>Poznámky

Podobně jako [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) ale také umožňuje určit datový typ sloupce a velikost.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
[v] Název sloupce.

*Pořadové*<br/>
[v] Číslo sloupce. Pokud se nejedná o sloupec Záložka, nesmí být číslo sloupce 0.

*Členské*<br/>
[v] Členská proměnná ve třídě dat, která data ukládá.

#### <a name="remarks"></a>Poznámky

Toto makro použijte, pokud jsou data sloupce nulovým ukončeným řetězcem znaků Unicode [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Označuje začátek mapy schématu.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parametry

*Třída schématu*<br/>
Třída, která obsahuje MAP. Obvykle se jedná o třídu relace.

#### <a name="remarks"></a>Poznámky

Další informace o sadách řádků schématu naleznete v sadě [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v sadě Windows SDK.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Označuje konec mapy schématu.

#### <a name="syntax"></a>Syntaxe

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [IDBSchemaRowsetImpl Class](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Přidruží identifikátor GUID ke třídě.

#### <a name="syntax"></a>Syntaxe

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parametry

*Identifikátor guid*<br/>
Identifikátor GUID sady řádků schématu. Seznam sad řádků schématu a jejich identifikátorů GUID naleznete v sadě řádků schématu [iDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *referenční příručce programátora OLE DB.*

*třída řádků*<br/>
Třída, která bude vytvořena k reprezentaci sady řádků schématu.

#### <a name="remarks"></a>Poznámky

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) pak můžete dotaz na mapu pro seznam identifikátorů GUID, nebo může vytvořit sadu řádků, pokud je uveden identifikátor GUID. Sada řádků schématu `IDBSchemaRowsetImpl` vytvoří je podobný `CRowsetImpl`standard-odvozené třídy, s `Execute` tím rozdílem, že musí poskytnout metodu, která má následující podpis:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Tato `Execute` funkce naplní data sady řádků. Průvodce projektem knihovny ATL vytvoří, jak je popsáno v [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *ole DB programmer odkaz*, tři počáteční sady řádků schématu v projektu pro každý ze tří povinných schémat TECHNOLOGIE OLE DB:

- Dbschema_tables

- Dbschema_columns

- Dbschema_provider_types

Průvodce také přidá tři odpovídající položky v mapě schématu. Další informace o vytvoření zprostředkovatele pomocí průvodce naleznete [v tématu Vytvoření zprostředkovatele šablony technologie OLE DB.](../../data/oledb/creating-an-ole-db-provider.md)

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatelů OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Vytvoření zprostředkovatele TECHNOLOGIE OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Odkaz na šablony zprostředkovatelů OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Makra pro šablony zprostředkovatelů technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)
