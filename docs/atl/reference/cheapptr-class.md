---
title: Třída CHeapPtr
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
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326918"
---
# <a name="cheapptr-class"></a>Třída CHeapPtr

Inteligentní třída ukazatele pro správu ukazatelů haldy.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, který má být uložen na haldě.

*Přidělování*<br/>
Třída přidělení paměti, která má být používána.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtr::Přidělit](#allocate)|Volání této metody přidělit paměť na haldě pro ukládání objektů.|
|[CHeapPtr::Přerozdělit](#reallocate)|Volání této metody přerozdělit paměti na haldě.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtr::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

`CHeapPtr`je odvozen z [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) a ve výchozím nastavení používá CRT rutiny (v [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) přidělit a uvolnit paměť. Třída [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) lze sestavit seznam ukazatelů haldy. Viz také [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), který používá rutiny přidělení paměti COM.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr::Přidělit

Volání této metody přidělit paměť na haldě pro ukládání objektů.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parametry

*nPrvky*<br/>
Počet prvků, které slouží k výpočtu množství paměti přidělit. Výchozí hodnota je 1.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud byla paměť úspěšně přidělena, false při selhání.

### <a name="remarks"></a>Poznámky

Alokátor rutiny se používají k rezervaci dostatek paměti na haldě pro uložení *nElement* objekty typu definovaného v konstruktoru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr::CHeapPtr

Konstruktor

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Existující ukazatel haldy nebo `CHeapPtr`.

### <a name="remarks"></a>Poznámky

Ukazatel haldy lze volitelně vytvořit pomocí existujícího ukazatele nebo objektu. `CHeapPtr` Pokud ano, `CHeapPtr` nový objekt přebírá odpovědnost za správu nového ukazatele a prostředků.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::operátor =

Operátor přiřazení.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Existující objekt `CHeapPtr`.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CHeapPtr`aktualizovaný .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr::Přerozdělit

Volání této metody přerozdělit paměti na haldě.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nPrvky*<br/>
Nový počet prvků, které slouží k výpočtu množství paměti přidělit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud byla paměť úspěšně přidělena, false při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Viz také

[Třída CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Třída CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
