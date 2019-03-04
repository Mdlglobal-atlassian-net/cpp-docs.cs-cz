---
title: CPtrArray Class
ms.date: 11/04/2016
f1_keywords:
- CPtrArray
- AFXCOLL/CPtrArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: c23b87a3-bf84-49d6-a66b-61e999d0938a
ms.openlocfilehash: 59ecf01b81c4150e2bdae3b6d2862c1b3e91152b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281717"
---
# <a name="cptrarray-class"></a>CPtrArray Class

Podporuje pole ukazatelů typu void.

## <a name="syntax"></a>Syntaxe

```
class CPtrArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CPtrArray` jsou podobné jako u členských funkcí třídy [cobarray –](../../mfc/reference/cobarray-class.md). Z důvodu podobnosti, můžete použít `CObArray` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení `CObject` ukazatele jako parametr funkce nebo návratová hodnota, nahraďte ukazatel na **void**.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`void* CPtrArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole. v případě potřeby se zvětší pole.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli; v případě potřeby se zvětší pole.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje jiného objektu array do pole. v případě potřeby se zvětší pole.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel na prvek v poli.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní všechny nevyužité paměti nad aktuální horní mez.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu na daném indexu.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet elementů v tomto poli.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být `NULL`.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet elementů v tomto poli.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere element na konkrétní indexu.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby se zvětší pole.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsažena v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObArray::operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CPtrArray` zahrnuje IMPLEMENT_DYNAMIC – makro pro podporu přístupu typu modulu runtime a k vypsání `CDumpContext` objektu. Pokud potřebujete výpisu ukazatel jednotlivé prvky pole, musíte nastavit hloubky kontextu výpisu stavu systému na 1 nebo větší.

> [!NOTE]
>  Před použitím pole, použijte `SetSize` vytvoření jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidání prvků pole způsobí, že ho bude často nevyčerpané a zkopírovat. Časté realokace a kopírování jsou neefektivní a může fragmentovat paměti.

Pole ukazatelů nejde serializovat.

Při odstraňování ukazatel pole nebo jeho prvky jsou odebrány, odeberou se jenom ukazatele, nikoli entity, které odkazují.

Další informace o používání `CPtrArray`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)
