---
title: IRowsetChangeImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: 1e07289a2d0fb283a20657797db5f915c06a39ad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446324"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl – třída

Šablony OLE DB implementaci rozhraní [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) ve specifikaci OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída odvozená od `IRowsetChangeImpl`.

*Storage*<br/>
Záznam uživatele.

*BaseInterface*<br/>
Základní třída pro rozhraní, například `IRowsetChange`.

*RowClass*<br/>
Jednotka úložiště pro popisovač řádku

*MapClass*<br/>
Jednotka úložiště pro všechny obsluhy řádků držené zprostředkovatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používané s IRowsetChange)

|||
|-|-|
|[DeleteRows](#deleterows)|Odstraní řádky ze sady řádků.|
|[InsertRow](#insertrow)|Vloží řádek do sady řádků.|
|[SetData](#setdata)|Nastaví hodnoty dat v jednom nebo více sloupcích.|

### <a name="implementation-method-callback"></a>Metoda implementace (zpětné volání)

|||
|-|-|
|[FlushData](#flushdata)|Přepsáno zprostředkovatelem pro zápis dat do svého úložiště.|

## <a name="remarks"></a>Poznámky

Toto rozhraní zodpovídá za okamžité operace zápisu do úložiště dat. "Okamžité" znamená, že když koncový uživatel (osoba používající příjemce) provede změny, tyto změny se okamžitě přenesou do úložiště dat (a nedá se vrátit zpátky).

`IRowsetChangeImpl` implementuje rozhraní OLE DB `IRowsetChange`, které umožňuje aktualizovat hodnoty sloupců ve stávajících řádcích, odstraňovat řádky a vkládat nové řádky.

Implementace šablon OLE DB podporuje všechny základní metody (`SetData`, `InsertRow`a `DeleteRows`).

> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si před pokusem o implementaci poskytovatele přečetli následující dokumentaci:

- [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)

- Kapitola 6 *referenčních informací programátora OLE DB*

- Viz také způsob použití třídy `RUpdateRowset` v ukázce [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="deleterows"></a>IRowsetChangeImpl::D eleteRows

Odstraní řádky ze sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange::D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="insertrow"></a>IRowsetChangeImpl:: InsertRow

Vytvoří a inicializuje nový řádek v sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange:: InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="setdata"></a>IRowsetChangeImpl:: SetData

Nastaví hodnoty dat v jednom nebo více sloupcích.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="flushdata"></a>IRowsetChangeImpl:: FlushData

Přepsáno zprostředkovatelem pro zápis dat do svého úložiště.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parametry

*hRowToFlush*<br/>
pro Zpracujte řádky dat. Typ tohoto řádku je určen z argumentu šablony *RowClass* třídy `IRowsetImpl` (ve výchozím nastavení`CSimpleRow`).

*hAccessorToFlush*<br/>
pro Popisovač přistupujícího objektu, který obsahuje informace o vazbě a informace o typu v jeho `PROVIDER_MAP` (viz [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)