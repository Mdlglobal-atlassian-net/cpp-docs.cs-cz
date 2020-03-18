---
title: CPtrArray – třída
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
ms.openlocfilehash: 3167c6a388ecbfefce9a72b7bfd720f83639108a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444283"
---
# <a name="cptrarray-class"></a>CPtrArray – třída

Podporuje pole ukazatelů typu void.

## <a name="syntax"></a>Syntaxe

```
class CPtrArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CPtrArray` jsou podobné členským funkcím třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CObArray` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte ukazatel na **void**.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`void* CPtrArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPtrArray::CPtrArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPtrArray:: Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CPtrArray:: Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CPtrArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CPtrArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel elementu v rámci pole.|
|[CPtrArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CPtrArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CPtrArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CPtrArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Lze `NULL`.|
|[CPtrArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CPtrArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CPtrArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CPtrArray::-Empty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CPtrArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CPtrArray:: funkce RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v konkrétním indexu.|
|[CPtrArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CPtrArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CPtrArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CPtrArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CPtrArray` zahrnuje makro IMPLEMENT_DYNAMIC pro podporu přístupu k běhovým typům a výpisu do objektu `CDumpContext`. Pokud potřebujete výpis paměti jednotlivých prvků pole ukazatelů, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

> [!NOTE]
>  Před použitím pole použijte `SetSize` k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Pole ukazatelů nelze serializovat.

Když je odstraněno pole ukazatele nebo když jsou jeho prvky odebrány, jsou odebrány pouze ukazatele, nikoli entity, na které odkazují.

Další informace o používání `CPtrArray`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)
