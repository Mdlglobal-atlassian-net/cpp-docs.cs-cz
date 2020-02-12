---
title: CComPtr – třída
description: Referenční příručka ke třídě ATL C++ (Microsoft Active Template Library) CComPtr.
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127402"
---
# <a name="ccomptr-class"></a>CComPtr – třída

Třída inteligentního ukazatele pro správu ukazatelů rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Rozhraní COM určující typ ukazatele, který má být uložen.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComPtr:: CComPtr](#ccomptr)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CComPtr:: operator =](#operator_eq)|Přiřadí ukazatel na ukazatel na člen.|

## <a name="remarks"></a>Poznámky

Knihovna ATL používá ke správě ukazatelů rozhraní modelu COM `CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) . Obě jsou odvozeny z [CComPtrBase](../../atl/reference/ccomptrbase-class.md)a obě dělají automatické počítání odkazů.

Třídy `CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) můžou zabránit nevracení paměti tím, že provádí automatické počítání odkazů.  Následující funkce oba dělají stejné logické operace. Druhá verze však může být méně náchylná k chybám, protože používá třídu `CComPtr`:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

V sestavení ladění, propojte knihovny Atlsd. lib pro trasování kódu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="ccomptr"></a>CComPtr:: CComPtr

Konstruktor

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parametry

*úloh*<br/>
Slouží k inicializaci ukazatele rozhraní.

*Š*<br/>
Rozhraní modelu COM.

### <a name="remarks"></a>Poznámky

Konstruktory, které přijímají volání argumentu `AddRef` na *LP*, pokud se nejedná o ukazatel s hodnotou null. Vlastní objekt, který není null, získá `Release` volání na zničení objektu CComPtr, nebo pokud je nový objekt přiřazen objektu CComPtr.

## <a name="operator_eq"></a>CComPtr:: operator =

Operátor přiřazení

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na aktualizovaný objekt `CComPtr`.

### <a name="remarks"></a>Poznámky

Tato operace AddRefs nový objekt a uvolní existující objekt, pokud existuje.

## <a name="see-also"></a>Viz také

[CComPtr:: CComPtr](#ccomptr)<br/>
[CComQIPtr:: CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
