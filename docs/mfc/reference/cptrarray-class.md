---
title: Třída CPtrArray
ms.date: 11/04/2016
f1_keywords:
- CPtrArray
- AFXCOLL/CPtrArray
- AFXCOLL/CPtrArray::CPtrArray
- AFXCOLL/CPtrArray::Add
- AFXCOLL/CPtrArray::Append
- AFXCOLL/CPtrArray::Copy
- AFXCOLL/CPtrArray::ElementAt
- AFXCOLL/CPtrArray::FreeExtra
- AFXCOLL/CPtrArray::GetAt
- AFXCOLL/CPtrArray::GetCount
- AFXCOLL/CPtrArray::GetData
- AFXCOLL/CPtrArray::GetSize
- AFXCOLL/CPtrArray::GetUpperBound
- AFXCOLL/CPtrArray::InsertAt
- AFXCOLL/CPtrArray::IsEmpty
- AFXCOLL/CPtrArray::RemoveAll
- AFXCOLL/CPtrArray::RemoveAt
- AFXCOLL/CPtrArray::SetAt
- AFXCOLL/CPtrArray::SetAtGrow
- AFXCOLL/CPtrArray::SetSize
helpviewer_keywords:
- CPtrArray [MFC], CPtrArray
- CPtrArray [MFC], Add
- CPtrArray [MFC], Append
- CPtrArray [MFC], Copy
- CPtrArray [MFC], ElementAt
- CPtrArray [MFC], FreeExtra
- CPtrArray [MFC], GetAt
- CPtrArray [MFC], GetCount
- CPtrArray [MFC], GetData
- CPtrArray [MFC], GetSize
- CPtrArray [MFC], GetUpperBound
- CPtrArray [MFC], InsertAt
- CPtrArray [MFC], IsEmpty
- CPtrArray [MFC], RemoveAll
- CPtrArray [MFC], RemoveAt
- CPtrArray [MFC], SetAt
- CPtrArray [MFC], SetAtGrow
- CPtrArray [MFC], SetSize
ms.assetid: c23b87a3-bf84-49d6-a66b-61e999d0938a
ms.openlocfilehash: 7bab68fcbd2cfa4cfe44b0fcd2a1f78af886533d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363983"
---
# <a name="cptrarray-class"></a>Třída CPtrArray

Podporuje pole void ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CPtrArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CPtrArray` jsou podobné členské funkce třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete `CObArray` použít referenční dokumentaci pro specifika členské funkce. Všude tam, kde vidíte `CObject` ukazatel jako parametr funkce nebo vrácenou hodnotu, nahraďte ukazatel **void**.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například znamená, že

`void* CPtrArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPtrArray::CPtrArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPtrArray::Přidat](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CPtrArray::Připojit](../../mfc/reference/cobarray-class.md#append)|Připojí k poli jiné pole; v případě potřeby pole zvětší.|
|[CPtrArray::Kopírovat](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CPtrArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel prvku v rámci pole.|
|[CPtrArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CPtrArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CPtrArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CPtrArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může `NULL`být .|
|[CPtrArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CPtrArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CPtrArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CPtrArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CPtrArray::OdebratVše](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CPtrArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v určitém indexu.|
|[CPtrArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CPtrArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CPtrArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CPtrArray::operátor \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

`CPtrArray`obsahuje makro IMPLEMENT_DYNAMIC pro podporu přístupu typu run-time a ukládání do objektu. `CDumpContext` Pokud potřebujete výpis jednotlivých prvků pole ukazatele, musíte nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

> [!NOTE]
> Před použitím pole `SetSize` použijte k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Pole ukazatele nelze serializovat.

Při odstranění pole ukazatele nebo při odebrání jeho prvky jsou odebrány pouze ukazatele, nikoli entity, na které odkazují.

Další informace o `CPtrArray`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CObArray](../../mfc/reference/cobarray-class.md)
