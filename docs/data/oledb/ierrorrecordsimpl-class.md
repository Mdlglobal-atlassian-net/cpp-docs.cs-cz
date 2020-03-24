---
title: IErrorRecordsImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
ms.openlocfilehash: 40ac0b248e1e90dae29a787d59f6ded9581aca70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210597"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl – třída

Implementuje rozhraní OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , přidávání záznamů do a načítání záznamů z datového členu ([M_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) typu **CAtlArray <** `RecordClass` **>** .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída odvozená od `IErrorRecordsImpl`.

*RecordClass*<br/>
Třída, která představuje objekt chyby OLE DB.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|Získá řetězec s popisem chyby z záznamu chyby.|
|[GetErrorGUID](#geterrorguid)|Získá identifikátor GUID chyby z záznamu chyby.|
|[GetErrorHelpContext](#geterrorhelpcontext)|Získá ID kontextu helpu z záznamu chyby.|
|[GetErrorHelpFile](#geterrorhelpfile)|Získá úplnou cestu k souboru s názvem z záznamu chyby.|
|[GetErrorSource](#geterrorsource)|Získá zdrojový kód chyby z záznamu chyby.|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|Přidá záznam do objektu chyby OLE DB.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Vrátí základní informace o chybě, jako je návratový kód a číslo chyby specifické pro poskytovatele.|
|[GetCustomErrorObject](#getcustomerrorobject)|Vrátí ukazatel na rozhraní objektu vlastní chyby.|
|[GetErrorInfo](#geterrorinfo)|Vrátí ukazatel rozhraní [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) na zadaném záznamu.|
|[GetErrorParameters](#geterrorparameters)|Vrátí parametry chyby.|
|[GetRecordCount](#getrecordcount)|Vrátí počet záznamů v objektu OLE DB záznamu.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_rgErrors](#rgerrors)|Pole záznamů chyb.|

## <a name="ierrorrecordsimplgeterrordescriptionstring"></a><a name="geterrordescriptionstring"></a>IErrorRecordsImpl:: GetErrorDescriptionString

Získá řetězec s popisem chyby z záznamu chyby.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Záznam `ERRORINFO` v rozhraní `IErrorInfo`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec popisující chybu.

## <a name="ierrorrecordsimplgeterrorguid"></a><a name="geterrorguid"></a>IErrorRecordsImpl:: GetErrorGUID

Získá identifikátor GUID chyby z záznamu chyby.

### <a name="syntax"></a>Syntaxe

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Záznam `ERRORINFO` v rozhraní `IErrorInfo`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na identifikátor GUID pro chybu.

## <a name="ierrorrecordsimplgeterrorhelpcontext"></a><a name="geterrorhelpcontext"></a>IErrorRecordsImpl:: GetErrorHelpContext

Získá ID kontextu helpu z záznamu chyby.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Záznam `ERRORINFO` v rozhraní `IErrorInfo`.

### <a name="return-value"></a>Návratová hodnota

ID kontextu nápovědu pro chybu.

## <a name="ierrorrecordsimplgeterrorhelpfile"></a><a name="geterrorhelpfile"></a>IErrorRecordsImpl:: GetErrorHelpFile

Získá název cesty souboru Help z záznamu chyby.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Záznam `ERRORINFO` v rozhraní `IErrorInfo`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který obsahuje název cesty souboru s nápovědu pro chybu.

## <a name="ierrorrecordsimplgeterrorsource"></a><a name="geterrorsource"></a>IErrorRecordsImpl:: GetErrorSource

Získá zdrojový kód, který způsobil chybu v záznamu chyby.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Záznam `ERRORINFO` v rozhraní `IErrorInfo`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující zdrojový kód chyby.

## <a name="ierrorrecordsimpladderrorrecord"></a><a name="adderrorrecord"></a>IErrorRecordsImpl:: AddErrorRecord

Přidá záznam do objektu chyby OLE DB.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="ierrorrecordsimplgetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>IErrorRecordsImpl:: GetBasicErrorInfo

Vrátí základní informace o chybě, jako je návratový kód a číslo chyby specifické pro poskytovatele.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="ierrorrecordsimplgetcustomerrorobject"></a><a name="getcustomerrorobject"></a>IErrorRecordsImpl:: GetCustomErrorObject

Vrátí ukazatel na rozhraní objektu vlastní chyby.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="ierrorrecordsimplgeterrorinfo"></a><a name="geterrorinfo"></a>IErrorRecordsImpl:: GetErrorInfo

Vrátí ukazatel rozhraní [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) na zadaném záznamu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="ierrorrecordsimplgeterrorparameters"></a><a name="geterrorparameters"></a>IErrorRecordsImpl:: GetErrorParameters

Vrátí parametry chyby.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="ierrorrecordsimplgetrecordcount"></a><a name="getrecordcount"></a>IErrorRecordsImpl:: GetRecordCount

Vrátí počet záznamů v objektu OLE DB záznamu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="ierrorrecordsimplm_rgerrors"></a><a name="rgerrors"></a>IErrorRecordsImpl:: m_rgErrors

Pole záznamů chyb.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
