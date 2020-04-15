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
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376950"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl – třída

Ole DB šablony implementace rozhraní [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) ve specifikaci OLE DB.

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

*T*<br/>
Třída odvozená `IRowsetChangeImpl`z .

*Storage*<br/>
Záznam uživatele.

*Základní rozhraní*<br/>
Základní třída pro rozhraní, `IRowsetChange`například .

*Třída řádku*<br/>
Úložná jednotka pro popisovač řádku.

*Třída Mapy*<br/>
Úložná jednotka pro všechny popisovače řádků držené zprostředkovatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)

|||
|-|-|
|[Odstranit řádky](#deleterows)|Odstraní řádky ze sady řádků.|
|[Vložit řádek](#insertrow)|Vloží řádek do sady řádků.|
|[Setdata](#setdata)|Nastaví hodnoty dat v jednom nebo více sloupcích.|

### <a name="implementation-method-callback"></a>Metoda implementace (zpětné volání)

|||
|-|-|
|[Flushdata](#flushdata)|Přepsáno zprostředkovatelem k potvrzení dat do jeho úložiště.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je zodpovědný za okamžité operace zápisu do úložiště dat. "Okamžité" znamená, že když koncový uživatel (osoba, která používá spotřebitele) provede jakékoli změny, tyto změny jsou okamžitě přeneseny do úložiště dat (a nelze je vrátit zpět).

`IRowsetChangeImpl`implementuje rozhraní `IRowsetChange` OLE DB, které umožňuje aktualizaci hodnot sloupců v existujících řádcích, odstranění řádků a vložení nových řádků.

Implementace šablon OLE DB podporuje všechny`SetData`základní `InsertRow`metody `DeleteRows`( , , a ).

> [!IMPORTANT]
> Důrazně doporučujeme, abyste si před pokusem o implementaci zprostředkovatele přečetli následující dokumentaci:

- [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)

- Kapitola 6 *referenční příručky programátora OLE DB*

- Také zobrazit, `RUpdateRowset` jak se používá třída v [updatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku.

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::DeleteRows

Odstraní řádky ze sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl::InsertRow

Vytvoří a inicializuje nový řádek v sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl::SetData

Nastaví hodnoty dat v jednom nebo více sloupcích.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl::FlushData

Přepsáno zprostředkovatelem k potvrzení dat do jeho úložiště.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parametry

*hRowToFlush*<br/>
[v] Zpracovat řádky pro data. Typ tohoto řádku je určen z argumentu `IRowsetImpl` šablony`CSimpleRow` *RowClass* třídy (ve výchozím nastavení).

*hPřipřístupkaToFlush*<br/>
[v] Zpracování přístupového pole, který obsahuje informace o `PROVIDER_MAP` vazbě a informace o typu v jeho (viz [IAccessorImpl).](../../data/oledb/iaccessorimpl-class.md)

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatelů OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
