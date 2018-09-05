---
title: CComQIPtr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d4437d06a7308505c2338f37deea1126fcb0605
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752906"
---
# <a name="ccomqiptr-class"></a>CComQIPtr – třída

Třída inteligentní ukazatel pro správu ukazatele rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parametry

*T*  
Rozhraní modelu COM zadání typu ukazatel na Uložit.

*piid*  
Ukazatel na IID *T*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|Přiřadí ukazatel na ukazatel člen.|

## <a name="remarks"></a>Poznámky

ATL – používá `CComQIPtr` a [CComPtr](../../atl/reference/ccomptr-class.md) ke správě ukazatele rozhraní modelu COM, které jsou odvozeny z [ccomptrbase –](../../atl/reference/ccomptrbase-class.md). Obě třídy provést automatické pomocí volání pro počítání odkazů `AddRef` a `Release`. Přetížené operátory zpracování operací ukazatele.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

Konstruktor

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parametry

*LP*  
Použít k inicializaci ukazatele rozhraní.

*T*  
Rozhraní modelu COM.

*piid*  
Ukazatel na IID *T*.

##  <a name="operator_eq"></a>  CComQIPtr::operator =

Operátor přiřazení.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parametry

*LP*  
Použít k inicializaci ukazatele rozhraní.

*T*  
Rozhraní modelu COM.

*piid*  
Ukazatel na IID *T*.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na aktualizovaný `CComQIPtr` objektu.

## <a name="see-also"></a>Viz také

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
[CComQIPtr::CComQIPtr](#ccomqiptr)   
[Ccomptrbase – třída](../../atl/reference/ccomptrbase-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[CComQIPtrElementTraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)
