---
title: CAtlException – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168199"
---
# <a name="catlexception-class"></a>CAtlException – třída

Tato třída definuje výjimku ATL.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAtlException:: operator HRESULT](#operator_hresult)|Přetypování aktuálního objektu na hodnotu HRESULT.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlException:: m_hr](#m_hr)|Proměnná typu HRESULT vytvořená objektem a slouží k uložení chybové podmínky.|

## <a name="remarks"></a>Poznámky

`CAtlException` Objekt představuje podmínku výjimky vztahující se k operaci ATL. `CAtlException` Třída zahrnuje veřejný datový člen, který ukládá stavový kód označující důvod výjimky a operátor přetypování, který umožňuje zacházet s výjimkou, jako by ŠLO o HRESULT.

Obecně budete volat `AtlThrow` místo přímého vytváření `CAtlException` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlexcept. h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Konstruktor

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parametry

*oddělení*<br/>
Kód chyby HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException:: operator HRESULT

Přetypování aktuálního objektu na hodnotu HRESULT.

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException:: m_hr

Datový člen HRESULT.

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>Poznámky

Datový člen, který ukládá chybový stav. Hodnota HRESULT je nastavena konstruktorem, [CAtlException:: CAtlException](#catlexception).

## <a name="see-also"></a>Viz také

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
