---
title: CUIntArray – třída
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CUIntArray::CUIntArray
- AFXCOLL/CUIntArray::Add
- AFXCOLL/CUIntArray::Append
- AFXCOLL/CUIntArray::Copy
- AFXCOLL/CUIntArray::ElementAt
- AFXCOLL/CUIntArray::FreeExtra
- AFXCOLL/CUIntArray::GetAt
- AFXCOLL/CUIntArray::GetCount
- AFXCOLL/CUIntArray::GetData
- AFXCOLL/CUIntArray::GetSize
- AFXCOLL/CUIntArray::GetUpperBound
- AFXCOLL/CUIntArray::InsertAt
- AFXCOLL/CUIntArray::IsEmpty
- AFXCOLL/CUIntArray::RemoveAll
- AFXCOLL/CUIntArray::RemoveAt
- AFXCOLL/CUIntArray::SetAt
- AFXCOLL/CUIntArray::SetAtGrow
- AFXCOLL/CUIntArray::SetSize
helpviewer_keywords:
- CUIntArray [MFC], CUIntArray
- CUIntArray [MFC], Add
- CUIntArray [MFC], Append
- CUIntArray [MFC], Copy
- CUIntArray [MFC], ElementAt
- CUIntArray [MFC], FreeExtra
- CUIntArray [MFC], GetAt
- CUIntArray [MFC], GetCount
- CUIntArray [MFC], GetData
- CUIntArray [MFC], GetSize
- CUIntArray [MFC], GetUpperBound
- CUIntArray [MFC], InsertAt
- CUIntArray [MFC], IsEmpty
- CUIntArray [MFC], RemoveAll
- CUIntArray [MFC], RemoveAt
- CUIntArray [MFC], SetAt
- CUIntArray [MFC], SetAtGrow
- CUIntArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 932062ec289a34cffcd929853233a0c7c81a7a72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447538"
---
# <a name="cuintarray-class"></a>CUIntArray – třída

Podporuje pole celých čísel bez znaménka.

## <a name="syntax"></a>Syntaxe

```
class CUIntArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CUIntArray` jsou podobné členským funkcím třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CObArray` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte UINT.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CUIntArray::CUIntArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CUIntArray:: Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CUIntArray:: Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CUIntArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CUIntArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel elementu v rámci pole.|
|[CUIntArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CUIntArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CUIntArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CUIntArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CUIntArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CUIntArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CUIntArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CUIntArray::-Empty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CUIntArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CUIntArray:: funkce RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v konkrétním indexu.|
|[CUIntArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CUIntArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CUIntArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CUIntArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

Unsigned integer, nebo UINT, se liší od slov a doubleword v tom, že fyzická velikost objektu UINT se může změnit v závislosti na cílovém operačním prostředí. Objekt UINT má stejnou velikost jako doubleword.

`CUIntArray` zahrnuje makro [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) pro podporu přístupu k běhovým typům a výpisu do [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objektu. Pokud potřebujete výpis paměti jednotlivých unsigned integer prvků, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší. Pole typu Integer bez znaménka nelze serializovat.

> [!NOTE]
>  Před použitím pole použijte `SetSize` k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Další informace o používání `CUIntArray`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
