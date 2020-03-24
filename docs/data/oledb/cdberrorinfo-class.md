---
title: CDBErrorInfo – třída
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: 8c91beb2a305604f663d5e81b4a534a1699705cf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212014"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo – třída

Poskytuje podporu pro OLE DB zpracování chyb pomocí rozhraní OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Vrátí všechny informace o chybě obsažené v záznamu chyby.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Volá [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) , aby vracel základní informace o zadané chybě.|
|[GetCustomErrorObject](#getcustomerrorobject)|Volá metodu [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) , která vrátí ukazatel na rozhraní objektu Custom Error.|
|[GetErrorInfo](#geterrorinfo)|Volá [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) a vrátí ukazatel rozhraní `IErrorInfo` zadaného záznamu.|
|[GetErrorParameters](#geterrorparameters)|Volá [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) , aby se vracely parametry chyby.|
|[GetErrorRecords](#geterrorrecords)|Získá záznamy chyb pro zadaný objekt.|

## <a name="remarks"></a>Poznámky

Toto rozhraní vrátí uživateli jeden nebo více záznamů o chybách. Napřed zavolejte [CDBErrorInfo:: GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) , aby se získal počet záznamů chyb. Pak zavolejte jednu z funkcí přístupu, jako je například [CDBErrorInfo:: GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), a načtěte informace o chybě pro každý záznam.

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a>CDBErrorInfo:: GetAllErrorInfo

Vrátí všechny typy informací o chybách obsažených v záznamu chyby.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>Parametry

*ulRecordNum*<br/>
pro Číslo s nulovým základem záznamu, pro který mají být vráceny informace o chybě.

*lcid*<br/>
pro ID národního prostředí pro vrácení informací o chybě.

*pbstrDescription*<br/>
mimo Ukazatel na textový popis chyby nebo hodnotu NULL, pokud se národní prostředí nepodporuje. Viz poznámky.

*pbstrSource*<br/>
mimo Ukazatel na řetězec obsahující název součásti, která generovala chybu.

*pguid*<br/>
mimo Ukazatel na identifikátor GUID rozhraní, které definuje chybu.

*pdwHelpContext*<br/>
mimo Ukazatel na ID kontextu nápovědu pro chybu.

*pbstrHelpFile*<br/>
mimo Ukazatel na řetězec obsahující cestu k souboru s informacemi o chybě.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud bylo úspěšné. Další vrácené hodnoty najdete v tématu [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) v *referenci programátora OLE DB* .

### <a name="remarks"></a>Poznámky

Výstupní hodnota *pbstrDescription* je interně získána voláním `IErrorInfo::GetDescription`, která nastaví hodnotu na null, pokud národní prostředí není podporováno, nebo pokud jsou splněny obě následující podmínky:

1. hodnota *LCID* není anglická a

1. hodnota *LCID* není rovna hodnotě vrácené funkcí GetUserDefaultLCID.

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>CDBErrorInfo:: GetBasicErrorInfo

Volá [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) , aby vracel základní informace o chybě, jako je návratový kód a číslo chyby specifické pro poskytovatele.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a>CDBErrorInfo:: GetCustomErrorObject

Volá metodu [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) , která vrátí ukazatel na rozhraní objektu Custom Error.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a>CDBErrorInfo:: GetErrorInfo

Volá [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) a vrátí ukazatel rozhraní [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) na zadaný záznam.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a>CDBErrorInfo:: GetErrorParameters

Volá [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) , aby se vracely parametry chyby.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a>CDBErrorInfo:: GetErrorRecords

Získá záznamy chyb pro zadaný objekt.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Rozhraní objektu, pro který se mají získat záznamy o chybách.

*identifikátor*<br/>
pro IID rozhraní přidruženého k chybě

*pcRecords*<br/>
mimo Ukazatel na počet záznamů chyb (založený na jednom).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Použijte první formu funkce, pokud chcete zjistit, které rozhraní má získat informace o chybě z. V opačném případě použijte druhý formulář.

## <a name="see-also"></a>Viz také

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
