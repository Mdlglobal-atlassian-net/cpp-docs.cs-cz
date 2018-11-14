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
ms.openlocfilehash: c2cc67e6e837844356a071aa362dcca85eca24e4
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556969"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor – třída

Podobně jako [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ale získává informace o parametrech nastavit voláním [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Požadavky

**Hlavička**: také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|Konstruktor|
|[GetParam](#getparam)|Načte data parametrů z vyrovnávací paměti.|
|[GetParamCount](#getparamcount)|Získá počet parametrů přístupového objektu.|
|[GetParamIO](#getparamio)|Určuje, zda je zadaný parametr jako vstupní nebo výstupní parametr.|
|[GetParamLength](#getparamlength)|Načte Délka zadaného parametru uloženy ve vyrovnávací paměti.|
|[GetParamName](#getparamname)|Načte název zadaného parametru.|
|[GetParamStatus](#getparamstatus)|Načte stav zadaný parametr uloženy ve vyrovnávací paměti.|
|[GetParamString](#getparamstring)|Načte data řetězce zadaného parametru uloženy ve vyrovnávací paměti.|
|[GetParamType](#getparamtype)|Načte datový typ zadaný parametr.|
|[SetParam](#setparam)|Nastaví vyrovnávací paměť pomocí data parametrů.|
|[SetParamLength](#setparamlength)|Nastaví délku zadaný parametr uloženy ve vyrovnávací paměti.|
|[Setparamstatus –](#setparamstatus)|Nastaví stav zadaný parametr uloženy ve vyrovnávací paměti.|
|[Setparamstring –](#setparamstring)|Nastaví data řetězce zadaného parametru uloženy ve vyrovnávací paměti.|

## <a name="remarks"></a>Poznámky

Zprostředkovatel musí podporovat `ICommandWithParameters` pro spotřebitele pro tuto třídu používají.

Parametr informace jsou uloženy ve vyrovnávací paměti, vytvářet a spravovat touto třídou. Získejte data parametrů z vyrovnávací paměti pomocí [GetParam –](../../data/oledb/cdynamicparameteraccessor-getparam.md) a [GetParamType –](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Příklad ukazuje, jak použít tuto třídu pro spuštění systému SQL Server uložené procedury a získat hodnoty výstupních parametrů, najdete v článku [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) ukázkový kód v [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) úložišti na Githubu.

## <a name="cdynamicparameteraccessor"></a> CDynamicParameterAccessor::CDynamicParameterAccessor

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
Určuje, jak má být zpracována datový objekt BLOB. Výchozí hodnota je DBBLOBHANDLING_DEFAULT. Zobrazit [CDynamicAccessor::SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) popis DBBLOBHANDLINGENUM hodnoty.

*nBlobSize*<br/>
Maximální velikost objektu BLOB v bajtech; sloupec data v průběhu této hodnoty je považován za objekt BLOB. Výchozí hodnota je 8 000. Zobrazit [CDynamicAccessor::SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) podrobnosti.

### <a name="remarks"></a>Poznámky

Zobrazit [CDynamicAccessor::CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) konstruktor pro další informace o zpracování objektů BLOB.

## <a name="getparam"></a> CDynamicParameterAccessor::GetParam

Načte data neřetězcový pro zadaný parametr z parametru vyrovnávací paměti.

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

*ctype*<br/>
Parametr bez vizuálního vzhledu, který je datového typu.

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*pParamName*<br/>
[in] Název parametru.

*pData*<br/>
[out] Ukazatel na paměti, který obsahuje data načtená z vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Pro nešablonové verze odkazuje na paměti, který obsahuje data načíst z vyrovnávací paměti. Šablony verzí, vrátí **true** v případě úspěchu nebo **false** při selhání.

Použití `GetParam` k načtení neřetězcový parametr dat z vyrovnávací paměti. Použití [getparamstring –](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) načíst data parametru řetězce z vyrovnávací paměti.

## <a name="getparamcount"></a> CDynamicParameterAccessor::GetParamCount

Získá počet parametrů, které jsou uloženy ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet parametrů.

## <a name="getparamio"></a> CDynamicParameterAccessor::GetParamIO

Určuje, zda je zadaný parametr jako vstupní nebo výstupní parametr.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*pParamIO*<br/>
Ukazatel na proměnnou obsahující `DBPARAMIO` (vstupní nebo výstupní) typu zadaného parametru. Je definovaná následujícím způsobem:

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** v případě úspěchu nebo **false** při selhání.

## <a name="getparamlength"></a> CDynamicParameterAccessor::GetParamLength

Načte Délka zadaného parametru uloženy ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*pLength*<br/>
[out] Ukazatel na proměnnou obsahující délku v bajtech zadaný parametr.

### <a name="remarks"></a>Poznámky

První přepsat vrátí **true** v případě úspěchu nebo **false** při selhání. Druhá přepsat odkazuje na paměti, který obsahuje délku parametru.

## <a name="getparamname"></a> CDynamicParameterAccessor::GetParamName

Načte název zadaný parametr.

### <a name="syntax"></a>Syntaxe

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

### <a name="return-value"></a>Návratová hodnota

Název zadaný parametr.

## <a name="getparamstatus"></a> CDynamicParameterAccessor::GetParamStatus

Načte stav zadaný parametr uloženy ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*pStatus*<br/>
[out] Ukazatel na proměnnou obsahující stav DBSTATUS zadaný parametr. Informace o hodnotách DBSTATUS, naleznete v tématu [stav](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) v *OLE DB referenční informace pro programátory*, nebo vyhledejte DBSTATUS oledb.h.

### <a name="remarks"></a>Poznámky

První přepsat vrátí **true** v případě úspěchu nebo **false** při selhání. Druhá přepsat odkazuje na paměti, který obsahuje stav zadaný parametr.

## <a name="getparamstring"></a> CDynamicParameterAccessor::GetParamString

Načte data řetězce zadaného parametru uloženy ve vyrovnávací paměti.

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
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*strOutput*<br/>
[out] ANSI (`CSimpleStringA`) nebo Unicode (`CSimpleStringW`) data zadaný parametr řetězce. Je třeba předat parametr typu `CString`, například:

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
[out] Ukazatel na ANSI (**CHAR**) nebo Unicode (**WCHAR**) data zadaný parametr řetězce.

*pMaxLen*<br/>
[out] Ukazatel na velikost vyrovnávací paměti, na které odkazuje *pBuffer* (ve znacích, včetně ukončujícího znaku NULL).

### <a name="remarks"></a>Poznámky

Vrátí **true** v případě úspěchu nebo **false** při selhání.

Pokud *pBuffer* má hodnotu NULL, tato metoda nastaví velikost požadované vyrovnávací paměti v paměti, na které odkazuje *pMaxLen* a vrátit **true** bez kopírování data.

Tato metoda se nezdaří, pokud vyrovnávací paměť *pBuffer* není dostatečně velký, aby se tak, aby obsahovala celý řetězec.

Použití `GetParamString` načíst data parametru řetězce z vyrovnávací paměti. Použití [GetParam –](../../data/oledb/cdynamicparameteraccessor-getparam.md) k načtení neřetězcový parametr dat z vyrovnávací paměti.

## <a name="getparamtype"></a> CDynamicParameterAccessor::GetParamType

Načte datový typ zadaný parametr.

### <a name="syntax"></a>Syntaxe

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*pType*<br/>
[out] Ukazatel na proměnnou obsahující datový typ zadaný parametr.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** v případě úspěchu nebo **false** při selhání.

## <a name="setparam"></a> CDynamicParameterAccessor::SetParam

Nastaví parametr vyrovnávací paměti, pomocí zadaného data (bez řetězce).

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

*ctype*<br/>
Parametr bez vizuálního vzhledu, který je datového typu.

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Příklad:

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
[in] Název parametru.

*pData*<br/>
[in] Ukazatel na paměť obsahující data, která mají být zapsána do vyrovnávací paměti.

*Stav*<br/>
[in] Stav sloupce je DBSTATUS. Informace o hodnotách DBSTATUS, naleznete v tématu [stav](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) v *OLE DB referenční informace pro programátory*, nebo vyhledejte DBSTATUS oledb.h.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** v případě úspěchu nebo **false** při selhání.

Použití `SetParam` nastavit neřetězcový parametr data ve vyrovnávací paměti. Použití [setparamstring –](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) nastavení data parametru řetězce ve vyrovnávací paměti.

## <a name="setparamlength"></a> CDynamicParameterAccessor::SetParamLength

Nastaví délku zadaný parametr uloženy ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*Délka*<br/>
[in] Délka zadaného parametru v bajtech.

### <a name="remarks"></a>Poznámky

Vrátí **true** v případě úspěchu nebo **false** při selhání.

## <a name="setparamstatus"></a> CDynamicParameterAccessor::SetParamStatus

Nastaví stav zadaný parametr uloženy ve vyrovnávací paměti.

### <a name="syntax"></a>Syntaxe

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>Parametry

*nParam*<br/>
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*Stav*<br/>
[in] Stav DBSTATUS zadaný parametr. Informace o hodnotách DBSTATUS, naleznete v tématu [stav](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) v *OLE DB referenční informace pro programátory*, nebo vyhledejte DBSTATUS oledb.h.

### <a name="remarks"></a>Poznámky

Vrátí **true** v případě úspěchu nebo **false** při selhání.

## <a name="setparamstring"></a> CDynamicParameterAccessor::SetParamString

Nastaví data řetězce zadaného parametru uloženy ve vyrovnávací paměti.

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
[in] Číslo parametru (posun od 1). Parametr 0 je vyhrazený pro vrácené hodnoty. Počet parametrů je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Zobrazit [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.

*pString*<br/>
[in] Ukazatel na ANSI (**CHAR**) nebo Unicode (**WCHAR**) data zadaný parametr řetězce. Zobrazit DBSTATUS v oledb.h.

*Stav*<br/>
[in] Stav DBSTATUS zadaný parametr. Informace o hodnotách DBSTATUS, naleznete v tématu [stav](https://docs.microsoft.com/previous-versions/windows/desktop/ms722617(v=vs.85)) v *OLE DB referenční informace pro programátory*, nebo vyhledejte DBSTATUS oledb.h.

### <a name="remarks"></a>Poznámky

Vrátí **true** v případě úspěchu nebo **false** při selhání.

`SetParamString` selže, pokud se pokusíte nastavit řetězec, který je větší než maximální velikost zadaná pro *pString*.

Použití `SetParamString` nastavení data parametru řetězce ve vyrovnávací paměti. Použití [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) nastavit neřetězcový parametr data ve vyrovnávací paměti.

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)