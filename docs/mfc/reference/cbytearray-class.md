---
title: Třída CByteArray
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 9da30f6546a69a51c56bf4b27668e1603c13290b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352388"
---
# <a name="cbytearray-class"></a>Třída CByteArray

Podporuje dynamická pole bajtů.

## <a name="syntax"></a>Syntaxe

```
class CByteArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CByteArray` jsou podobné členské funkce třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete `CObArray` použít referenční dokumentaci pro specifika členské funkce. Všude tam, kde vidíte `CObject` ukazatel jako parametr funkce nebo vrácenou hodnotu, nahraďte BYTE.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například znamená, že

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CByteArray::CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CByteArray::Přidat](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CByteArray::Připojit](../../mfc/reference/cobarray-class.md#append)|Připojí k poli jiné pole; v případě potřeby pole zvětší.|
|[CByteArray::Kopírovat](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CByteArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na bajt v rámci pole.|
|[CByteArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CByteArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CByteArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CByteArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být NULL.|
|[CByteArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CByteArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CByteArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CByteArray::Jeprázdný](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CByteArray::OdstranitVše](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CByteArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v určitém indexu.|
|[CByteArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CByteArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CByteArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CByteArray::operátor \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

`CByteArray`obsahuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Pokud pole bajtů je uložen do archivu, buď s **<<** přetížené vložení `Serialize` ( ) operátor nebo s členovou funkcí, každý prvek je zase serializován.

> [!NOTE]
> Před použitím pole `SetSize` použijte k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Pokud potřebujete ladit výstup z jednotlivých prvků v poli, `CDumpContext` musíte nastavit hloubku objektu na 1 nebo vyšší.

Další informace o `CByteArray`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CObArray](../../mfc/reference/cobarray-class.md)
