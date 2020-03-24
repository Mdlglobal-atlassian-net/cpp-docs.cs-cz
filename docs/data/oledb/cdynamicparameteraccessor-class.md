---
title: CDynamicParameterAccessor – třída
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: 9c326c337ff210ef9de26b3fd88c0d853832b260
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211863"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor – třída

Podobně jako [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) , ale získá informace o parametrech, které mají být nastaveny voláním rozhraní [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) .

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Požadavky

**Záhlaví**: atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|Konstruktor|
|[GetParam](#getparam)|Načte data parametrů z vyrovnávací paměti.|
|[GetParamCount](#getparamcount)|Načte počet parametrů v přístupovém objektu.|
|[GetParamIO](#getparamio)|Určuje, zda je zadaný parametr vstupní nebo výstupní parametr.|
|[GetParamLength](#getparamlength)|Načte délku zadaného parametru uloženého ve vyrovnávací paměti.|
|[GetParam](#getparamname)|Načte název zadaného parametru.|
|[GetParamStatus](#getparamstatus)|Načte stav zadaného parametru uloženého ve vyrovnávací paměti.|
|[GetParamString](#getparamstring)|Načte řetězcová data určeného parametru uloženého ve vyrovnávací paměti.|
|[GetParamType](#getparamtype)|Načte datový typ zadaného parametru.|
|[SetParam](#setparam)|Nastaví vyrovnávací paměť pomocí dat parametru.|
|[SetParamLength](#setparamlength)|Nastaví délku zadaného parametru uloženého ve vyrovnávací paměti.|
|[SetParamStatus](#setparamstatus)|Nastaví stav zadaného parametru uloženého ve vyrovnávací paměti.|
|[SetParamString](#setparamstring)|Nastaví řetězcová data určeného parametru uloženého ve vyrovnávací paměti.|

## <a name="remarks"></a>Poznámky

Poskytovatel musí podporovat `ICommandWithParameters` pro příjemce, aby tuto třídu používal.

Informace o parametrech jsou uloženy ve vyrovnávací paměti vytvořené a spravované touto třídou. Získejte data parametrů z vyrovnávací paměti pomocí [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) a [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Příklad demonstrující, jak pomocí této třídy spustit SQL Server uloženou proceduru a získat výstupní hodnoty parametrů, najdete v tématu vzorový kód [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) v úložišti [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) na GitHubu.

## <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a><a name="cdynamicparameteraccessor"></a>CDynamicParameterAccessor:: CDynamicParameterAccessor

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>Parametry

*eBlobHandling*<br/>
Určuje způsob zpracování dat objektu BLOB. Výchozí hodnota je DBBLOBHANDLING_DEFAULT. Popis hodnot DBBLOBHANDLINGENUM naleznete v tématu [CDynamicAccessor:: SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) .

*nBlobSize*<br/>
Maximální velikost objektu BLOB v bajtech; data sloupce nad tuto hodnotu se považují za objekt BLOB. Výchozí hodnota je 8 000. Podrobnosti naleznete v tématu [CDynamicAccessor:: SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) .

### <a name="remarks"></a>Poznámky

Další informace o zpracování objektů BLOB naleznete v konstruktoru [CDynamicAccessor:: CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) .

## <a name="cdynamicparameteraccessorgetparam"></a><a name="getparam"></a>CDynamicParameterAccessor:: GetParam

Načte neřetězcová data pro zadaný parametr z vyrovnávací paměti parametru.

### <a name="syntax"></a>Syntaxe

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>Parametry

*CType*<br/>
Parametr s šablonou, který je datovým typem.

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pParamName*<br/>
pro Název parametru.

*pData*<br/>
mimo Ukazatel na paměť obsahující data získaná z vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Pro nešablonované verze odkazuje na paměť obsahující data získaná z vyrovnávací paměti. Pro verze v šabloně vrátí **hodnotu true** při úspěchu nebo **false** při selhání.

Použijte `GetParam` k načtení neřetězcových dat parametrů z vyrovnávací paměti. Pomocí [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) načtěte data parametrů řetězce z vyrovnávací paměti.

## <a name="cdynamicparameteraccessorgetparamcount"></a><a name="getparamcount"></a>CDynamicParameterAccessor:: GetParamCount

Načte počet parametrů uložených ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet parametrů

## <a name="cdynamicparameteraccessorgetparamio"></a><a name="getparamio"></a>CDynamicParameterAccessor:: GetParamIO

Určuje, zda je zadaný parametr vstupní nebo výstupní parametr.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pParamIO*<br/>
Ukazatel na proměnnou obsahující typ `DBPARAMIO` (vstup nebo výstup) zadaného parametru. Je definována takto:

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>Návratová hodnota

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

## <a name="cdynamicparameteraccessorgetparamlength"></a><a name="getparamlength"></a>CDynamicParameterAccessor:: GetParamLength

Načte délku zadaného parametru uloženého ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pLength*<br/>
mimo Ukazatel na proměnnou obsahující délku v bajtech zadaného parametru.

### <a name="remarks"></a>Poznámky

První přepsání vrátí **hodnotu true** nebo **false** při selhání. Druhé přepsání odkazuje na paměť obsahující délku parametru.

## <a name="cdynamicparameteraccessorgetparamname"></a><a name="getparamname"></a>CDynamicParameterAccessor:: GetParam

Načte název zadaného parametru.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

### <a name="return-value"></a>Návratová hodnota

Název zadaného parametru

## <a name="cdynamicparameteraccessorgetparamstatus"></a><a name="getparamstatus"></a>CDynamicParameterAccessor:: GetParamStatus

Načte stav zadaného parametru uloženého ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pStatus*<br/>
mimo Ukazatel na proměnnou, která obsahuje stav DBSTATUS zadaného parametru. Informace o hodnotách DBSTATUS naleznete v tématu [stav](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *referenci programátora OLE DB*, nebo v OLEDB. h vyhledejte DBSTATUS.

### <a name="remarks"></a>Poznámky

První přepsání vrátí **hodnotu true** nebo **false** při selhání. Druhé přepsání odkazuje na paměť obsahující stav zadaného parametru.

## <a name="cdynamicparameteraccessorgetparamstring"></a><a name="getparamstring"></a>CDynamicParameterAccessor:: GetParamString

Načte řetězcová data určeného parametru uloženého ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*strOutput*<br/>
mimo Data řetězce ANSI (`CSimpleStringA`) nebo Unicode (`CSimpleStringW`) zadaného parametru. Měli byste předat parametr typu `CString`, například:

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
mimo Ukazatel na data řetězce ANSI (**char**) nebo Unicode (**WCHAR**) zadaného parametru.

*pMaxLen*<br/>
mimo Ukazatel na velikost vyrovnávací paměti, na kterou ukazuje *pBuffer* (ve znacích, včetně ukončující hodnoty null).

### <a name="remarks"></a>Poznámky

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

Pokud má *pBuffer* hodnotu null, tato metoda nastaví požadovanou velikost vyrovnávací paměti v paměti, na kterou ukazuje *pMaxLen* , a vrátí **hodnotu true** bez kopírování dat.

Tato metoda selže, pokud *pBuffer* vyrovnávací paměti není dostatečně velká pro uložení celého řetězce.

Pomocí `GetParamString` načíst data parametrů řetězce z vyrovnávací paměti. Pomocí [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) načtěte data neřetězcových parametrů z vyrovnávací paměti.

## <a name="cdynamicparameteraccessorgetparamtype"></a><a name="getparamtype"></a>CDynamicParameterAccessor:: GetParamType

Načte datový typ zadaného parametru.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pType*<br/>
mimo Ukazatel na proměnnou obsahující datový typ zadaného parametru.

### <a name="return-value"></a>Návratová hodnota

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

## <a name="cdynamicparameteraccessorsetparam"></a><a name="setparam"></a>CDynamicParameterAccessor:: SetParam

Nastaví vyrovnávací paměť parametrů pomocí zadaných (neřetězcových) dat.

### <a name="syntax"></a>Syntaxe

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Parametry

*CType*<br/>
Parametr s šablonou, který je datovým typem.

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad:

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
pro Název parametru.

*pData*<br/>
pro Ukazatel na paměť obsahující data, která mají být zapsána do vyrovnávací paměti.

*stav*<br/>
pro Stav sloupce DBSTATUS. Informace o hodnotách DBSTATUS naleznete v tématu [stav](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *referenci programátora OLE DB*, nebo v OLEDB. h vyhledejte DBSTATUS.

### <a name="return-value"></a>Návratová hodnota

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

Použijte `SetParam` k nastavení neřetězcových dat parametrů ve vyrovnávací paměti. Použijte [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) k nastavení dat parametrů řetězce ve vyrovnávací paměti.

## <a name="cdynamicparameteraccessorsetparamlength"></a><a name="setparamlength"></a>CDynamicParameterAccessor:: SetParamLength

Nastaví délku zadaného parametru uloženého ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*časový*<br/>
pro Délka zadaného parametru v bajtech

### <a name="remarks"></a>Poznámky

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

## <a name="cdynamicparameteraccessorsetparamstatus"></a><a name="setparamstatus"></a>CDynamicParameterAccessor:: SetParamStatus

Nastaví stav zadaného parametru uloženého ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*stav*<br/>
pro Stav DBSTATUS zadaného parametru Informace o hodnotách DBSTATUS naleznete v tématu [stav](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *referenci programátora OLE DB*, nebo v OLEDB. h vyhledejte DBSTATUS.

### <a name="remarks"></a>Poznámky

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

## <a name="cdynamicparameteraccessorsetparamstring"></a><a name="setparamstring"></a>CDynamicParameterAccessor:: SetParamString

Nastaví řetězcová data určeného parametru uloženého ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
pro Číslo parametru (posun od 1). Parametr 0 je rezervován pro návratové hodnoty. Číslo parametru je index parametru na základě jeho pořadí v SQL nebo ve volání uložené procedury. Příklad najdete v tématu [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) .

*pString*<br/>
pro Ukazatel na data řetězce ANSI (**char**) nebo Unicode (**WCHAR**) zadaného parametru. Viz DBSTATUS v OLEDB. h.

*stav*<br/>
pro Stav DBSTATUS zadaného parametru Informace o hodnotách DBSTATUS naleznete v tématu [stav](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *referenci programátora OLE DB*, nebo v OLEDB. h vyhledejte DBSTATUS.

### <a name="remarks"></a>Poznámky

Vrací **hodnotu true** při úspěchu nebo **false** při selhání.

`SetParamString` dojde k chybě, pokud se pokusíte nastavit řetězec, který je větší než maximální velikost určenou pro *pString*.

Pomocí `SetParamString` nastavovat data parametrů řetězce ve vyrovnávací paměti. Použijte [setParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) k nastavení neřetězcových dat parametrů ve vyrovnávací paměti.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)
