---
title: Cheapptr – třída
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: 8cb35139e707d81a53edb762a2b7fc2ab41ff247
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296056"
---
# <a name="cheapptr-class"></a>Cheapptr – třída

Třída inteligentní ukazatel pro správu haldy ukazatele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu ukládaly na haldě.

*Allocator –*<br/>
Třída přidělení paměti pro použití.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|Volejte tuto metodu za účelem přidělení paměti v haldě pro uložení objektů.|
|[CHeapPtr::Reallocate](#reallocate)|Voláním této metody lze znovu přidělit paměti v haldě.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

`CHeapPtr` je odvozen z [cheapptrbase –](../../atl/reference/cheapptrbase-class.md) a ve výchozím nastavení používá rutiny CRT (v [ccrtallocator –](../../atl/reference/ccrtallocator-class.md)) k přidělují a uvolňují paměť. Třída [cheapptrlist –](../../atl/reference/cheapptrlist-class.md) slouží k vytvoření seznamu haldy ukazatelů. Viz také [ccomheapptr –](../../atl/reference/ccomheapptr-class.md), který používá COM rutiny přidělení paměti.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

Volejte tuto metodu za účelem přidělení paměti v haldě pro uložení objektů.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parametry

*nElements*<br/>
Počet prvků, které slouží k výpočtu velikosti paměti k přidělení. Výchozí hodnota je 1.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je paměť byla úspěšně přidělena false při selhání.

### <a name="remarks"></a>Poznámky

Allocator rutiny umožňují rezervovat dostatek paměti v haldě k uložení *nElement* objekty typu definovaného v konstruktoru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

Konstruktor

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Stávajícího ukazatele haldy nebo `CHeapPtr`.

### <a name="remarks"></a>Poznámky

Ukazatel na haldu lze vytvořit volitelně pomocí stávajícího ukazatele, nebo `CHeapPtr` objektu. Pokud ano, nové `CHeapPtr` objekt zodpovědnost za správu nový ukazatel a prostředky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

Operátor přiřazení.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Existující objekt `CHeapPtr`.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CHeapPtr`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

Voláním této metody lze znovu přidělit paměti v haldě.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nElements*<br/>
Nový počet prvků, které slouží k výpočtu velikosti paměti k přidělení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je paměť byla úspěšně přidělena false při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Viz také:

[CHeapPtrBase – třída](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator – třída](../../atl/reference/ccrtallocator-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
