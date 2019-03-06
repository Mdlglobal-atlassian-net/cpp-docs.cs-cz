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
- GetCustomErrorObject
- GetErrorInfo
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
ms.openlocfilehash: 24c64c489f52cb4746e3e2b6ebb52bb81870cffd
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420190"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl – třída

Implementuje rozhraní OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) rozhraní, přidání záznamů do a načtení záznamů z datového členu ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) typu **catlarray – <** `RecordClass`**>**.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída odvozená z `IErrorRecordsImpl`.

*RecordClass*<br/>
Třída, která představuje objekt error OLE DB.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|Získá řetězec popisu chyby z záznam chyby.|
|[GetErrorGUID](#geterrorguid)|Získá chybu identifikátoru GUID z záznam chyby.|
|[Geterrorhelpcontext –](#geterrorhelpcontext)|Získá ID kontextové nápovědy z záznam chyby.|
|[Geterrorhelpfile –](#geterrorhelpfile)|Získá úplnou cestu v souboru nápovědy z záznam chyby.|
|[GetErrorSource](#geterrorsource)|Získá zdrojový kód chyby z záznam chyby.|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|Přidá záznam do objektu Chyba OLE DB.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Vrátí základní informace o této chybě, jako je například návratový kód a číslo chyby specifické pro zprostředkovatele.|
|[GetCustomErrorObject](#getcustomerrorobject)|Vrací ukazatel na rozhraní pro objekt vlastních chyb.|
|[GetErrorInfo](#geterrorinfo)|Vrátí [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) ukazatel rozhraní na zadaný záznam.|
|[Geterrorparameters –](#geterrorparameters)|Vrátí parametry chyby.|
|[GetRecordCount](#getrecordcount)|Vrátí počet záznamů v záznamu objektu OLE DB.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_rgErrors](#rgerrors)|Pole Chyba záznamů.|

## <a name="geterrordescriptionstring"></a> IErrorRecordsImpl::GetErrorDescriptionString

Získá řetězec popisu chyby z záznam chyby.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` v záznamu `IErrorInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec popisující chybu.

## <a name="geterrorguid"></a> IErrorRecordsImpl::GetErrorGUID

Získá chybu identifikátoru GUID z záznam chyby.

### <a name="syntax"></a>Syntaxe

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` v záznamu `IErrorInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Odkaz na identifikátor GUID pro chybu.

## <a name="geterrorhelpcontext"></a> IErrorRecordsImpl::GetErrorHelpContext

Získá ID kontextové nápovědy z záznam chyby.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` v záznamu `IErrorInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

ID kontextové nápovědy k chybě.

## <a name="geterrorhelpfile"></a> IErrorRecordsImpl::GetErrorHelpFile

Získá název cesty souboru nápovědy z záznam chyby.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` v záznamu `IErrorInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který obsahuje název cesty souboru nápovědy k chybě.

## <a name="geterrorsource"></a> IErrorRecordsImpl::GetErrorSource

Získá zdrojový kód, který způsobil chybu z záznam chyby.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` v záznamu `IErrorInfo` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který obsahuje zdrojový kód chyby.

## <a name="adderrorrecord"></a> IErrorRecordsImpl::AddErrorRecord

Přidá záznam do objektu Chyba OLE DB.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IErrorRecords::AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="getbasicerrorinfo"></a> IErrorRecordsImpl::GetBasicErrorInfo

Vrátí základní informace o této chybě, jako je například návratový kód a číslo chyby specifické pro zprostředkovatele.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="getcustomerrorobject"></a> IErrorRecordsImpl::GetCustomErrorObject

Vrací ukazatel na rozhraní pro objekt vlastních chyb.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="geterrorinfo"></a> IErrorRecordsImpl::GetErrorInfo

Vrátí [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) ukazatel rozhraní na zadaný záznam.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="geterrorparameters"></a> IErrorRecordsImpl::GetErrorParameters

Vrátí parametry chyby.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="getrecordcount"></a> IErrorRecordsImpl::GetRecordCount

Vrátí počet záznamů v záznamu objektu OLE DB.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IErrorRecords::GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="rgerrors"></a> IErrorRecordsImpl::m_rgErrors

Pole Chyba záznamů.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)