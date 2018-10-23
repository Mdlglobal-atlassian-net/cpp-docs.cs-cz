---
title: Iatlstringmgr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d637750ab4aa9dc30ca7b297373cb2c752802d8
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808867"
---
# <a name="iatlstringmgr-class"></a>Iatlstringmgr – třída

Tato třída reprezentuje rozhraní pro `CStringT` správce paměti.

## <a name="syntax"></a>Syntaxe

```
__interface IAtlStringMgr
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[přidělení](#allocate)|Volejte tuto metodu za účelem přidělení nového datová struktura řetězec.|
|[Clone](#clone)|Volejte tuto metodu za účelem vrací ukazatel na nového správce řetězců pro použití s jinou instancí `CSimpleStringT`.|
|[Zdarma](#free)|Volejte tuto metodu pro uvolnění datová struktura řetězec.|
|[GetNilString](#getnilstring)|Vrací ukazatel `CStringData` objekt použitý objektem objekty prázdný řetězec.|
|[Přidělit jinému uživateli](#reallocate)|Volejte tuto metodu, aby mohla znovu přidělit datová struktura řetězec.|

## <a name="remarks"></a>Poznámky

Toto rozhraní spravuje paměť používanou tříd řetězců nezávislé na MFC; například [csimplestringt –](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), a [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

Tato třída také můžete implementovat vlastní paměti správce pro vaši třídu vlastního řetězce. Další informace najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

##  <a name="allocate"></a>  IAtlStringMgr::Allocate

Přidělí novou strukturu dat řetězce.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*nAllocLength*<br/>
Počet znaků v nového bloku paměti.

*nCharSize*<br/>
Velikost typ znaku, používá správce řetězců (v bajtech).

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na nově přidělenou paměť bloku.

> [!NOTE]
>  Nevydá signál neúspěšné přidělení vyvoláním výjimky. Místo toho by měl být signalizován neúspěšné přidělení vrácením hodnoty NULL.

### <a name="remarks"></a>Poznámky

Volání [IAtlStringMgr::Free](#free) nebo [IAtlStringMgr::ReAllocate](#reallocate) k uvolnění paměti přidělené touto metodou.

> [!NOTE]
>  Příklady využití naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="clone"></a>  IAtlStringMgr::Clone

Vrací ukazatel na nového správce řetězců pro použití s jinou instancí `CSimpleStringT`.

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii objektu `IAtlStringMgr` objektu.

### <a name="remarks"></a>Poznámky

Běžně volá se rozhraním, když správce řetězců je potřeba pro nový řetězec. Ve většině případů **to** je vrácen ukazatel.

Nicméně pokud správce paměti nepodporuje, která je používána ve více instancí `CSimpleStringT`, má být vrácen ukazatel na řetězec sdílet správce.

> [!NOTE]
>  Příklady využití naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="free"></a>  IAtlStringMgr::Free

Uvolní datová struktura řetězec.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Ukazatele na blok paměti určený k uvolnění.

### <a name="remarks"></a>Poznámky

Uvolní blok zadaný paměti dříve přidělený metodou [přidělení](#allocate) nebo [přidělit jinému uživateli](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
>  Příklady využití naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="getnilstring"></a>  IAtlStringMgr::GetNilString

Vrací ukazatel na strukturu dat řetězce pro prázdný řetězec.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CStringData` objekt použitý k reprezentaci prázdný řetězec.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrátí reprezentaci prázdný řetězec.

> [!NOTE]
> Při implementaci vlastní řetězec správce, musí tuto funkci nikdy selhat. Lze toho docílit s využitím vkládání služby instance `CNilStringData` správce třída string a vrácení ukazatele do této instance.

> [!NOTE]
> Příklady využití naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="reallocate"></a>  IAtlStringMgr::Reallocate

Znovu alokuje datová struktura řetězec.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

*nAllocLength*<br/>
Počet znaků v nového bloku paměti.

*nCharSize*<br/>
Velikost typ znaku, používá správce řetězců (v bajtech).

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na začátek bloku nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Voláním této funkce pro změnu velikosti existujícího blok paměti určený *pData*.

Volání [IAtlStringMgr::Free](#free) k uvolnění paměti přidělené touto metodou.

> [!NOTE]
> Příklady využití naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
