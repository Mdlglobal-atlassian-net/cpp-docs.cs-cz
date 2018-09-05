---
title: Ccomobjectstack – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c3e29c3eed99c95ee92841413ceaca6e17e8565
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755059"
---
# <a name="ccomobjectstack-class"></a>Ccomobjectstack – třída

Tato třída se vytvoří dočasný objekt modelu COM a poskytuje základní implementaci `IUnknown`.

## <a name="syntax"></a>Syntaxe

```
template <class  Base>  
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parametry

*základ*  
Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Konstruktor|
|[Ccomobjectstack –:: ~ ccomobjectstack –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Vrátí nulu. V režimu ladění, volá `_ASSERTE`.|
|[CComObjectStack::QueryInterface](#queryinterface)|Vrátí E_NOINTERFACE. V režimu ladění, volá `_ASSERTE`.|
|[CComObjectStack::Release](#release)|Vrátí nulu. V režimu ladění, volá `_ASSERTE`. ~|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Obsahuje HRESULT vrátil během procesu vytváření `CComObjectStack` objektu.|

## <a name="remarks"></a>Poznámky

`CComObjectStack` slouží k vytvoření dočasného objektu COM a poskytnout objekt základní implementaci `IUnknown`. Objekt se obvykle používá jako místní proměnné v rámci jedné funkce, (, který se vloží do zásobníku). Protože objekt je zničen při dokončení funkce, počítání odkazů se neprovádí ke zvýšení efektivity.

Následující příklad ukazuje, jak vytvořit objekt modelu COM použít uvnitř funkce:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

Dočasný objekt `Tempobj` vloženo do zásobníku a automaticky při dokončení funkce zmizí.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObjectStack`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="addref"></a>  CComObjectStack::AddRef

Vrátí nulu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nulu.

### <a name="remarks"></a>Poznámky

V režimu ladění, volá `_ASSERTE`.

##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack

Konstruktor

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Poznámky

Volání `FinalConstruct` a pak nastaví [m_hResFinalConstruct](#m_hresfinalconstruct) HRESULT vrácený `FinalConstruct`. Pokud ještě odvozené ze základní třídy [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md), je nutné zadat vlastní `FinalConstruct` metody. Volání destruktoru `FinalRelease`.

##  <a name="dtor"></a>  Ccomobjectstack –:: ~ ccomobjectstack –

Destruktor.

```
CComObjectStack();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volání [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct

Obsahuje HRESULT vrácená z volání `FinalConstruct` během procesu vytváření `CComObjectStack` objektu.

```
HRESULT    m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface

Vrátí E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOINTERFACE.

### <a name="remarks"></a>Poznámky

V režimu ladění, volá `_ASSERTE`.

##  <a name="release"></a>  CComObjectStack::Release

Vrátí nulu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nulu.

### <a name="remarks"></a>Poznámky

V režimu ladění, volá `_ASSERTE`.

## <a name="see-also"></a>Viz také

[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
[CComObject – třída](../../atl/reference/ccomobject-class.md)   
[Ccomobjectglobal – třída](../../atl/reference/ccomobjectglobal-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
