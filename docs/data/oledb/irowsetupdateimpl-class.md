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
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370750"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl – třída

Ole DB šablony implementace rozhraní [IRowsetUpdate.](/previous-versions/windows/desktop/ms714401(v=vs.85))

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
Třída odvozená `IRowsetUpdateImpl`z .

*Storage*<br/>
Záznam uživatele.

*Pole UpdateArray*<br/>
Pole obsahující data uložená v mezipaměti pro aktualizaci sady řádků.

*Třída řádku*<br/>
Skladovací jednotka pro `HROW`.

*Třída Mapy*<br/>
Úložná jednotka pro všechny popisovače řádků držené zprostředkovatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)

|||
|-|-|
|[Setdata](#setdata)|Nastaví hodnoty dat v jednom nebo více sloupcích.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Metody rozhraní (používá se s IRowsetUpdate)

|||
|-|-|
|[Získat původní data](#getoriginaldata)|Získá data naposledy přenášena nebo získané ze zdroje dat, ignoruje čekající změny.|
|[GetPendingRows](#getpendingrows)|Vrátí seznam řádků s čekajícími změnami.|
|[GetRowStatus](#getrowstatus)|Vrátí stav zadaných řádků.|
|[Zpět](#undo)|Od posledního načtení nebo aktualizace se v řádku neodevzpisnou všechny změny.|
|[Aktualizace](#update)|Přenáší všechny změny provedené v řádku od posledního načtení nebo aktualizace.|

### <a name="implementation-methods-callback"></a>Metody implementace (zpětné volání)

|||
|-|-|
|[Je aktualizace povolena.](#isupdateallowed)|Slouží ke kontrole zabezpečení, integrity a tak dále před povolením aktualizací.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Obsahuje původní data pro odložené operace.|

## <a name="remarks"></a>Poznámky

Měli byste si nejprve přečíst a pochopit dokumentaci pro [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), protože vše, co je zde popsáno, platí i zde. Měli byste si také přečíst kapitolu 6 *ole db programmer odkaz* na nastavení dat.

`IRowsetUpdateImpl`implementuje rozhraní `IRowsetUpdate` OLE DB, které umožňuje spotřebitelům `IRowsetChange` zpozdit přenos změn provedených se zdrojem dat a vrátit zpět změny před přenosem.

> [!IMPORTANT]
> Důrazně doporučujeme, abyste si před pokusem o implementaci zprostředkovatele přečetli následující dokumentaci:

- [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)

- Kapitola 6 *referenční příručky programátora OLE DB*

- Také zobrazit, `RUpdateRowset` jak se používá třída v [updatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl::SetData

Nastaví hodnoty dat v jednom nebo více sloupcích.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) v *odkazu programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše [metodu IRowsetChangeImpl::SetData,](../../data/oledb/irowsetchangeimpl-setdata.md) ale zahrnuje ukládání původních dat do mezipaměti, aby bylo možné okamžité nebo odložené zpracování operace.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData

Získá data naposledy přenášena nebo získané ze zdroje dat, ignoruje čekající změny.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parametry

Viz [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl::GetPendingRows

Vrátí seznam řádků s čekajícími změnami.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>Parametry

*hVyhrazeno*<br/>
[v] Odpovídá parametru *hChapter* v [iRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) v *odkazu programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl::GetRowStatus

Vrátí stav zadaných řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parametry

*hVyhrazeno*<br/>
[v] Odpovídá parametru *hChapter* v [iRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl::Vrátit

Od posledního načtení nebo aktualizace se v řádku neodevzpisnou všechny změny.

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

*hVyhrazeno*<br/>
[v] Odpovídá parametru *hChapter* v [iRowsetUpdate::Redo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
[out] Odpovídá parametru *pcRows* v [iRowsetUpdate::Redo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[v] Odpovídá *parametru prgRows* v [iRowsetUpdate::Redo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate::Redo](/previous-versions/windows/desktop/ms719655(v=vs.85)) v *odkazu programátora OLE DB*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl::Aktualizovat

Přenáší všechny změny provedené v řádku od posledního načtení nebo aktualizace.

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

*hVyhrazeno*<br/>
[v] Odpovídá parametru *hChapter* v [iRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Další parametry naleznete v tématu [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) in the *OLE DB Programmer's Reference*.

### <a name="remarks"></a>Poznámky

Změny jsou přenášeny voláním [iRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). Příjemce musí volat [CRowset::Update](../../data/oledb/crowset-update.md) pro změny se projeví. Nastavte *stav prgRowstatus* na příslušnou hodnotu, jak je popsáno v [stavech řádků](/previous-versions/windows/desktop/ms722752(v=vs.85)) v odkazu *programátora OLE DB*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed

Přepište tuto metodu a zkontrolujte zabezpečení, integritu a tak dále před aktualizací.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parametry

*Stav*<br/>
[v] Stav čekající operace na řádcích.

*hRowUpdate*<br/>
[v] Popisovač pro řádky, které chce uživatel aktualizovat.

*pRowStatus*<br/>
[out] Stav vrácený uživateli.

### <a name="remarks"></a>Poznámky

Pokud zjistíte, že aktualizace by měla být povolena, vrátí S_OK; jinak vrátí E_FAIL. Pokud povolíte aktualizaci, musíte také `DBROWSTATUS` nastavit v [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) do příslušného [stavu řádku](/previous-versions/windows/desktop/ms722752(v=vs.85)).

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData

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

*hŘádek*<br/>
Zpracovat řádky pro data.

*Pdata*<br/>
Ukazatel na data, která mají být uložena do mezipaměti. Data jsou typu *Storage* (třída záznamu uživatele). Viz argument šablony *úložiště* ve [třídě IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatelů OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)
