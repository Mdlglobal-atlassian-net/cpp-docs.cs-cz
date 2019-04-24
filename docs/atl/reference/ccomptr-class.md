---
title: CComPtr – třída
ms.date: 11/04/2016
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 5e3e510291daa50ddcf5d63451edef0428d66ed1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259102"
---
# <a name="ccomptr-class"></a>CComPtr – třída

Třída inteligentní ukazatel pro správu ukazatele rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class CComPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní modelu COM zadání typu ukazatel na Uložit.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|Přiřadí ukazatel na ukazatel člen.|

## <a name="remarks"></a>Poznámky

ATL – používá `CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) ke správě ukazatele rozhraní modelu COM. Obě jsou odvozeny od [ccomptrbase –](../../atl/reference/ccomptrbase-class.md), a jak provádět automatické počítání odkazů.

`CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) třídy může pomoct eliminovat nevrácené paměti pomocí provádí automatické počítání odkazů.  Následující funkce obou provádět stejné logické operace; Mějte však na paměti jak druhý verze může být méně náchylný pomocí `CComPtr` třídy:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

V ladicím buildu odkaz knihovny atlsd.lib pro trasování kódu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="ccomptr"></a>  CComPtr::CComPtr

Konstruktor

```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parametry

*lp*<br/>
Použít k inicializaci ukazatele rozhraní.

*T*<br/>
Rozhraní modelu COM.

##  <a name="operator_eq"></a>  CComPtr::operator =

Operátor přiřazení.

```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na aktualizovaný `CComPtr` objektu

### <a name="remarks"></a>Poznámky

Tato operace AddRefs nový objekt a verzích existující objekt, pokud existuje.

## <a name="see-also"></a>Viz také:

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
