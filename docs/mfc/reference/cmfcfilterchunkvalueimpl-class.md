---
title: Třída CMFCFilterChunkValueImpl | Microsoft Docs
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
ms.openlocfilehash: 9d274cbafbd50df2f577b484e433c964f1dec096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl – třída
Toto je třída, která zjednodušuje bloku i pro vlastnost hodnota pár logiku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destructs objektu.|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Vytvoří objekt.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](#clear)|Vymaže ChunkValue.|  
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Zkopíruje tento blok pro strukturu popisující charakteristiky bloku.|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicializuje tuto hodnotu bloků dat z jiné hodnoty.|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Načte bloku identifikátor GUID.|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Načte bloku PID (ID vlastnosti).|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Získá bloku dat typu.|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Načte hodnotu řetězce.|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Načte hodnotu jako přidělené propvariant.|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Hodnota, vrátí nepřiděleného (interní hodnota).|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Kontroluje, zda hodnota této vlastnosti je platný, nebo ne.|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Přetíženo. Nastaví vlastnost pomocí klíče na booleovskou hodnotu.|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Nastaví vlastnost pomocí klíče k typu DWORD.|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Nastaví vlastnost pomocí klíče k filetime.|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Nastaví vlastnost pomocí klíče na datovém typu int64.|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Nastaví vlastnost pomocí klíče na typ int.|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Nastaví vlastnost pomocí klíče na DLOUHÝ.|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Nastaví vlastnost pomocí klíče k SystemTime.|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Nastaví vlastnost pomocí klíče na řetězec.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Pomocné funkce, která nastaví společných vlastností u bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete použít, stačí vytvořit třídu CMFCFilterChunkValueImpl správného typu  
  
 Příklad:  
  
 CMFCFilterChunkValueImpl bloku;  
  
 hr = bloku. SetBoolValue(PKEY_IsAttachment, true);  
  
 or  
  
 hr = bloku. SetFileTimeValue (PKEY_ItemDate, ftLastModified);  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
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
  
##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl  
 Destructs objektu.  
  
```  
virtual ~CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk  
 Zkopíruje tento blok pro strukturu popisující charakteristiky bloku.  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>Parametry  
 `pStatChunk`  
 Ukazatel na hodnotu cílové popisující charakteristiky bloku.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom  
 Inicializuje tuto hodnotu bloků dat z jiné hodnoty.  
  
```  
void CopyFrom (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pValue`  
 Určuje zdroj hodnotu pro kopírování z.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID  
 Načte bloku identifikátor GUID.  
  
```  
REFGUID GetChunkGUID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na identifikátor GUID identifikace u bloku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID  
 Načte bloku PID (ID vlastnosti).  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Přidejte hodnotu DWORD obsahující identifikátor vlastnosti.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType  
 Načte typ bloku.  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota CHUNKSTATE ve výčtu, která určuje, zda je aktuální bloku vlastnost typ text nebo typ hodnoty vlastnosti.  
  
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
 Načte hodnotu jako přidělené propvariant.  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>Parametry  
 `ppPropVariant`  
 Když funkce vrátí hodnotu, tento parametr obsahuje hodnotu bloku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud byl úspěšně přidělen PROPVARIANT a hodnota bloku byl úspěšně zkopírován do S_OK `ppPropVariant`jinak chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc  
 Vrátí hodnotu nepřiděleného (interní hodnota).  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací aktuální hodnotu bloku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid  
 Kontroluje, zda hodnota této vlastnosti je platný, nebo ne.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je aktuální hodnota bloku platná; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue  
 Přetíženo. Nastaví vlastnost pomocí klíče na booleovskou hodnotu.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `bVal`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk  
 Pomocné funkce, která nastaví společných vlastností u bloku.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak kód chyby.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue  
 Nastavte vlastnost pomocí klíče k typu DWORD.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `dwVal`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue  
 Nastavte vlastnost pomocí klíče k filetime.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `dtVal`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value  
 Nastavte vlastnost pomocí klíče na datovém typu int64.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `nVal`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue  
 Nastavte vlastnost pomocí klíče na typ int.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `nVal`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue  
 Nastavte vlastnost pomocí klíče na DLOUHÝ.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `lVal`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue  
 Nastaví vlastnost pomocí klíče k SystemTime.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `systemTime`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue  
 Nastaví vlastnost pomocí klíče na řetězec.  
  
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
 `pkey`  
 Určuje klíč vlastnost.  
  
 `pszValue`  
 Určuje hodnotu bloku nastavit.  
  
 `chunkType`  
 Příznaky označuje, zda obsahuje tento blok typem text nebo typ hodnoty vlastnosti. Příznak hodnoty jsou převzaty z výčtu CHUNKSTATE.  
  
 `locale`  
 Jazyk a související s poškozeným textu dílčího jazyka. Národní prostředí bloku je dokument indexery používané k provádění dělení textu správné slov. Pokud u bloku je typ text ani typu hodnoty s datovým typem VT_LPWSTR, VT_LPSTR nebo VT_BSTR, toto pole je ignorováno.  
  
 `cwcLenSource`  
 Délka ve znacích zdrojový text, ze kterého byl odvozené aktuální bloku. Nulová hodnota označuje znak po znaku propojeni zdrojový text a odvozené text. Nenulová hodnota znamená, že žádné přímé korespondence existuje.  
  
 `cwcStartSource`  
 Posun, ze kterého zdrojový text pro odvozené bloku spustí v bloku dat zdroje.  
  
 `chunkBreakType`  
 Typ přerušení, která odděluje předchozí bloku od aktuální bloku. Hodnoty jsou CHUNK_BREAKTYPE výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
