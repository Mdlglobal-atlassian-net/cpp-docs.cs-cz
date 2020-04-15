---
title: Třída CComObjectGlobal
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327623"
---
# <a name="ccomobjectglobal-class"></a>Třída CComObjectGlobal

Tato třída spravuje počet odkazů na modul `Base` obsahující objekt.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jakéhokoli jiného rozhraní, které chcete podporovat na objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Konstruktor|
|[CComObjectGlobal::~CComObjectGlobal](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComObjectGlobal::Addref](#addref)|Implementuje `AddRef`globální .|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementuje `QueryInterface`globální .|
|[CComObjectGlobal::Vydání](#release)|Implementuje `Release`globální .|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Obsahuje HRESULT vrácené během `CComObjectGlobal` konstrukce objektu.|

## <a name="remarks"></a>Poznámky

`CComObjectGlobal`spravuje referenční počet na modul obsahující `Base` váš objekt. `CComObjectGlobal`zajišťuje, že váš objekt nebude odstraněn, pokud modul nebude uvolněn. Objekt bude odebrán pouze v případě, že počet odkazů na celý modul přejde na nulu.

Například pomocí `CComObjectGlobal`objektu třídy může být objekt třídy obsahovat společný globální objekt, který je sdílen všemi jeho klienty.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::Addref

Zintáží počet odkazů objektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Ve výchozím `AddRef` `_Module::Lock`nastavení `_Module` volání , kde je globální instance [CComModule](../../atl/reference/ccommodule-class.md) nebo třídy odvozené z něj.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal

Konstruktor Volá `FinalConstruct` a potom nastaví `FinalConstruct` [m_hResFinalConstruct](#m_hresfinalconstruct) na vrácené `HRESULT` .

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Poznámky

Pokud jste neodvodili základní třídu z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), musíte zadat vlastní `FinalConstruct` metodu. Destruktor `FinalRelease`volá .

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObjectGlobal::~CComObjectGlobal

Destruktor.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct

Obsahuje HRESULT z `FinalConstruct` volání během `CComObjectGlobal` konstrukce objektu.

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObjectGlobal::QueryInterface

Načte ukazatel na požadovaný ukazatel rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní identifikovaný iid nebo NULL, pokud rozhraní není nalezeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`QueryInterface`zpracovává pouze rozhraní v tabulce mapy COM.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObjectGlobal::Vydání

Sníží počet odkazů objektu o 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění `Release` vrátí hodnotu, která může být užitečná pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí 0.

### <a name="remarks"></a>Poznámky

Ve výchozím `Release` `_Module::Unlock`nastavení `_Module` volání , kde je globální instance [CComModule](../../atl/reference/ccommodule-class.md) nebo třídy odvozené z něj.

## <a name="see-also"></a>Viz také

[Třída CComObjectStack](../../atl/reference/ccomobjectstack-class.md)<br/>
[Třída CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Třída CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
