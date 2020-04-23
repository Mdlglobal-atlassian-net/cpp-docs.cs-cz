---
title: CMFCFilterChunkValueImpl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: c89d41f7db43d9504bfc22cbf35a59fcceb511e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752359"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl – třída

Toto je třída, která zjednodušuje logiku dvojice hodnot bloku a vlastností.

## <a name="syntax"></a>Syntaxe

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Zničí objekt.|
|[CMFCFilterChunkValueImpl:::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Vymazat](#clear)|Vymaže ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Zkopíruje tento blok do struktury popisující vlastnosti bloku.|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicializuje tuto hodnotu bloku dat z jiné hodnoty.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Načte identifikátor GUID bloku.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Načte blok PID (ID vlastnosti).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Získá typ bloku.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Načte hodnotu řetězce.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Načte hodnotu jako přidělenou propvariantu.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Vrátí nepřidělenou (interní hodnotu).|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Zkontroluje, zda je tato hodnota vlastnosti platná či nikoli.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Přetíženo. Nastaví vlastnost podle klíče na logickou hodnotu.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Nastaví vlastnost podle klíče dword.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Nastaví vlastnost podle klíče na soubor.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Nastaví vlastnost podle klíče na int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Nastaví vlastnost podle klíče na int.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Nastaví vlastnost klíčem long.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Nastaví vlastnost podle klíče na SystemTime.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Nastaví vlastnost podle klíče na řetězec Unicode.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Pomocná funkce, která nastavuje společné vlastnosti bloku.|

## <a name="remarks"></a>Poznámky

Chcete-li použít, jednoduše vytvořit CMFCFilterChunkValueImpl třídy správného druhu

Příklad:

CMFCFilterChunkValueImpl blok;

hod = kus. SetBoolValue(PKEY_IsAttachment, true);

– nebo –

hod = kus. SetFileTimeValue (PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Vymazat

Vymaže ChunkValue.

```cpp
void Clear();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl:::CMFCFilterChunkValueImpl

Vytvoří objekt.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl

Zničí objekt.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk

Zkopíruje tento blok do struktury popisující vlastnosti bloku.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Parametry

*pStatChunk*<br/>
Ukazatel na cílovou hodnotu popisující charakteristiky bloku dat.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyFrom

Inicializuje tuto hodnotu bloku dat z jiné hodnoty.

```cpp
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pHodnota*<br/>
Určuje zdrojovou hodnotu, ze které se má kopírovat.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID

Načte identifikátor GUID bloku.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na identifikátor GUID identifikující blok dat.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID

Načte blok PID (ID vlastnosti).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující ID vlastnosti.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType

Načte typ bloku.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Návratová hodnota

A CHUNKSTATE výčtu hodnota, která určuje, zda aktuální blok je vlastnost typu textu nebo vlastnost typu value.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString

Načte hodnotu řetězce.

```
CString &GetString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující hodnotu bloku dat.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue

Načte hodnotu jako přidělenou propvariantu.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Parametry

*ppPropVariant*<br/>
Když funkce vrátí, tento parametr obsahuje hodnotu bloku.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud byla úspěšně přidělena hodnota PROPVARIANT a hodnota bloku dat byla úspěšně zkopírována do *ppPropVariant*; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc

Vrátí nepřidělenou (interní hodnotu).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální hodnotu bloku dat.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid

Zkontroluje, zda je tato hodnota vlastnosti platná či nikoli.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je aktuální hodnota bloku dat platná; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue

Přetíženo. Nastaví vlastnost podle klíče na logickou hodnotu.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*bVal*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk

Pomocná funkce, která nastavuje společné vlastnosti bloku.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue

Nastavte vlastnost podle klíče na DWORD.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*dwVal řekl:*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue

Nastavte vlastnost podle klíče na soubor.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*dtVal*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value

Nastavte vlastnost podle klíče na int64.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*nVal*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue

Nastavte vlastnost podle klíče na int.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*nVal*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue

Nastavte vlastnost podle klíče na LONG.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*lVal*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue

Nastaví vlastnost podle klíče na SystemTime.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*systemTime*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue

Nastaví vlastnost podle klíče na řetězec Unicode.

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

*pklíč*<br/>
Určuje klíč vlastnosti.

*pszValue*<br/>
Určuje hodnotu bloku, kterou chcete nastavit.

*chunkType*<br/>
Příznaky označují, zda tento blok obsahuje text typu nebo vlastnost typu value. Hodnoty příznaku jsou převzaty z výčtu CHUNKSTATE.

*Národní prostředí*<br/>
Jazyk a podjazyk přidružený k bloku textu. Národní prostředí bloku dat používá indexery dokumentů k provedení správné horečné rozdělení textu. Pokud blok dat není textový ani typ hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, bude toto pole ignorováno.

*cwcLenSource*<br/>
Délka zdrojového textu, ze kterého byl odvozen aktuální blok dat, ve znacích. Nulová hodnota označuje korespondenci po znaku mezi zdrojovým textem a odvozeným textem. Nenulová hodnota znamená, že taková přímá korespondence neexistuje.

*cwcStartSource*<br/>
Posun, ze kterého zdrojový text pro odvozený blok začíná ve zdrojovém bloku.

*chunkBreakType*<br/>
Typ přerušení, který odděluje předchozí blok od aktuálního bloku. Hodnoty jsou z CHUNK_BREAKTYPE výčtu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
