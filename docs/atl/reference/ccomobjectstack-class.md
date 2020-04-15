---
title: Třída CComObjectStack
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327577"
---
# <a name="ccomobjectstack-class"></a>Třída CComObjectStack

Tato třída vytvoří dočasný objekt COM a poskytuje `IUnknown`mu kosterní implementaci .

## <a name="syntax"></a>Syntaxe

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jakéhokoli jiného rozhraní, které chcete podporovat na objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Konstruktor|
|[CComObjectStack::~CComObjectStack](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComObjectStack::Addref](#addref)|Vrátí nula. V režimu ladění `_ASSERTE`volání .|
|[CComObjectStack::QueryInterface](#queryinterface)|Vrátí E_NOINTERFACE. V režimu ladění `_ASSERTE`volání .|
|[CComObjectStack::Vydání](#release)|Vrátí nula. V režimu ladění `_ASSERTE`volání . ~|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Obsahuje HRESULT vrácené během `CComObjectStack` konstrukce objektu.|

## <a name="remarks"></a>Poznámky

`CComObjectStack`slouží k vytvoření dočasného objektu COM a `IUnknown`poskytnutí objektu kosterní implementaci . Objekt se obvykle používá jako místní proměnná v rámci jedné funkce (to znamená, že je posunuta do zásobníku). Vzhledem k tomu, že objekt je zničen po dokončení funkce, počítání odkazů se neprovádí ke zvýšení efektivity.

Následující příklad ukazuje, jak vytvořit objekt COM použitý uvnitř funkce:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

Dočasný objekt `Tempobj` je posunut do zásobníku a automaticky zmizí po dokončení funkce.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObjectStack`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::Addref

Vrátí nula.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nula.

### <a name="remarks"></a>Poznámky

V režimu ladění `_ASSERTE`volání .

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack

Konstruktor

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Poznámky

Volá `FinalConstruct` a potom nastaví [m_hResFinalConstruct](#m_hresfinalconstruct) `FinalConstruct`hresult vrácené . Pokud jste neodvodili základní třídu z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), musíte zadat vlastní `FinalConstruct` metodu. Destruktor `FinalRelease`volá .

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObjectStack::~CComObjectStack

Destruktor.

```
CComObjectStack();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct

Obsahuje HRESULT vrácené `FinalConstruct` z volání `CComObjectStack` během konstrukce objektu.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::QueryInterface

Vrátí E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOINTERFACE.

### <a name="remarks"></a>Poznámky

V režimu ladění `_ASSERTE`volání .

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::Vydání

Vrátí nula.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nula.

### <a name="remarks"></a>Poznámky

V režimu ladění `_ASSERTE`volání .

## <a name="see-also"></a>Viz také

[Třída CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Třída CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Třída CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
