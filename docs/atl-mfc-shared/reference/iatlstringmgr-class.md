---
title: IAtlStringMgr – třída
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: 49ef7850edb18cd51092f282644973376abd4c7c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317485"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr – třída

Tato třída představuje rozhraní `CStringT` správce paměti.

## <a name="syntax"></a>Syntaxe

```
__interface IAtlStringMgr
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Přidělit](#allocate)|Volání této metody přidělit novou strukturu dat řetězce.|
|[Klonování](#clone)|Volání této metody vrátit ukazatel na nový správce řetězců `CSimpleStringT`pro použití s jinou instanci .|
|[Zdarma](#free)|Volání této metody k uvolnění struktury dat řetězce.|
|[Řetězec GetNilString](#getnilstring)|Vrátí ukazatel na `CStringData` objekt používaný prázdnými řetězcovými objekty.|
|[Přerozdělit](#reallocate)|Volání této metody přerozdělit strukturu dat řetězce.|

## <a name="remarks"></a>Poznámky

Toto rozhraní spravuje paměť používanou třídami řetězců nezávislých na knihovně MFC. například [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)a [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Tuto třídu můžete také použít k implementaci vlastního správce paměti pro vlastní třídu řetězce. Další informace naleznete v [tématu Memory Management a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::Přidělit

Přiděluje novou strukturu dat řetězce.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*nDélka alloc*<br/>
Počet znaků v novém bloku paměti.

*nVelikost*<br/>
Velikost (v bajtů) typu znaku používaného správcem řetězců.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na nově přidělený blok paměti.

> [!NOTE]
> Nesignalizujte neúspěšné přidělení vyvoláním výjimky. Místo toho by mělo být signalizováno neúspěšné přidělení vrácením hodnoty NULL.

### <a name="remarks"></a>Poznámky

Volání [IAtlStringMgr::Free](#free) nebo [IAtlStringMgr::ReAllocate](#reallocate) uvolnit paměť přidělené touto metodou.

> [!NOTE]
> Příklady použití naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr::Klonování

Vrátí ukazatel na nový správce řetězců pro `CSimpleStringT`použití s jinou instanci aplikace .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii `IAtlStringMgr` objektu.

### <a name="remarks"></a>Poznámky

Běžně volána v rámci při správce řetězce je potřeba pro nový řetězec. Ve většině případů je vrácena **tento** ukazatel.

Pokud však správce paměti nepodporuje použití více `CSimpleStringT`instancemi aplikace , měl by být vrácen ukazatel na správce sharable string.

> [!NOTE]
> Příklady použití naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr::Zdarma

Uvolní strukturu dat řetězce.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Ukazatel na blok paměti, který má být uvolněn.

### <a name="remarks"></a>Poznámky

Uvolní zadaný blok paměti dříve přidělené [přidělit](#allocate) nebo [přerozdělit](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
> Příklady použití naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

Vrátí ukazatel na strukturu dat řetězce pro prázdný řetězec.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CStringData` objekt, který slouží k reprezentaci prázdného řetězce.

### <a name="remarks"></a>Poznámky

Volání této funkce vrátit reprezentaci prázdný řetězec.

> [!NOTE]
> Při implementaci správce vlastní řetězec, tato funkce nesmí nikdy selhat. Můžete to zajistit vložením instance `CNilStringData` do třídy string manager a vrátit ukazatel na tuto instanci.

> [!NOTE]
> Příklady použití naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr::Přerozdělit

Přerozdělí strukturu dat řetězce.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Ukazatel na paměť dříve přidělenou tímto správcem paměti.

*nDélka alloc*<br/>
Počet znaků v novém bloku paměti.

*nVelikost*<br/>
Velikost (v bajtů) typu znaku používaného správcem řetězců.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek bloku nově přidělené paměti.

### <a name="remarks"></a>Poznámky

Voláním této funkce změníte velikost existujícího bloku paměti určeného *společností pData*.

Volání [IAtlStringMgr::Free](#free) uvolnit paměť přidělenou touto metodou.

> [!NOTE]
> Příklady použití naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
