---
title: Třída CComQIPtr
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327421"
---
# <a name="ccomqiptr-class"></a>Třída CComQIPtr

Inteligentní třída ukazatele pro správu ukazatelů rozhraní COM.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní COM určující typ ukazatele, který má být uložen.

*piid*<br/>
Ukazatel na IID *T*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CComQIPtr::operátor =](#operator_eq)|Přiřadí ukazatel k ukazateli člena.|

## <a name="remarks"></a>Poznámky

ATL `CComQIPtr` používá a [CComPtr](../../atl/reference/ccomptr-class.md) pro správu ukazatelů rozhraní COM, které jsou odvozeny z [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Obě třídy provádějí automatické `AddRef` počítání `Release`odkazů prostřednictvím volání a . Přetížené operátory zpracovávají operace ukazatele.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr řekl:](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr::CComQIPtr

Konstruktor

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Slouží k inicializaci ukazatele rozhraní.

*T*<br/>
Rozhraní COM.

*piid*<br/>
Ukazatel na IID *T*.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::operátor =

Operátor přiřazení.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Slouží k inicializaci ukazatele rozhraní.

*T*<br/>
Rozhraní COM.

*piid*<br/>
Ukazatel na IID *T*.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `CComQIPtr` aktualizovaný objekt.

## <a name="see-also"></a>Viz také

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[Třída CComPtrBase](../../atl/reference/ccomptrbase-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)
