---
title: CWordArray – třída
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CWordArray::CWordArray
- AFXCOLL/CWordArray::Add
- AFXCOLL/CWordArray::Append
- AFXCOLL/CWordArray::Copy
- AFXCOLL/CWordArray::ElementAt
- AFXCOLL/CWordArray::FreeExtra
- AFXCOLL/CWordArray::GetAt
- AFXCOLL/CWordArray::GetCount
- AFXCOLL/CWordArray::GetData
- AFXCOLL/CWordArray::GetSize
- AFXCOLL/CWordArray::GetUpperBound
- AFXCOLL/CWordArray::InsertAt
- AFXCOLL/CWordArray::IsEmpty
- AFXCOLL/CWordArray::RemoveAll
- AFXCOLL/CWordArray::RemoveAt
- AFXCOLL/CWordArray::SetAt
- AFXCOLL/CWordArray::SetAtGrow
- AFXCOLL/CWordArray::SetSize
helpviewer_keywords:
- CWordArray [MFC], CWordArray
- CWordArray [MFC], Add
- CWordArray [MFC], Append
- CWordArray [MFC], Copy
- CWordArray [MFC], ElementAt
- CWordArray [MFC], FreeExtra
- CWordArray [MFC], GetAt
- CWordArray [MFC], GetCount
- CWordArray [MFC], GetData
- CWordArray [MFC], GetSize
- CWordArray [MFC], GetUpperBound
- CWordArray [MFC], InsertAt
- CWordArray [MFC], IsEmpty
- CWordArray [MFC], RemoveAll
- CWordArray [MFC], RemoveAt
- CWordArray [MFC], SetAt
- CWordArray [MFC], SetAtGrow
- CWordArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: 99484071c81ed6b766d3e4259d9fc88353b27ea3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446222"
---
# <a name="cwordarray-class"></a>CWordArray – třída

Podporuje pole 16bitových slov.

## <a name="syntax"></a>Syntaxe

```
class CWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CWordArray` jsou podobné členským funkcím třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CObArray` pro konkrétní členské funkce. Všude, kde vidíte ukazatel [CObject](../../mfc/reference/cobject-class.md) jako parametr funkce nebo návratovou hodnotu, nahraďte slovo.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWordArray::CWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWordArray:: Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CWordArray:: Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CWordArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CWordArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel elementu v rámci pole.|
|[CWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CWordArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CWordArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CWordArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CWordArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CWordArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CWordArray::-Empty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CWordArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CWordArray:: funkce RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v konkrétním indexu.|
|[CWordArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CWordArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CWordArray:: operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CWordArray` zahrnuje makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) pro podporu serializace a dumpingu jeho prvků. Je-li pole slov uloženo do archivu, buď pomocí přetíženého operátoru vložení, nebo pomocí členské funkce [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize) , je každý prvek následně serializován.

> [!NOTE]
>  Před použitím pole použijte `SetSize` k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Pokud potřebujete výpis paměti jednotlivých prvků v poli, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Další informace o používání `CWordArray`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[Ukázka MFC – shromáždit](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
