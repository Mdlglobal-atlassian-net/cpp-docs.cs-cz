---
title: CDynamicAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: a2dcb946b4161c03fe34f02608cfb3dbbca21695
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075822"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor – třída

Umožňuje přístup ke zdroji dat, když nemáte žádné znalosti o schématu databáze (podkladové struktuře databáze).

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Požadavky

**Záhlaví**: atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddBindEntry](#addbindentry)|Přidá položku vazby do výstupních sloupců při přepisu výchozího přístupového objektu.|
|[CDynamicAccessor](#cdynamicaccessor)|Vytvoří instanci a inicializuje objekt `CDynamicAccessor`.|
|[Uzavírací](#close)|Odpojí všechny sloupce, uvolní přidělenou paměť a uvolní ukazatel rozhraní [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) ve třídě.|
|[GetBlobHandling](#getblobhandling)|Načte hodnotu zpracování objektu BLOB pro aktuální řádek.|
|[GetBlobSizeLimit](#getblobsizelimit)|Načte maximální velikost objektu BLOB v bajtech.|
|[GetBookmark](#getbookmark)|Načte záložku pro aktuální řádek.|
|[Getpočet sloupců](#getcolumncount)|Načte počet sloupců v sadě řádků.|
|[GetColumnFlags](#getcolumnflags)|Načte vlastnosti sloupce.|
|[GetColumnInfo –](#getcolumninfo)|Načte metadata sloupce.|
|[GetColumn](#getcolumnname)|Načte název zadaného sloupce.|
|[GetColumnType](#getcolumntype)|Načte datový typ zadaného sloupce.|
|[GetLength –](#getlength)|Načte maximální možnou délku sloupce v bajtech.|
|[GetOrdinal](#getordinal)|Načte index sloupce s ohledem na název sloupce.|
|[GetStatus](#getstatus)|Načte stav zadaného sloupce.|
|[GetValue](#getvalue)|Načte data z vyrovnávací paměti.|
|[SetBlobHandling](#setblobhandling)|Nastaví hodnotu manipulace objektu BLOB pro aktuální řádek.|
|[SetBlobSizeLimit](#setblobsizelimit)|Nastaví maximální velikost objektu BLOB v bajtech.|
|[SetLength](#setlength)|Nastaví délku sloupce v bajtech.|
|[Jiná](#setstatus)|Nastaví stav zadaného sloupce.|
|[SetValue](#setvalue)|Ukládá data do vyrovnávací paměti.|

## <a name="remarks"></a>Poznámky

Použijte metody `CDynamicAccessor` k získání informací o sloupci, jako jsou názvy sloupců, počet sloupců, datový typ a tak dále. Tyto informace o sloupci pak můžete použít k dynamickému vytvoření přístupového objektu za běhu.

Informace o sloupci jsou uloženy ve vyrovnávací paměti, která je vytvořena a spravována touto třídou. Získat data z vyrovnávací paměti pomocí [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Diskuzi a příklady použití tříd dynamického přistupujícího objektu naleznete v tématu [použití dynamických přístupových objektů](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a>CDynamicAccessor:: AddBindEntry

Přidá položku vazby do výstupních sloupců.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parametry

*příjemce*<br/>
pro Struktura `DBCOLUMNINFO` obsahující informace o sloupci Viz "DBCOLUMNINFO struktury" v [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte při přepisu výchozího přístupového objektu vytvořeného pomocí `CDynamicAccessor` (viz [Jak můžu načíst data?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a>CDynamicAccessor:: CDynamicAccessor

Vytvoří instanci a inicializuje objekt `CDynamicAccessor`.

### <a name="syntax"></a>Syntaxe

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Určuje, jak mají být zpracovávána data binárního rozsáhlého objektu (BLOB). Výchozí hodnota je DBBLOBHANDLING_DEFAULT. Popis hodnot DBBLOBHANDLINGENUM naleznete v tématu [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) .

*nBlobSize*<br/>
Maximální velikost objektu BLOB v bajtech; data sloupce nad tuto hodnotu se považují za objekt BLOB. Výchozí hodnota je 8 000. Podrobnosti najdete v tématu [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) .

### <a name="remarks"></a>Poznámky

Použijete-li konstruktor k inicializaci objektu `CDynamicAccessor`, můžete určit, jak bude navazovat objekty blob. Objekty blob můžou obsahovat binární data, jako jsou grafika, zvuk nebo zkompilovaný kód. Výchozím chováním je považovat sloupce více než 8 000 bajtů jako objekty BLOB a pokusit se je navážet na objekt `ISequentialStream`. Můžete ale zadat jinou hodnotu jako velikost objektu BLOB.

Můžete také určit, jakým způsobem `CDynamicAccessor` zpracovává data sloupců, která se mají vycházet jako data objektů BLOB: může zpracovávat data objektů BLOB ve výchozím způsobu; může přeskočit (nevytvářet vazby) data objektů BLOB; nebo může navazovat data objektů BLOB v paměti přidělené poskytovatelem.

## <a name="cdynamicaccessorclose"></a><a name="close"></a>CDynamicAccessor:: Close

Odpojí všechny sloupce, uvolní přidělenou paměť a uvolní ukazatel rozhraní [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) ve třídě.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a>CDynamicAccessor:: GetBlobHandling

Načte hodnotu zpracování objektu BLOB pro aktuální řádek.

### <a name="syntax"></a>Syntaxe

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu zpracování objektu BLOB *eBlobHandling* jako nastavenou hodnotou [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a>CDynamicAccessor:: GetBlobSizeLimit

Načte maximální velikost objektu BLOB v bajtech.

### <a name="syntax"></a>Syntaxe

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu zpracování objektu BLOB *nBlobSize* jako nastavenou hodnotou [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a>CDynamicAccessor:: GetBookmark

Načte záložku pro aktuální řádek.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parametry

*pBookmark*<br/>
mimo Ukazatel na objekt [CBookmark](../../data/oledb/cbookmark-class.md) .

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Je nutné nastavit `DBPROP_IRowsetLocate` pro VARIANT_TRUE k načtení záložky.

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a>CDynamicAccessor:: getsloupců

Načte počet sloupců.

### <a name="syntax"></a>Syntaxe

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet načtených sloupců

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a>CDynamicAccessor:: GetColumnFlags

Načte vlastnosti sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pFlags*<br/>
mimo Ukazatel na bitovou masku, která popisuje vlastnosti sloupce. Viz "DBCOLUMNFLAGS Výčtový typ" v [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud jsou charakteristiky sloupce úspěšně načteny. V opačném případě vrátí **hodnotu false**.

### <a name="remarks"></a>Poznámky

Číslo sloupce je posunuto od jednoho. Nula sloupce je zvláštní případ; je to záložka, pokud je dostupná.

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a>CDynamicAccessor:: GetColumnInfo

Vrátí metadata sloupce potřebná pro většinu uživatelů.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*pRowset*<br/>
pro Ukazatel na rozhraní [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) .

*pColumns*<br/>
mimo Ukazatel na paměť, ve které má být vrácen počet sloupců v sadě řádků; Toto číslo zahrnuje sloupec Bookmark, pokud je nějaký.

*ppColumnInfo*<br/>
mimo Ukazatel na paměť, ve kterém se má vrátit pole `DBCOLUMNINFO` struktury. Viz "DBCOLUMNINFO struktury" v [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenci programátora OLE DB*.

*ppStringsBuffer*<br/>
mimo Ukazatel na paměť, ve kterém se má vrátit ukazatel na úložiště pro všechny řetězcové hodnoty (názvy používané v rámci *ColumnID* nebo pro *pwszName*) v rámci jednoho bloku přidělení.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Informace o datových typech `DBORDINAL`, `DBCOLUMNINFO`a `OLECHAR`naleznete v tématu [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenčních informacích programátora OLE DB* .

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a>CDynamicAccessor:: getsloupcový

Načte název zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

### <a name="return-value"></a>Návratová hodnota

Název zadaného sloupce

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a>CDynamicAccessor:: GetColumnType

Načte datový typ zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pType*<br/>
mimo Ukazatel na datový typ zadaného sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a>CDynamicAccessor:: GetLength

Načte délku zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pColumnName*<br/>
pro Ukazatel na řetězec znaků obsahující název sloupce.

*pLength*<br/>
mimo Ukazatel na celé číslo, které obsahuje délku sloupce v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu pravda** , pokud je nalezen zadaný sloupec. V opačném případě vrátí tato funkce **hodnotu false**.

### <a name="remarks"></a>Poznámky

První přepsání přebírá číslo sloupce a druhá a třetí přepsání přebírají název sloupce ve formátu ANSI nebo Unicode, v uvedeném pořadí.

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a>CDynamicAccessor:: GetOrdinal

Načte číslo sloupce pro daný název sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Parametry

*pColumnName*<br/>
pro Ukazatel na řetězec znaků obsahující název sloupce.

*pOrdinal*<br/>
mimo Ukazatel na číslo sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu pravda** , pokud je nalezen sloupec se zadaným názvem. V opačném případě vrátí tato funkce **hodnotu false**.

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a>CDynamicAccessor:: GetStatus

Načte stav zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pColumnName*<br/>
pro Ukazatel na řetězec znaků obsahující název sloupce.

*pStatus*<br/>
mimo Ukazatel na proměnnou, která obsahuje stav sloupce. Další informace najdete v tématu [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *Referenční příručce programátora OLE DB* .

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu pravda** , pokud je nalezen zadaný sloupec. V opačném případě vrátí tato funkce **hodnotu false**.

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a>CDynamicAccessor:: GetValue

Načte data pro zadaný sloupec.

### <a name="syntax"></a>Syntaxe

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>Parametry

*CType*<br/>
pro Parametr s šablonou, který zpracovává libovolný datový typ kromě řetězcových typů (`CHAR*`, `WCHAR*`), které vyžadují speciální zpracování. `GetValue` používá vhodný datový typ podle toho, co tady zadáte.

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pColumnName*<br/>
pro Název sloupce

*pData*<br/>
mimo Ukazatel na obsah zadaného sloupce.

### <a name="return-value"></a>Návratová hodnota

Pokud chcete předat řetězcová data, použijte nešablonované verze `GetValue`. Verze této metody bez šablon vrací `void*`, která odkazuje na část vyrovnávací paměti, která obsahuje zadaná data sloupce. Vrátí hodnotu NULL, pokud sloupec nebyl nalezen.

Pro všechny ostatní datové typy je jednodušší používat šablony verze `GetValue`. Verze šablon vrací **hodnotu true** při úspěchu nebo **NEPRAVDA** při selhání.

### <a name="remarks"></a>Poznámky

Použijte nešablonované verze k vrácení sloupců, které obsahují řetězce a verze šablon pro sloupce, které obsahují jiné datové typy.

V režimu ladění obdržíte kontrolní výraz, pokud je velikost *PDATA* rovna velikosti sloupce, na který odkazuje.

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a>CDynamicAccessor:: SetBlobHandling

Nastaví hodnotu manipulace objektu BLOB pro aktuální řádek.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Určuje způsob zpracování dat objektu BLOB. Může mít následující hodnoty:

- DBBLOBHANDLING_DEFAULT: zpracování dat sloupce větší než *nBlobSize* (jako nastavení `SetBlobSizeLimit`) jako dat objektů BLOB a jejich načtení prostřednictvím objektu `ISequentialStream` nebo `IStream`. Tato možnost se pokusí vytvořit vazby na všechny sloupce obsahující data větší než *nBlobSize* nebo uvedená jako DBTYPE_IUNKNOWN jako data objektů BLOB.

- DBBLOBHANDLING_NOSTREAMS: zpracování dat sloupce větší než *nBlobSize* (jako nastavení `SetBlobSizeLimit`) jako dat objektů BLOB a jejich načtení prostřednictvím odkazu v paměti, která je přidělena poskytovateli a uživatelem vlastněných uživatelů. Tato možnost je užitečná pro tabulky, které mají více než jeden sloupec objektů BLOB, a poskytovatel podporuje pouze jeden objekt `ISequentialStream` pro přístup.

- DBBLOBHANDLING_SKIP: přeskočit (nevytvářet vazby) sloupce opravňující jako obsahující objekty BLOB (přistupující objekt nebude navazovat nebo načíst hodnotu sloupce, ale bude i nadále získávat stav a délku sloupce).

### <a name="remarks"></a>Poznámky

Před voláním `Open`byste měli volat `SetBlobHandling`.

Metoda konstruktoru [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) nastaví hodnotu manipulace objektu BLOB na DBBLOBHANDLING_DEFAULT.

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a>CDynamicAccessor:: SetBlobSizeLimit

Nastaví maximální velikost objektu BLOB v bajtech.

### <a name="syntax"></a>Syntaxe

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parametry

*nBlobSize*<br/>
Určuje limit velikosti objektu BLOB.

### <a name="remarks"></a>Poznámky

Nastaví maximální velikost objektu BLOB v bajtech. data sloupce větší, než je tato hodnota, se považují za objekt BLOB. Někteří poskytovatelé poskytují pro sloupce extrémně velké velikosti (například 2 GB). Místo toho, abyste se pokoušeli přidělit paměť pro sloupec této velikosti, obvykle se pokusíte tyto sloupce vytvořit jako objekty blob. Tímto způsobem nemusíte přidělit veškerou paměť, ale přesto můžete všechna data číst, aniž byste se museli obávat zkrátit. Existují však případy, kdy je možné vynutit `CDynamicAccessor` vázání velkých sloupců v jejich nativních datových typech. Chcete-li to provést, zavolejte `SetBlobSizeLimit` před voláním `Open`.

Metoda konstruktoru [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) nastaví maximální velikost objektu BLOB na výchozí hodnotu 8 000 bajtů.

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a>CDynamicAccessor:: SetLength

Nastaví délku zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*nLength*<br/>
pro Délka sloupce v bajtech

*pColumnName*<br/>
pro Ukazatel na řetězec znaků obsahující název sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud je zadaná délka sloupce úspěšně nastavena. V opačném případě vrátí tato funkce **hodnotu false**.

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a>CDynamicAccessor:: SetStatus

Nastaví stav zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*stav*<br/>
pro Stav sloupce Další informace najdete v tématu [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *Referenční příručce programátora OLE DB* .

*pColumnName*<br/>
pro Ukazatel na řetězec znaků obsahující název sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud je stav zadaného sloupce úspěšně nastaven. V opačném případě vrátí tato funkce **hodnotu false**.

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a>CDynamicAccessor:: SetValue

Ukládá data do zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype>
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>Parametry

*CType*<br/>
pro Parametr s šablonou, který zpracovává libovolný datový typ kromě řetězcových typů (`CHAR*`, `WCHAR*`), které vyžadují speciální zpracování. `GetValue` používá vhodný datový typ podle toho, co tady zadáte.

*pColumnName*<br/>
pro Ukazatel na řetězec znaků obsahující název sloupce.

*údajů*<br/>
pro Ukazatel na paměť obsahující data.

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

### <a name="return-value"></a>Návratová hodnota

Pokud chcete nastavit řetězcová data, použijte nešablonované verze `GetValue`. Verze této metody bez šablon vrací `void*`, která odkazuje na část vyrovnávací paměti, která obsahuje zadaná data sloupce. Vrátí hodnotu NULL, pokud sloupec nebyl nalezen.

Pro všechny ostatní datové typy je jednodušší používat šablony verze `GetValue`. Verze šablon vrací **hodnotu true** při úspěchu nebo **NEPRAVDA** při selhání.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)