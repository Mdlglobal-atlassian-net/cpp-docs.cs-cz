---
title: Třída CAtlException
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: 6da56e4d6c443520eb6f857624a5923e71a1e580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318998"
---
# <a name="catlexception-class"></a>Třída CAtlException

Tato třída definuje výjimku ATL.

## <a name="syntax"></a>Syntaxe

```
class CAtlException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlException::operátor HRESULT](#operator_hresult)|Přetypovat aktuální objekt na hodnotu HRESULT.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|Proměnná typu HRESULT vytvořená objektem a použitá k uložení chybového stavu.|

## <a name="remarks"></a>Poznámky

Objekt `CAtlException` představuje podmínku výjimky související s operací knihovny ATL. Třída `CAtlException` obsahuje veřejný datový člen, který ukládá stavový kód označující důvod výjimky a operátor přetypování, který umožňuje zacházet s výjimkou, jako by se jednalo o HRESULT.

Obecně platí, že `AtlThrow` budete volat `CAtlException` spíše než vytváření objektu přímo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlexcept.h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

Konstruktor

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Kód chyby HRESULT.

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException::operátor HRESULT

Přetypovat aktuální objekt na hodnotu HRESULT.

```
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException::m_hr

Datový člen HRESULT.

```
HRESULT m_hr;
```

### <a name="remarks"></a>Poznámky

Datový člen, který ukládá chybový stav. Hodnota HRESULT je nastavena konstruktorem [CAtlException::CAtlException](#catlexception).

## <a name="see-also"></a>Viz také

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
