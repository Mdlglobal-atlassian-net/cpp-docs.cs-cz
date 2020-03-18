---
title: IRowsetUpdateImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: dba962c761fac0408a3c68a46ec6447aa7832522
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444074"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl – třída

Implementace šablon OLE DB rozhraní [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída odvozená od `IRowsetUpdateImpl`.

*Storage*<br/>
Záznam uživatele.

*UpdateArray*<br/>
Pole obsahující data uložená v mezipaměti pro aktualizaci sady řádků.

*RowClass*<br/>
Jednotka úložiště pro `HROW`.

*MapClass*<br/>
Jednotka úložiště pro všechny obsluhy řádků držené zprostředkovatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používané s IRowsetChange)

|||
|-|-|
|[SetData](#setdata)|Nastaví hodnoty dat v jednom nebo více sloupcích.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Metody rozhraní (používané s IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Načte data, která se na zdroj dat naposled přenáší nebo získají, a ignoruje probíhající změny.|
|[GetPendingRows](#getpendingrows)|Vrátí seznam řádků s nedokončenými změnami.|
|[GetRowStatus](#getrowstatus)|Vrátí stav zadaných řádků.|
|[Vrátit zpět](#undo)|Vrátí na řádku od posledního načtení nebo aktualizace změny.|
|[Aktualizace](#update)|Přenese všechny změny provedené na řádku od posledního načtení nebo aktualizace.|

### <a name="implementation-methods-callback"></a>Metody implementace (zpětné volání)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Slouží ke kontrole zabezpečení, integrity a tak dále před povolením aktualizací.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Obsahuje původní data pro odloženou operaci.|

## <a name="remarks"></a>Poznámky

Měli byste si nejdřív přečíst a porozumět dokumentaci k [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), protože zde uvedené taky platí. Měli byste si také přečíst kapitolu 6 *odkazu OLE DB programátora* o nastavení dat.

`IRowsetUpdateImpl` implementuje rozhraní OLE DB `IRowsetUpdate`, které umožňuje uživatelům zpozdit přenos změn provedených v `IRowsetChange` ke zdroji dat a vrátit zpět změny před přenosem.

> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si před pokusem o implementaci poskytovatele přečetli následující dokumentaci:

- [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)

- Kapitola 6 *referenčních informací programátora OLE DB*

- Podívejte se také, jak se třída `RUpdateRowset` používá v ukázce [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="setdata"></a>IRowsetUpdateImpl:: SetData

Nastaví hodnoty dat v jednom nebo více sloupcích.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Tato metoda přepisuje metodu [IRowsetChangeImpl:: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) , ale zahrnuje ukládání původních dat do mezipaměti, aby bylo možné povolit okamžité nebo odložené zpracování operace.

## <a name="getoriginaldata"></a>IRowsetUpdateImpl:: GetOriginalData

Načte data, která se na zdroj dat naposled přenáší nebo získají, a ignoruje probíhající změny.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetUpdate:: GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="getpendingrows"></a>IRowsetUpdateImpl:: GetPendingRows

Vrátí seznam řádků s nedokončenými změnami.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
pro Odpovídá parametru *hChapter* v [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="getrowstatus"></a>IRowsetUpdateImpl:: GetRowStatus

Vrátí stav zadaných řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
pro Odpovídá parametru *hChapter* v [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="undo"></a>IRowsetUpdateImpl:: Undo

Vrátí na řádku od posledního načtení nebo aktualizace změny.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
pro Odpovídá parametru *hChapter* v [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
mimo Odpovídá parametru *pcRows* v [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
pro Odpovídá parametru *prgRows* v [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="update"></a>IRowsetUpdateImpl:: Update

Přenese všechny změny provedené na řádku od posledního načtení nebo aktualizace.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
pro Odpovídá parametru *hChapter* v [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) in *OLE DB Programmer 's Reference*.

### <a name="remarks"></a>Poznámky

Změny se odesílají voláním [IRowsetChangeImpl:: FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Aby se změny projevily, musí příjemce zavolat [CRowset:: Update](../../data/oledb/crowset-update.md) . Nastavte *prgRowStatus* na odpovídající hodnotu, jak je popsáno v části [stavy řádků](/previous-versions/windows/desktop/ms722752(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="isupdateallowed"></a>IRowsetUpdateImpl:: IsUpdateAllowed

Před aktualizacemi popište tuto metodu, aby kontrolovala zabezpečení, integritu a tak dále.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parametry

*stav*<br/>
pro Stav nevyřízených operací na řádcích.

*hRowUpdate*<br/>
pro Zpracujte řádky, které chce uživatel aktualizovat.

*pRowStatus*<br/>
mimo Stav vrácený uživateli

### <a name="remarks"></a>Poznámky

Pokud určíte, že by měla být aktualizace povolená, vrátí S_OK; v opačném případě vrátí E_FAIL. Pokud povolíte aktualizaci, musíte také nastavit `DBROWSTATUS` v [IRowsetUpdateImpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) na příslušný [stav řádku](/previous-versions/windows/desktop/ms722752(v=vs.85)).

## <a name="mapcacheddata"></a>IRowsetUpdateImpl:: m_mapCachedData

Mapa obsahující původní data pro odloženou operaci.

### <a name="syntax"></a>Syntaxe

```cpp
CAtlMap<
   HROW hRow, 
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Parametry

*hRow*<br/>
Zpracujte řádky dat.

*pData*<br/>
Ukazatel na data, která mají být ukládána do mezipaměti. Data jsou typu *úložiště* (třída záznamu uživatele). Podívejte se na argument šablony *úložiště* ve [třídě IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)