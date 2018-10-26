---
title: Cmfcfilterchunkvalueimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
dev_langs:
- C++
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3de666443d3ce675d1a95553608d3a9fdc1b82e9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068135"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Cmfcfilterchunkvalueimpl – třída

Toto je třída, která zjednodušuje logiku párování hodnot bloku dat a vlastnosti.

## <a name="syntax"></a>Syntaxe

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Cmfcfilterchunkvalueimpl –:: ~ cmfcfilterchunkvalueimpl –](#_dtorcmfcfilterchunkvalueimpl)|Destructs objektu.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|Vymaže ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Tento blok dat zkopíruje do struktury popisující vlastnosti blok.|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicializuje tuto hodnotu bloků dat z jiné hodnoty.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Načte bloků dat identifikátoru GUID.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Načte bloků PID (ID vlastnosti).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Získá bloku dat typu.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Načte hodnotu řetězce.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Načte hodnotu jako přidělené sestavování propvariant.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Hodnota vrátí nepřidělený (vnitřní hodnotu).|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Kontroluje, zda hodnota této vlastnosti je platný, nebo ne.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Přetíženo. Nastaví vlastnost klíčem na logickou hodnotu.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Nastaví vlastnost klíčem k typu DWORD.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Klíčem k FileTime – nastaví vlastnost.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Nastaví vlastnost klíčem pro typ int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Nastaví vlastnost klíčem na celé číslo|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Nastaví vlastnost klíčem k typu LONG.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Klíčem k SYSTEMTIME – nastaví vlastnost.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Nastaví vlastnost klíčem na řetězec znaků Unicode.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Pomocná funkce, která nastavuje společné vlastnosti u bloku.|

## <a name="remarks"></a>Poznámky

Pokud chcete použít, jednoduše vytvořte cmfcfilterchunkvalueimpl – třída typu vpravo

Příklad:

Cmfcfilterchunkvalueimpl – bloku;

hr = bloku. SetBoolValue(PKEY_IsAttachment, true);

or

hr = bloku. SetFileTimeValue (PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ATL::IFilterChunkValue`

[Cmfcfilterchunkvalueimpl –](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear

Vymaže ChunkValue.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Vytvoří objekt.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Poznámky

##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  Cmfcfilterchunkvalueimpl –:: ~ cmfcfilterchunkvalueimpl –

Destructs objektu.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Poznámky

##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk

Tento blok dat zkopíruje do struktury popisující vlastnosti blok.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Parametry

*pStatChunk*<br/>
Ukazatel na cílové hodnoty popisující vlastnosti bloků.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom

Inicializuje tuto hodnotu bloků dat z jiné hodnoty.

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Určuje hodnotu zdroje ke zkopírování z.

### <a name="remarks"></a>Poznámky

##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID

Načte bloků dat identifikátoru GUID.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na identifikátor GUID identifikující bloků.

### <a name="remarks"></a>Poznámky

##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID

Načte bloků PID (ID vlastnosti).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující ID vlastnosti.

### <a name="remarks"></a>Poznámky

##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType

Získá typ bloku.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota CHUNKSTATE výčtu, která určuje, zda aktuální blok dat je vlastnost text – typ nebo typ hodnoty vlastnosti.

### <a name="remarks"></a>Poznámky

##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString

Načte hodnotu řetězce.

```
CString &GetString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující hodnotu bloku.

### <a name="remarks"></a>Poznámky

##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue

Načte hodnotu jako přidělené sestavování propvariant.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Parametry

*ppPropVariant*<br/>
Po návratu funkce tento parametr obsahuje hodnotu bloku.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud byla úspěšně přidělena sestavování PROPVARIANT a hodnota bloků dat byl úspěšně zkopírován do *ppPropVariant*; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc

Vrátí hodnotu-přidělené (interní hodnota).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální hodnotu bloku.

### <a name="remarks"></a>Poznámky

##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid

Kontroluje, zda hodnota této vlastnosti je platný, nebo ne.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je aktuální blok dat hodnota platná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue

Přetíženo. Nastaví vlastnost klíčem na logickou hodnotu.

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*bVal*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk

Pomocná funkce, která nastavuje společné vlastnosti u bloku.

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue

Nastavte vlastnost klíčem k typu DWORD.

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*dwVal*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue

Nastavte vlastnost klíč hodnota filetime.

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*dtVal*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value

Nastavte vlastnost klíčem pro typ int64.

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*nVal*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue

Nastavte vlastnost klíčem na celé číslo

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*nVal*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue

Nastavte vlastnost klíčem k typu LONG.

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*lVal*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue

Klíčem k SYSTEMTIME – nastaví vlastnost.

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*SYSTEMTIME –*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue

Nastaví vlastnost klíčem na řetězec znaků Unicode.

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parametry

*pkey*<br/>
Určuje klíč vlastnosti.

*pszValue*<br/>
Určuje hodnotu bloků dat pro nastavení.

*chunkType*<br/>
Příznaky označoval, zda tento blok obsahuje text – typ nebo typ hodnoty vlastnosti. Příznak hodnoty pocházejí z CHUNKSTATE výčtu.

*Národní prostředí*<br/>
Jazyk a dílčího přidružený blok textu. Národní prostředí bloků dat používá indexery dokumentu provést řádné dělení slov textu. Jestliže u bloku není typu text ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole se ignoruje.

*cwcLenSource*<br/>
Délka ve znacích zdrojový text, ze kterého aktuální blok dat odvozený. Nulová hodnota označuje, že propojeni znak po znaku zdrojového textu a odvozené text. Nenulová hodnota znamená, že neexistuje žádné přímé komunikaci.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozené blok začíná v bloku dat zdroje.

*chunkBreakType*<br/>
Typu break, který odděluje od aktuální blok dat u předchozího bloku. Hodnoty jsou od CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
