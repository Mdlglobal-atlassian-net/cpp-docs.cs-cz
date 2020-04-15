---
title: Třída CComPtr
description: Referenční příručka ke třídě CComPtr (Microsoft C++ Active Template Library).
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327529"
---
# <a name="ccomptr-class"></a>Třída CComPtr

Inteligentní třída ukazatele pro správu ukazatelů rozhraní COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní COM určující typ ukazatele, který má být uložen.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CComPtr::operátor =](#operator_eq)|Přiřadí ukazatel k ukazateli člena.|

## <a name="remarks"></a>Poznámky

Knihovna `CComPtr` ATL používá a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) ke správě ukazatelů rozhraní COM. Oba jsou odvozeny z [CComPtrBase](../../atl/reference/ccomptrbase-class.md)a oba provést automatické počítání odkazů.

Třídy `CComPtr` [CComQIPtr](../../atl/reference/ccomqiptr-class.md) mohou pomoci eliminovat nevracení paměti prováděním automatického počítání odkazů.  Následující funkce obou provést stejné logické operace. Druhá verze však může být méně náchylné k `CComPtr` chybám, protože používá třídu:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

V sestaveních ladění odkaz na soubor atlsd.lib pro trasování kódu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr

Konstruktor

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Slouží k inicializaci ukazatele rozhraní.

*T*<br/>
Rozhraní COM.

### <a name="remarks"></a>Poznámky

Konstruktory, které přijmout `AddRef` volání argument *na lp*, pokud není ukazatel null. Objekt, který není ve `Release` vlastnictví null, zavolá při zničení objektu CComPtr nebo pokud je objektu CComPtr přiřazen nový objekt.

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::operátor =

Operátor přiřazení.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `CComPtr` aktualizovaný objekt.

### <a name="remarks"></a>Poznámky

Tato operace AddRefs nový objekt a uvolní existující objekt, pokud existuje.

## <a name="see-also"></a>Viz také

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
