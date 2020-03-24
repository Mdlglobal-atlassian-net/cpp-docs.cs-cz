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
ms.openlocfilehash: 2fda4d9f003e84247527d964685e631532d4c366
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210142"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra pro šablony zprostředkovatele OLE DB

Makra poskytovatele OLE DB šablon nabízí funkce v následujících kategoriích:

## <a name="property-set-map-macros"></a>Nastavení vlastností – makra mapování

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Označuje začátek sady vlastností.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Označuje začátek sady vlastností.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Označí začátek sady vlastností, která může být skrytá nebo definovaná mimo obor poskytovatele.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Řetězí skupiny vlastností dohromady.|
|[END_PROPERTY_SET](#end_property_set)|Označuje konec sady vlastností.|
|[END_PROPSET_MAP](#end_propset_map)|Označuje konec mapy sady vlastností.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Nastaví určitou vlastnost ve vlastnosti nastavenou na výchozí hodnotu.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Nastaví určitou vlastnost v sadě vlastností nastavenou na hodnotu poskytnutou vámi. Také umožňuje nastavit příznaky a možnosti.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Nastaví určitou vlastnost v sadě vlastností nastavenou na hodnotu poskytnutou vámi.|

## <a name="column-map-macros"></a>Makra map sloupců

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Označí začátek položek mapování sloupce zprostředkovatele.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Označuje konec položek mapování sloupce zprostředkovatele.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Představuje konkrétní sloupec podporovaný zprostředkovatelem.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Můžete zadat datový typ sloupce.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Můžete zadat velikost sloupce, datový typ, přesnost, měřítko a identifikátor GUID sady řádků schématu.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Můžete určit velikost sloupce.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Předpokládá, že typ sloupce je řetězec.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Stejně jako PROVIDER_COLUMN_ENTRY_LENGTH, ale také umožňuje určit datový typ sloupce i velikost.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Představuje konkrétní sloupec podporovaný zprostředkovatelem. Předpokládá, že typ sloupce je řetězec znaků Unicode.|

## <a name="schema-rowset-macros"></a>Makra sady řádků schématu

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Označuje začátek mapy schématu.|
|[END_SCHEMA_MAP](#end_schema_map)|Označuje konec mapy schématu.|
|[SCHEMA_ENTRY](#schema_entry)|Přidruží identifikátor GUID ke třídě.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Označí začátek sady vlastností v mapě sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID vlastnosti

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Označí začátek sady vlastností v mapě sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID vlastnosti

*Flag*<br/>
pro UPROPSET_HIDDEN pro jakékoli sady vlastností, které nechcete zveřejnit, nebo UPROPSET_PASSTHROUGH pro zprostředkovatele, který vystavuje vlastnosti definované mimo obor poskytovatele.

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Označuje začátek nastavení vlastností položek mapy.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parametry

*Deník*<br/>
pro Třída, ve které je tato sada vlastností určena. Sadu vlastností lze zadat v následujících objektech OLE DB:

- [Objekty zdroje dat](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Objekty relace](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Příkaz](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Příklad

Tady je ukázka mapy sady vlastností:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

Toto makro zřetězí skupiny vlastností dohromady.

#### <a name="syntax"></a>Syntaxe

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parametry

*ChainClass*<br/>
pro Název třídy, pro kterou řetězení vlastností. Toto je třída vygenerovaná průvodcem projektem ATL, která již obsahuje mapu (jako je například relace, příkaz nebo třída objektu zdroje dat).

#### <a name="remarks"></a>Poznámky

Můžete zřetězit sadu vlastností z jiné třídy na vlastní třídu a pak přistupovat k vlastnostem přímo z vaší třídy.

> [!CAUTION]
>  Toto makro používejte zřídka. Nesprávné použití může způsobit, že se příjemci nedaří OLE DB testy shody.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Označuje konec sady vlastností.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
pro Identifikátor GUID vlastnosti

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
pro Hodnota [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) , kterou lze použít ve spojení s identifikátorem GUID sady vlastností k identifikaci vlastnosti.

#### <a name="remarks"></a>Poznámky

Toto makro nastaví hodnotu vlastnosti typu `DWORD` na výchozí hodnotu definovanou v ATLDB. Y. Chcete-li nastavit vlastnost na hodnotu, kterou zvolíte, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Chcete-li nastavit `VARTYPE` a [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) pro vlastnost ve stejnou dobu, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

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
pro Hodnota [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) , kterou lze použít ve spojení s identifikátorem GUID sady vlastností k identifikaci vlastnosti.

*terminálu*<br/>
pro `VARTYPE` této položky vlastnosti (Definováno v wtypes. h)

*dwFlags*<br/>
pro Hodnota [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) popisující tuto položku Vlastnosti.

*value*<br/>
pro Hodnota vlastnosti typu `DWORD`.

*nastavení*<br/>
Buď DBPROPOPTIONS_REQUIRED, nebo DBPROPOPTIONS_SETIFCHEAP. V normálním případě poskytovatel nemusí nastavovat *Možnosti* , protože je nastaven příjemcem.

#### <a name="remarks"></a>Poznámky

Pomocí tohoto makra můžete přímo zadat hodnotu vlastnosti typu `DWORD` a také možnosti a příznaky. Chcete-li pouze nastavit vlastnost na výchozí hodnotu definovanou v ATLDB. H použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Chcete-li nastavit vlastnost na hodnotu podle vlastního výběru bez nastavení možností nebo příznaků, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

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
pro Hodnota [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) , kterou lze použít ve spojení s identifikátorem GUID sady vlastností k identifikaci vlastnosti.

*value*<br/>
pro Hodnota vlastnosti typu `DWORD`.

#### <a name="remarks"></a>Poznámky

Pomocí tohoto makra můžete přímo zadat hodnotu vlastnosti typu `DWORD`. Chcete-li nastavit vlastnost na výchozí hodnotu definovanou v ATLDB. H použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Chcete-li nastavit hodnotu, příznaky a možnosti pro vlastnost, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Příklad

Viz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Označí začátek položek mapování sloupce zprostředkovatele.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
pro Název třídy, do které tato mapa patří.

#### <a name="example"></a>Příklad

Tady je mapa sloupce ukázkového poskytovatele:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Označuje konec položek mapování sloupce zprostředkovatele.

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
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*člen*<br/>
pro Členská proměnná v `dataClass` odpovídající sloupci.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*DbType*<br/>
pro Datový typ v [DbType](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*člen*<br/>
pro Členská proměnná v `dataClass`, která ukládá data.

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
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*Flag*<br/>
pro Určuje způsob, jakým se vrátí data. Podívejte se na popis `dwFlags` ve [strukturách DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize*<br/>
pro Velikost sloupce

*DbType*<br/>
pro Určuje datový typ hodnoty. Podívejte se na popis `wType` ve [strukturách DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*číslic*<br/>
pro Určuje přesnost, která se má použít při získávání dat, je-li nastavena hodnota *dbType* DBTYPE_NUMERIC nebo DBTYPE_DECIMAL. Podívejte se na popis `bPrecision` ve [strukturách DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*kapacity*<br/>
pro Určuje měřítko, které má být použito při získávání dat, je-li nastavena hodnota dbType DBTYPE_NUMERIC nebo DBTYPE_DECIMAL. Podívejte se na popis `bScale` ve [strukturách DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*hlavních*<br/>
Identifikátor GUID sady řádků schématu. Seznam sad řádků schématu a jejich identifikátorů GUID naleznete v části [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *Referenční příručce OLE DB programátor* .

#### <a name="remarks"></a>Poznámky

Umožňuje určit velikost sloupce, datový typ, přesnost, měřítko a identifikátor GUID sady řádků schématu.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*hodnota*<br/>
pro Velikost sloupce v bajtech

*člen*<br/>
pro Členská proměnná v `dataClass`, která ukládá data sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje zadat velikost sloupce.

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
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*člen*<br/>
pro Členská proměnná v datové třídě, která ukládá data.

#### <a name="remarks"></a>Poznámky

Toto makro použijte, když se předpokládá, že jsou data sloupce [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

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
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*DbType*<br/>
pro Datový typ v [DbType](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*hodnota*<br/>
pro Velikost sloupce v bajtech

*člen*<br/>
pro Členská proměnná v datové třídě, která ukládá data.

#### <a name="remarks"></a>Poznámky

Podobně jako u [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , ale také umožňuje určit datový typ sloupce i velikost.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Představuje konkrétní sloupec podporovaný zprostředkovatelem.

#### <a name="syntax"></a>Syntaxe

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parametry

*Jméno*<br/>
pro Název sloupce

*řadový*<br/>
pro Číslo sloupce Pokud sloupec není sloupcem záložky, číslo sloupce nesmí být 0.

*člen*<br/>
pro Členská proměnná v datové třídě, která ukládá data.

#### <a name="remarks"></a>Poznámky

Toto makro použijte v případě, že data sloupce jsou znak null zakončený řetězcem znaků Unicode, [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Označuje začátek mapy schématu.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parametry

*SchemaClass*<br/>
Třída, která obsahuje mapu. Obvykle to bude třída Session.

#### <a name="remarks"></a>Poznámky

Další informace o sadách řádků schématu naleznete v části [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v Windows SDK.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Označuje konec mapy schématu.

#### <a name="syntax"></a>Syntaxe

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Třída IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Přidruží identifikátor GUID ke třídě.

#### <a name="syntax"></a>Syntaxe

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parametry

*hlavních*<br/>
Identifikátor GUID sady řádků schématu. Seznam sad řádků schématu a jejich identifikátorů GUID naleznete v části [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *Referenční příručce OLE DB programátor* .

*rowsetClass*<br/>
Třída, která bude vytvořena pro reprezentaci sady řádků schématu.

#### <a name="remarks"></a>Poznámky

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) může potom zadat dotaz na mapu pro seznam identifikátorů GUID, nebo může vytvořit sadu řádků, pokud se jí přestanou GUID. Sada řádků schématu `IDBSchemaRowsetImpl` vytvořena je podobná standardní třídě odvozené `CRowsetImpl`, s výjimkou, že musí poskytovat `Execute` metodu, která má následující signaturu:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Tato funkce `Execute` naplní data sady řádků. Průvodce projektem ATL vytvoří, jak je [popsáno v sadě řádků](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *referenčních informacích pro programátory OLE DB*, tři počáteční sady řádků schématu v projektu pro každé ze tří povinných OLE DB schémat:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

Průvodce také přidá tři odpovídající položky v mapě schématu. Další informace o tom, jak pomocí průvodce vytvořit poskytovatele, najdete v tématu [vytvoření zprostředkovatele šablon OLE DB](../../data/oledb/creating-an-ole-db-provider.md) .

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referenční dokumentace k šablonám zprostředkovatelů OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Makra pro šablony zprostředkovatele OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)
