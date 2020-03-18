---
title: CManualAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 80c8f94a417c700f86159de53bd53e4011f78d71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447376"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor – třída

Představuje typ přístupového objektu navržený pro pokročilé použití.

## <a name="syntax"></a>Syntaxe

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddBindEntry](#addbindentry)|Přidá položku vazby do výstupních sloupců.|
|[AddParameterEntry](#addparameterentry)|Přidá položku parametru do přístupového objektu parametru.|
|[CreateAccessor](#createaccessor)|Přiděluje paměť pro sloupce vázání struktury a inicializuje datové členy sloupce.|
|[CreateParameterAccessor](#createparameteraccessor)|Přiděluje paměť pro parametr struktury vazby a inicializuje datové členy parametru.|

## <a name="remarks"></a>Poznámky

Pomocí `CManualAccessor`můžete zadat parametr a výstupní vazbu sloupce voláním funkce za běhu.

## <a name="addbindentry"></a>CManualAccessor:: AddBindEntry

Přidá položku vazby do výstupních sloupců.

### <a name="syntax"></a>Syntaxe

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*wType*<br/>
pro Datový typ.

*nColumnSize*<br/>
pro Velikost sloupce v bajtech

*pData*<br/>
pro Ukazatel na data sloupce uložená ve vyrovnávací paměti.

*pLength*<br/>
pro V případě potřeby ukazatel na délku pole.

*pStatus*<br/>
pro V případě potřeby ukazatel na proměnnou, která má být vázána na stav sloupce.

### <a name="remarks"></a>Poznámky

Chcete-li použít tuto funkci, musíte nejprve volat [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md). Nelze přidat více položek, než je počet sloupců zadaný v `CreateAccessor`.

## <a name="addparameterentry"></a>CManualAccessor:: AddParameterEntry

Přidá položku parametru do struktur vstupních parametrů.

### <a name="syntax"></a>Syntaxe

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo parametru

*wType*<br/>
pro Datový typ.

*nColumnSize*<br/>
pro Velikost sloupce v bajtech

*pData*<br/>
pro Ukazatel na data sloupce uložená ve vyrovnávací paměti.

*pLength*<br/>
pro V případě potřeby ukazatel na délku pole.

*pStatus*<br/>
pro V případě potřeby ukazatel na proměnnou, která má být vázána na stav sloupce.

*eParamIO*<br/>
pro Určuje, zda je parametr, ke kterému je přidružena vazba, vstupní, vstupní/výstupní nebo výstupní parametr.

### <a name="remarks"></a>Poznámky

Chcete-li použít tuto funkci, musíte nejprve volat [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).

## <a name="createaccessor"></a>CManualAccessor:: CreateAccessor

Přiděluje paměť pro sloupce vázání struktury a inicializuje datové členy sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parametry

*nBindEntries*<br/>
pro Počet sloupců Toto číslo by mělo odpovídat počtu volání funkce [CManualAccessor:: AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) .

*pBuffer*<br/>
pro Ukazatel na vyrovnávací paměť, kde jsou uloženy výstupní sloupce.

*nBufferSize*<br/>
pro Velikost vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Před voláním funkce `CManualAccessor::AddBindEntry` volejte tuto funkci.

## <a name="createparameteraccessor"></a>CManualAccessor:: CreateParameterAccessor

Přiděluje paměť pro parametr struktury vazby a inicializuje datové členy parametru.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parametry

*nBindEntries*<br/>
pro Počet sloupců

*pBuffer*<br/>
pro Ukazatel na vyrovnávací paměť, kde jsou uloženy vstupní sloupce.

*nBufferSize*<br/>
pro Velikost vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tuto funkci je nutné volat před voláním [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).

## <a name="see-also"></a>Viz také

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)