---
title: IRowsetImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: db12af1aecc094e6c04ab37b5a70a0acd97e39e9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210415"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl – třída

Poskytuje implementaci rozhraní `IRowset`.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IRowsetImpl`.

*RowsetInterface*<br/>
Třída odvozená od `IRowsetImpl`.

*RowClass*<br/>
Jednotka úložiště pro `HROW`.

*MapClass*<br/>
Jednotka úložiště pro všechny obsluhy řádků držené zprostředkovatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRefRows](#addrefrows)|Přidá počet odkazů do existujícího popisovače řádku.|
|[CreateRow](#createrow)|Volá se [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) k přidělení nového `HROW`. Nevoláno přímo uživatelem.|
|[GetData](#getdata)|Načte data z kopie řádku sady řádků.|
|[GetDBStatus](#getdbstatus)|Vrátí stav pro zadané pole.|
|[GetNextRows](#getnextrows)|Načte řádky postupně a pamatuje předchozí pozici.|
|[IRowsetImpl](#irowsetimpl)|Konstruktor Nevoláno přímo uživatelem.|
|[RefRows](#refrows)|Volá se [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) a [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). Nevoláno přímo uživatelem.|
|[ReleaseRows](#releaserows)|Uvolní řádky.|
|[Volání metody RestartPosition](#restartposition)|Přemístí další pozici načtení na počáteční pozici; To znamená, že při prvním vytvoření sady řádků.|
|[SetDBStatus](#setdbstatus)|Nastaví pro zadané pole příznaky stavu.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Určuje, zda zprostředkovatel podporuje zpětné načítání.|
|[m_bCanScrollBack](#bcanscrollback)|Označuje, zda může být u poskytovatele posunuto kurzor zpět.|
|[m_bReset](#breset)|Označuje, zda poskytovatel obnovil pozici kurzoru. To má zvláštní význam při posouvání zpět nebo načítání zpětně v [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|
|[m_iRowset](#irowset)|Index sady řádků představující kurzor.|
|[m_rgRowHandles](#rgrowhandles)|Seznam popisovačů řádků.|

## <a name="remarks"></a>Poznámky

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) je základní rozhraní sady řádků.

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a>IRowsetImpl:: AddRefRows

Přidá počet odkazů do existujícího popisovače řádku.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Viz [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a>IRowsetImpl:: CreateRow

Pomocná metoda, kterou volá [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) k přidělení nového `HROW`.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>Parametry

*lRowsOffset*<br/>
Pozice kurzoru řádku, který se má vytvořit

*cRowsObtained*<br/>
Odkaz předaný uživateli, který indikuje počet vytvořených řádků.

*rgRows*<br/>
Do volajícího bylo vráceno pole `HROW`s nově vytvořenými obslužnými rutinami řádků.

### <a name="remarks"></a>Poznámky

Pokud řádek existuje, tato metoda volá [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) a vrátí. V opačném případě přidělí novou instanci proměnné šablony RowClass a přidá ji do [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).

## <a name="irowsetimplgetdata"></a><a name="getdata"></a>IRowsetImpl:: GetData

Načte data z kopie řádku sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) v *referenci programátora OLE DB*.

Některé parametry odpovídají *OLE DB referenční parametry programátora* různých názvů, které jsou popsány v `IRowset::GetData`:

|Parametry šablony OLE DB|*OLE DB referenční parametry programátora*|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Poznámky

Také zpracovává převod dat pomocí OLE DB DLL pro převod dat.

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a>IRowsetImpl:: GetDBStatus

Vrátí příznak stavu DBSTATUS pro zadané pole.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Parametry

*currentRow*<br/>
pro Aktuální řádek.

*columnNames*<br/>
pro Sloupec, pro který se požaduje stav

### <a name="return-value"></a>Návratová hodnota

Příznaky [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) pro sloupec.

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a>IRowsetImpl:: GetNextRows

Načte řádky postupně a pamatuje předchozí pozici.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parametry

Viz [IRowset:: GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a>IRowsetImpl:: IRowsetImpl

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Poznámky

Tuto metodu obvykle nemusíte volat přímo.

## <a name="irowsetimplrefrows"></a><a name="refrows"></a>IRowsetImpl:: RefRows

Volá se [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) a [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) pro zvýšení nebo uvolnění počtu odkazů na existující popisovač řádku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Parametry

Viz [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a>IRowsetImpl:: ReleaseRows

Uvolní řádky.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Viz [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a>IRowsetImpl:: volání metody RestartPosition

Přemístí další pozici načtení na počáteční pozici; To znamená, že při prvním vytvoření sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Parametry

Viz [IRowset:: volání metody RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Pozice sady řádků je nedefinovaná, dokud není volána `GetNextRow`. Zpětně můžete přejít v rowet voláním `RestartPosition` a následným načtením nebo posouváním zpět.

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a>IRowsetImpl:: SetDBStatus

Nastaví příznak stavu DBSTATUS pro zadané pole.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Parametry

*statusFlags*<br/>
Příznaky [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) pro nastavení sloupce.

*currentRow*<br/>
Aktuální řádek.

*Vlastnost ColumnInfo*<br/>
Sloupec, pro který se nastavuje stav

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Zprostředkovatel Přepisuje tuto funkci, aby poskytoval zvláštní zpracování pro DBSTATUS_S_ISNULL a DBSTATUS_S_DEFAULT.

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a>IRowsetImpl:: m_bCanFetchBack

Určuje, zda zprostředkovatel podporuje zpětné načítání.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Poznámky

Odkazuje na vlastnost `DBPROP_CANFETCHBACKWARDS` ve skupině `DBPROPSET_ROWSET`. Poskytovatel musí podporovat `DBPROP_CANFETCHBACKWARDS`, aby `m_bCanFetchBackwards` na **hodnotu true**.

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a>IRowsetImpl:: m_bCanScrollBack

Označuje, zda může být u poskytovatele posunuto kurzor zpět.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Poznámky

Odkazuje na vlastnost `DBPROP_CANSCROLLBACKWARDS` ve skupině `DBPROPSET_ROWSET`. Poskytovatel musí podporovat `DBPROP_CANSCROLLBACKWARDS`, aby `m_bCanFetchBackwards` na **hodnotu true**.

## <a name="irowsetimplm_breset"></a><a name="breset"></a>IRowsetImpl:: m_bReset

Bitový příznak, pomocí kterého lze určit, zda je pozice kurzoru definována v sadě řádků.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Poznámky

Pokud příjemce volá [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) se záporným `lOffset` nebo *rozvětvení* a `m_bReset` je true, `GetNextRows` přesune na konec sady řádků. Pokud je `m_bReset` false, příjemce obdrží kód chyby v souladu se specifikací OLE DB. Příznak `m_bReset` se nastaví na **hodnotu true** při prvním vytvoření sady řádků a když příjemce volá [IRowsetImpl:: volání metody RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Je nastavena na **hodnotu false** při volání `GetNextRows`.

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a>IRowsetImpl:: m_iRowset

Index sady řádků představující kurzor.

### <a name="syntax"></a>Syntaxe

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a>IRowsetImpl:: m_rgRowHandles

Mapa popisovačů řádků aktuálně obsažených poskytovatelem v reakci na `GetNextRows`.

### <a name="syntax"></a>Syntaxe

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Poznámky

Popisovače řádků se odeberou voláním `ReleaseRows`. Další informace najdete v tématu [Přehled IRowsetImpl](../../data/oledb/irowsetimpl-class.md) pro definici *MapClass*.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow – třída](../../data/oledb/csimplerow-class.md)
