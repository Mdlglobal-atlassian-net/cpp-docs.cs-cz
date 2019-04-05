---
title: IRowsetUpdateImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
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
- GetRowStatus
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
ms.openlocfilehash: 6c20698e2219cf7c3e1d840e23b5f8113947ae9f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037709"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl – třída

Šablony technologie OLE DB provádění [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) rozhraní.

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

*T*<br/>
Třída odvozená z `IRowsetUpdateImpl`.

*Úložiště*<br/>
Záznam uživatele.

*UpdateArray*<br/>
Pole obsahující data uložená v mezipaměti pro aktualizaci v sadě řádků.

*RowClass*<br/>
Jednotka pro ukládání `HROW`.

*MapClass*<br/>
Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)

|||
|-|-|
|[SetData](#setdata)|Nastaví hodnoty dat v jedné nebo více sloupců.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Metody rozhraní (používá se s IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Získá data naposledy předány nebo získané ze zdroje dat, ignoruje se čekající změny.|
|[GetPendingRows](#getpendingrows)|Vrátí seznam hodnot řádků s čekajícími změnami.|
|[GetRowStatus](#getrowstatus)|Vrátí stav zadaných řádků.|
|[Vrácení zpět](#undo)|Zruší všechny změny řádku od posledního načtení nebo aktualizace.|
|[Aktualizace](#update)|Odesílá všechny změny provedené od posledního načtení nebo aktualizace řádku.|

### <a name="implementation-methods-callback"></a>Implementace metody (zpětného volání)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Používá se ke kontrole integrity, zabezpečení a tak dále předtím, než aktualizace.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Obsahuje původní data pro odložené operaci.|

## <a name="remarks"></a>Poznámky

Nejprve byste si a porozuměli jim v dokumentaci k [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), protože všechno, co je popsáno zde platí i zde. Doporučujeme přečíst kapitola 6 *OLE DB referenční informace pro programátory* o nastavení data.

`IRowsetUpdateImpl` implementuje rozhraní OLE DB `IRowsetUpdate` rozhraní, která umožňuje uživatelům zpoždění přenosu změn provedených s `IRowsetChange` do zdroje dat a vrátit zpět změny před samotným přenosem.

> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si přečetli následující dokumentace před pokusem o implementaci poskytovatele:

- [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)

- Kapitola 6 *odkaz programátora technologie OLE DB*

- Také naleznete v tématu Jak `RUpdateRowset` třída se používá [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku

## <a name="setdata"></a> IRowsetUpdateImpl::SetData

Nastaví hodnoty dat v jedné nebo více sloupců.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Přepíše tuto metodu [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) metoda ale zahrnuje ukládání do mezipaměti původní data tak, aby povolovala okamžité nebo odložené zpracování operace.

## <a name="getoriginaldata"></a> IRowsetUpdateImpl::GetOriginalData

Získá data naposledy předány nebo získané ze zdroje dat, ignoruje se čekající změny.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) v *referenční informace pro OLE DB programátory*.

## <a name="getpendingrows"></a> IRowsetUpdateImpl::GetPendingRows

Vrátí seznam hodnot řádků s čekajícími změnami.

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
[in] Odpovídá *hChapter* parametr [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Další parametry, naleznete v tématu [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) v *OLE DB referenční informace pro programátory*.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) v *OLE DB referenční informace pro programátory*.

## <a name="getrowstatus"></a> IRowsetUpdateImpl::GetRowStatus

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
[in] Odpovídá *hChapter* parametr [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Další parametry, naleznete v tématu [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) v *OLE DB referenční informace pro programátory*.

## <a name="undo"></a> IRowsetUpdateImpl::Undo

Zruší všechny změny řádku od posledního načtení nebo aktualizace.

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
[in] Odpovídá *hChapter* parametr [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
[out] Odpovídá *pcRows* parametr [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[in] Odpovídá *prgRows* parametr [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Další parametry, naleznete v tématu [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) v *OLE DB referenční informace pro programátory*.

## <a name="update"></a> IRowsetUpdateImpl::Update

Odesílá všechny změny provedené od posledního načtení nebo aktualizace řádku.

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
[in] Odpovídá *hChapter* parametr [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Další parametry, naleznete v tématu [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) v *OLE DB referenční informace pro programátory*.

### <a name="remarks"></a>Poznámky

Změny se přenáší pomocí volání [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Spotřebitel musí volat [CRowset::Update](../../data/oledb/crowset-update.md) se změny projevily. Nastavte *prgRowstatus* na odpovídající hodnotu jak je popsáno v [stavy řádků](/previous-versions/windows/desktop/ms722752(v=vs.85)) v *OLE DB referenční informace pro programátory*.

## <a name="isupdateallowed"></a> IRowsetUpdateImpl::IsUpdateAllowed

Potlačí tuto metodu ke kontrole integrity a tak dále před aktualizací zabezpečení.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parametry

*stav*<br/>
[in] Stav čekající operace na řádky.

*hRowUpdate*<br/>
[in] Popisovač pro řádky, které chce uživatel aktualizovat.

*pRowStatus*<br/>
[out] Vrátí stav pro uživatele.

### <a name="remarks"></a>Poznámky

Pokud zjistíte, že má být povolený aktualizace, vrátí hodnotu S_OK; v opačném případě vrátí E_FAIL. Pokud povolíte aktualizaci, musíte také nastavit `DBROWSTATUS` v [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) na odpovídající [řádek stavu](/previous-versions/windows/desktop/ms722752(v=vs.85)).

## <a name="mapcacheddata"></a> IRowsetUpdateImpl::m_mapCachedData

Mapa obsahuje původní data pro odložené operaci.

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
Popisovač řádků pro data.

*pData*<br/>
Ukazatel na data ukládat do mezipaměti. Data jsou typu *úložiště* (třída uživatelského záznamu). Zobrazit *úložiště* argumentem šablony [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)