---
title: Třída CDWordArray
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: e009ca3e3612d10d9cdf62d4bea32224f7b7522c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374001"
---
# <a name="cdwordarray-class"></a>Třída CDWordArray

Podporuje pole 32bitová dvojsloví.

## <a name="syntax"></a>Syntaxe

```
class CDWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CDWordArray` jsou podobné členské funkce třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete `CObArray` použít referenční dokumentaci pro specifika členské funkce. Všude tam, kde se `CObject` zobrazí ukazatel jako `DWORD`parametr funkce nebo vrácená hodnota, nahraďte .

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například znamená, že

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDWordArray::CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDWordArray::Přidat](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CDWordArray::Připojit](../../mfc/reference/cobarray-class.md#append)|Připojí k poli jiné pole; v případě potřeby pole zvětší.|
|[CDWordArray::Kopírovat](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CDWordArray::Elementat](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na bajt v rámci pole.|
|[CDWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CDWordArray::Getat](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CDWordArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CDWordArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být NULL.|
|[CDWordArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CDWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CDWordArray::Insertat](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CDWordArray::Jeprázdný](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CDWordArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[POLE CDWordArray::Removeat](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v určitém indexu.|
|[CDWordArray::Setat](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CDWordArray::Setatgrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CDWordArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CDWordArray::operátor \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

`CDWordArray`obsahuje `IMPLEMENT_SERIAL` makro pro podporu serializace a dumpingu jeho prvků. Pokud pole doublewords je uložen do archivu, buď s **<<** přetížené vložení `Serialize` ( ) operátor nebo s členskou funkcí, každý prvek je zase serializován.

> [!NOTE]
> Před použitím pole `SetSize` použijte k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Pokud potřebujete ladit výstup z jednotlivých prvků v poli, `CDumpContext` musíte nastavit hloubku objektu na 1 nebo vyšší.

Další informace o `CDWordArray`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CObArray](../../mfc/reference/cobarray-class.md)
