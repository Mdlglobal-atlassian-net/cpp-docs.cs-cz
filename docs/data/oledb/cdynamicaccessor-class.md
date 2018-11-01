---
title: CDynamicAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
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
- GetColumnFlags
- GetColumnInfo
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
ms.openlocfilehash: ba456f11973a33eb3b65b8de940e5be76b821f89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461473"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor – třída

Umožňuje přístup ke zdroji dat, když nemají žádné informace o schématu databáze (základní strukturu vaší databáze).

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Požadavky

**Hlavička**: také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddBindEntry –](#addbindentry)|Přidá do vazby položku výstupní sloupce při přepisování výchozí přístupový objekt.|
|[CDynamicAccessor](#cdynamicaccessor)|Vytvoří a inicializuje `CDynamicAccessor` objektu.|
|[Zavřít](#close)|Odpojuje všechny sloupce, uvolní přidělené paměti a uvolní [IAccessor](/previous-versions/windows/desktop/ms719672) ukazatel rozhraní ve třídě.|
|[Getblobhandling –](#getblobhandling)|Načte objekt BLOB zpracování hodnotu aktuálního řádku.|
|[Getblobsizelimit –](#getblobsizelimit)|Získá maximální velikost objektu BLOB v bajtech.|
|[GetBookmark](#getbookmark)|Načte záložky na aktuálním řádku.|
|[Getcolumncount –](#getcolumncount)|Získá počet sloupců v dané sadě řádků.|
|[Getcolumnflags –](#getcolumnflags)|Načte vlastnosti sloupce.|
|[GetColumnInfo –](#getcolumninfo)|Načte metadata pro sloupec.|
|[Getcolumnname –](#getcolumnname)|Načte název určený sloupec.|
|[Getcolumntype –](#getcolumntype)|Načte datový typ zadaný sloupec.|
|[GetLength](#getlength)|Získá maximální možná délka sloupce v bajtech.|
|[Getordinal –](#getordinal)|Načte index sloupce název sloupce.|
|[GetStatus](#getstatus)|Načte stav zadaného sloupce.|
|[GetValue](#getvalue)|Načte data z vyrovnávací paměti.|
|[Setblobhandling –](#setblobhandling)|Nastaví objekt BLOB zpracování hodnotu aktuálního řádku.|
|[SetBlobSizeLimit](#setblobsizelimit)|Nastaví maximální velikost objektu BLOB v bajtech.|
|[SetLength](#setlength)|Nastaví délka sloupce v bajtech.|
|[SetStatus –](#setstatus)|Nastaví stav zadaného sloupce.|
|[SetValue](#setvalue)|Ukládá data do vyrovnávací paměti.|

## <a name="remarks"></a>Poznámky

Použití `CDynamicAccessor` metody získat informace o sloupci, jako je například názvy sloupců, počet sloupců, typ dat a tak dále. Pak použijete informace o tomto sloupci k vytvoření přistupující objekt dynamicky za běhu.

Informace o sloupci je uložená ve vyrovnávací paměti, který je vytvořen a spravován společností tuto třídu. Získání dat z vyrovnávací paměti pomocí [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Příklady použití tříd dynamického přístupového objektu a diskusi najdete v tématu [použití dynamických přístupových objektů](../../data/oledb/using-dynamic-accessors.md).

## <a name="addbindentry"></a> CDynamicAccessor::AddBindEntry

Přidá položku vazby výstupní sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parametry

*Informace o*<br/>
[in] A `DBCOLUMNINFO` struktura obsahující informace o sloupci. Naleznete v části "DBCOLUMNINFO struktury" v [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *referenční informace pro OLE DB programátory*.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud přepsání výchozí přístupový objekt vytvořené pomocí `CDynamicAccessor` (viz [co a jak načíst Data?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessor"></a> CDynamicAccessor::CDynamicAccessor

Vytvoří a inicializuje `CDynamicAccessor` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Určuje, jak má být zpracována data binárního rozsáhlého objektu (BLOB). Výchozí hodnota je DBBLOBHANDLING_DEFAULT. Zobrazit [setblobhandling –](../../data/oledb/cdynamicaccessor-setblobhandling.md) popis DBBLOBHANDLINGENUM hodnoty.

*nBlobSize*<br/>
Maximální velikost objektu BLOB v bajtech; sloupec data v průběhu této hodnoty je považován za objekt BLOB. Výchozí hodnota je 8 000. Zobrazit [setblobsizelimit –](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) podrobnosti.

### <a name="remarks"></a>Poznámky

Pokud použijete konstruktor k inicializaci `CDynamicAccessor` objektu, můžete určit, jak ho vytvoří vazbu mezi objekty BLOB. Objekty BLOB může obsahovat binárních dat jako grafiky, zvuk nebo zkompilovaný kód. Výchozí chování je zpracovávat více než 8 000 bajtů sloupců jako objekty BLOB a pokuste se vytvořit vazbu, aby `ISequentialStream` objektu. Můžete však zadat jinou hodnotu, bude velikost objektu BLOB.

Můžete také určit, jak `CDynamicAccessor` zpracovává sloupec data, která se považují za data objektů BLOB: dokáže zpracovat data objektů BLOB ve výchozím nastavení, můžete přeskočit (nemá vazbu) data objektů BLOB, nebo ho můžete svázat data objektů BLOB v paměti přidělené zprostředkovatele.

## <a name="close"></a> CDynamicAccessor::Close

Odpojuje všechny sloupce, uvolní přidělené paměti a uvolní [IAccessor](/previous-versions/windows/desktop/ms719672) ukazatel rozhraní ve třídě.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="getblobhandling"></a> CDynamicAccessor::GetBlobHandling

Načte objekt BLOB zpracování hodnotu aktuálního řádku.

### <a name="syntax"></a>Syntaxe

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Poznámky

Vrátí objekt BLOB zpracování hodnotu *eBlobHandling* jako nastavte podle [setblobhandling –](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="getblobsizelimit"></a> CDynamicAccessor::GetBlobSizeLimit

Získá maximální velikost objektu BLOB v bajtech.

### <a name="syntax"></a>Syntaxe

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Poznámky

Vrátí objekt BLOB zpracování hodnotu *nBlobSize* jako nastavte podle [setblobsizelimit –](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="getbookmark"></a> CDynamicAccessor::GetBookmark

Načte záložky na aktuálním řádku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parametry

*pBookmark*<br/>
[out] Ukazatel [CBookmark](../../data/oledb/cbookmark-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Je nutné nastavit `DBPROP_IRowsetLocate` k VARIANT_TRUE načíst záložky.

## <a name="getcolumncount"></a> CDynamicAccessor::GetColumnCount

Získá počet sloupců.

### <a name="syntax"></a>Syntaxe

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Načíst počet sloupců.

## <a name="getcolumnflags"></a> CDynamicAccessor::GetColumnFlags

Načte vlastnosti sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnFlags(DBORDINAL nColumn, 
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*pFlags*<br/>
[out] Ukazatel na bitová maska, která popisuje vlastnosti sloupce. Naleznete v části "DBCOLUMNFLAGS Výčtový typ" v [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *referenční informace pro OLE DB programátory*.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud vlastnosti sloupce se úspěšně obnovila. V opačném případě vrátí **false**.

### <a name="remarks"></a>Poznámky

Číslo sloupce je posun z jednoho. Sloupec nula je zvláštní případ. Pokud je k dispozici je na záložku.

## <a name="getcolumninfo"></a> CDynamicAccessor::GetColumnInfo

Vrátí metadata sloupce vyžadované většina uživatelů.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetColumnInfo(IRowset* pRowset, 
   DBORDINAL* pColumns, 
   DBCOLUMNINFO** ppColumnInfo, 
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*pRowset*<br/>
[in] Ukazatel [IRowset](/previous-versions/windows/desktop/ms720986) rozhraní.

*pColumns*<br/>
[out] Ukazatel na paměť ke vrácení počet sloupců v dané sadě řádků; Toto číslo zahrnuje sloupec záložky, pokud existuje.

*ppColumnInfo*<br/>
[out] Ukazatel na paměť ke vrácení pole `DBCOLUMNINFO` struktury. Naleznete v části "DBCOLUMNINFO struktury" v [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *referenční informace pro OLE DB programátory*.

*ppStringsBuffer*<br/>
[out] Ukazatel na paměť ke vrácení ukazatele do služby storage pro všechny hodnoty řetězce (použít názvy v rámci *columnid* nebo *pwszName*) v rámci jedna alokace bloku.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Zobrazit [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *OLE DB referenční informace pro programátory* informace o typech dat `DBORDINAL`, `DBCOLUMNINFO`, a `OLECHAR`.

## <a name="getcolumnname"></a> CDynamicAccessor::GetColumnName

Načte název pro určený sloupec.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

### <a name="return-value"></a>Návratová hodnota

Název zadaný sloupec.

## <a name="getcolumntype"></a> CDynamicAccessor::GetColumnType

Načte datový typ zadaný sloupec.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetColumnType(DBORDINAL nColumn, 
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*pType*<br/>
[out] Ukazatel na datový typ pro určený sloupec.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** v případě úspěchu nebo **false** při selhání.

## <a name="getlength"></a> CDynamicAccessor::GetLength

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
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

*pLength*<br/>
[out] Ukazatel na celé číslo obsahující délku sloupce v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud je nalezen zadaný sloupec. V opačném případě tato funkce vrací **false**.

### <a name="remarks"></a>Poznámky

První přepsání přebírá číslo sloupce a druhý a třetí přepsání trvat název sloupce ve formátu ANSI nebo Unicode, v uvedeném pořadí.

## <a name="getordinal"></a> CDynamicAccessor::GetOrdinal

Získá číslo sloupce, název sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Parametry

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

*pOrdinal*<br/>
[out] Ukazatel na číslo sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud je nalezen sloupec se zadaným názvem. V opačném případě tato funkce vrací **false**.

## <a name="getstatus"></a> CDynamicAccessor::GetStatus

Načte stav pro určený sloupec.

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
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

*pStatus*<br/>
[out] Ukazatel na proměnnou obsahující sloupec Stav. Zobrazit [DBSTATUS](/previous-versions/windows/desktop/ms722617) v *OLE DB referenční informace pro programátory* Další informace.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud je nalezen zadaný sloupec. V opačném případě tato funkce vrací **false**.

## <a name="getvalue"></a> CDynamicAccessor::GetValue

Načte data pro určený sloupec.

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

*ctype*<br/>
[in] Parametr bez vizuálního vzhledu, která zpracovává žádný datový typ s výjimkou typy řetězců (`CHAR*`, `WCHAR*`), které vyžadují speciální zacházení. `GetValue` používá odpovídající typ dat podle je určit tady.

*nColumn*<br/>
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*pColumnName*<br/>
[in] Název sloupce.

*pData*<br/>
[out] Ukazatel na obsah pro určený sloupec.

### <a name="return-value"></a>Návratová hodnota

Pokud chcete předat data řetězce, pomocí nešablonové verzích `GetValue`. Verze nešablonové této metody vrátit `void*`, který odkazuje na součást, která obsahuje zadaný sloupec dat vyrovnávací paměti. Vrátí hodnotu NULL, pokud sloupec nebyl nalezen.

Pro všechny ostatní typy dat, je jednodušší použít bez vizuálního vzhledu verzích `GetValue`. Vrátí bez vizuálního vzhledu verze **true** v případě úspěchu nebo **false** při selhání.

### <a name="remarks"></a>Poznámky

Pomocí nešablonové verze vrátit sloupce, které obsahují řetězce a bez vizuálního vzhledu verze pro sloupce, které obsahují jiné datové typy.

V režimu ladění, se zobrazí kontrolní výraz, když velikost *pData* nerovnost velikost sloupce, na kterou odkazuje.

## <a name="setblobhandling"></a> CDynamicAccessor::SetBlobHandling

Nastaví objekt BLOB zpracování hodnotu aktuálního řádku.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Určuje, jak má být zpracována datový objekt BLOB. To můžete provést následující hodnoty:

- DBBLOBHANDLING_DEFAULT: Zpracování sloupec dat větší než *nBlobSize* (jako nastavení podle `SetBlobSizeLimit`) stejně jako data v objektech BLOB a jejich prostřednictvím načtení `ISequentialStream` nebo `IStream` objektu. Tento příkaz se pokusí vytvořit vazbu každý sloupec, který obsahuje data, které jsou větší než *nBlobSize* nebo uveden jako DBTYPE_IUNKNOWN jako data objektů BLOB.

- DBBLOBHANDLING_NOSTREAMS: Zpracování sloupec dat větší než *nBlobSize* (například nastavit podle `SetBlobSizeLimit`) stejně jako data v objektech BLOB a získat prostřednictvím odkazů v paměti přidělené poskytovatele, vlastnictví příjemce. Tato možnost je užitečná pro tabulky, které mají více než jeden sloupec objektů BLOB a zprostředkovatel podporuje pouze jeden `ISequentialStream` objekt za přistupujícího objektu.

- DBBLOBHANDLING_SKIP: Přeskočit (vazba není) sloupce kvalifikaci jako obsahující objekty BLOB (přistupujícím objektu nebude vazby nebo načíst hodnotu sloupce, ale stále se načtou sloupce stavu a délky).

### <a name="remarks"></a>Poznámky

Měli byste zavolat `SetBlobHandling` před voláním `Open`.

Metoda konstruktoru [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) nastaví hodnota, která má DBBLOBHANDLING_DEFAULT zpracování objektu BLOB.

## <a name="setblobsizelimit"></a> CDynamicAccessor::SetBlobSizeLimit

Nastaví maximální velikost objektu BLOB v bajtech.

### <a name="syntax"></a>Syntaxe

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parametry

*nBlobSize*<br/>
Určuje maximální velikost objektu BLOB.

### <a name="remarks"></a>Poznámky

Nastaví maximální velikost objektu BLOB v bajtech; sloupec dat větší než tato hodnota je považován za objekt BLOB. Někteří poskytovatelé poskytují velmi velké velikosti sloupců (jako je například 2 GB). Namísto pokusu o přidělení paměti pro sloupec tato velikost by obvykle pokusíte navázat tyto sloupce jako objekty BLOB. Tímto způsobem není nutné přidělit veškerou paměť, ale i nadále můžete načítat všechna data bez obav zkrácení. Existují však případy, ve kterých může být vhodné vynutit `CDynamicAccessor` navázat velké sloupce v jejich nativním datové typy. Chcete-li to provést, zavolejte `SetBlobSizeLimit` před voláním `Open`.

Metoda konstruktoru [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Nastaví maximální velikost objektu BLOB na výchozí hodnotu 8 000 bajtů.

## <a name="setlength"></a> CDynamicAccessor::SetLength

Nastaví délku pro určený sloupec.

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
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*nLength*<br/>
[in] Délka sloupce v bajtech.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud délka zadaný sloupec je nastaven úspěšně. V opačném případě tato funkce vrací **false**.

## <a name="setstatus"></a> CDynamicAccessor::SetStatus

Nastaví stav pro určený sloupec.

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
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*Stav*<br/>
[in] Stav sloupce. Zobrazit [DBSTATUS](/previous-versions/windows/desktop/ms722617) v *OLE DB referenční informace pro programátory* Další informace.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud je zadaný sloupec stav nastaven úspěšně. V opačném případě tato funkce vrací **false**.

## <a name="setvalue"></a> CDynamicAccessor::SetValue

Ukládá data pro určený sloupec.

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

*ctype*<br/>
[in] Parametr bez vizuálního vzhledu, která zpracovává žádný datový typ s výjimkou typy řetězců (`CHAR*`, `WCHAR*`), které vyžadují speciální zacházení. `GetValue` používá odpovídající typ dat podle je určit tady.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

*data*<br/>
[in] Ukazatel na paměť obsahující data.

*nColumn*<br/>
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

### <a name="return-value"></a>Návratová hodnota

Pokud chcete nastavit data řetězce, pomocí nešablonové verzích `GetValue`. Verze nešablonové této metody vrátit `void*`, který odkazuje na součást, která obsahuje zadaný sloupec dat vyrovnávací paměti. Vrátí hodnotu NULL, pokud sloupec nebyl nalezen.

Pro všechny ostatní typy dat, je jednodušší použít bez vizuálního vzhledu verzích `GetValue`. Vrátí bez vizuálního vzhledu verze **true** v případě úspěchu nebo **false** při selhání.

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)