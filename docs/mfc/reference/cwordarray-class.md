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
ms.openlocfilehash: 9dfb0b674d52b288ebd05bf7574f1ae05e4ed1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365914"
---
# <a name="cwordarray-class"></a>CWordArray – třída

Podporuje pole 16bitových slov.

## <a name="syntax"></a>Syntaxe

```
class CWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CWordArray` jsou podobné členské funkce třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete `CObArray` použít referenční dokumentaci pro specifika členské funkce. Všude tam, kde vidíte [cobject](../../mfc/reference/cobject-class.md) ukazatel jako parametr funkce nebo vrácená hodnota, nahraďte WORD.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například znamená, že

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CWordArray::CWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWordArray::Přidat](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CWordArray::Připojit](../../mfc/reference/cobarray-class.md#append)|Připojí k poli jiné pole; v případě potřeby pole zvětší.|
|[CWordArray::Kopírovat](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CWordArray::Elementat](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel prvku v rámci pole.|
|[CWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CWordArray::Getat](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CWordArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CWordArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být NULL.|
|[CWordArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CWordArray::insertat](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CWordArray::Jeprázdný](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CWordArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CWordArray::Removeat](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v určitém indexu.|
|[CWordArray::Setat](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CWordArray::Setatgrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CWordArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CWordArray:: &#91;&#93;operátora](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

`CWordArray`obsahuje [makro IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) pro podporu serializace a dumpingu jeho prvků. Pokud pole slov je uložen do archivu, buď s přetížené vložení operátor nebo s [CObject::Serializovat](../../mfc/reference/cobject-class.md#serialize) členské funkce, každý prvek je zase serializován.

> [!NOTE]
> Před použitím pole `SetSize` použijte k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Pokud potřebujete výpis jednotlivých prvků v poli, je nutné nastavit hloubku kontextu výpisu na 1 nebo vyšší.

Další informace o `CWordArray`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
