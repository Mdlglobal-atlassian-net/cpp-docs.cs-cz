---
title: Třída CStringArray
ms.date: 11/04/2016
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
- AFXCOLL/CStringArray::CStringArray
- AFXCOLL/CStringArray::Add
- AFXCOLL/CStringArray::Append
- AFXCOLL/CStringArray::Copy
- AFXCOLL/CStringArray::ElementAt
- AFXCOLL/CStringArray::FreeExtra
- AFXCOLL/CStringArray::GetAt
- AFXCOLL/CStringArray::GetCount
- AFXCOLL/CStringArray::GetData
- AFXCOLL/CStringArray::GetSize
- AFXCOLL/CStringArray::GetUpperBound
- AFXCOLL/CStringArray::InsertAt
- AFXCOLL/CStringArray::IsEmpty
- AFXCOLL/CStringArray::RemoveAll
- AFXCOLL/CStringArray::RemoveAt
- AFXCOLL/CStringArray::SetAt
- AFXCOLL/CStringArray::SetAtGrow
- AFXCOLL/CStringArray::SetSize
helpviewer_keywords:
- CStringArray [MFC], CStringArray
- CStringArray [MFC], Add
- CStringArray [MFC], Append
- CStringArray [MFC], Copy
- CStringArray [MFC], ElementAt
- CStringArray [MFC], FreeExtra
- CStringArray [MFC], GetAt
- CStringArray [MFC], GetCount
- CStringArray [MFC], GetData
- CStringArray [MFC], GetSize
- CStringArray [MFC], GetUpperBound
- CStringArray [MFC], InsertAt
- CStringArray [MFC], IsEmpty
- CStringArray [MFC], RemoveAll
- CStringArray [MFC], RemoveAt
- CStringArray [MFC], SetAt
- CStringArray [MFC], SetAtGrow
- CStringArray [MFC], SetSize
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
ms.openlocfilehash: 96a272cbbb76b399ed7a3db6848ab3f74a615a38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365992"
---
# <a name="cstringarray-class"></a>Třída CStringArray

Podporuje pole [CString](../../atl-mfc-shared/using-cstring.md) objektů.

## <a name="syntax"></a>Syntaxe

```
class CStringArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CStringArray` jsou podobné členské funkce třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete `CObArray` použít referenční dokumentaci pro specifika členské funkce. Všude tam, kde se zobrazí `CObject` ukazatel jako vrácená hodnota, nahraďte [cstring](../../atl-mfc-shared/using-cstring.md) objekt (ne ukazatel [CString).](../../atl-mfc-shared/using-cstring.md) Všude tam, kde se `CObject` ukazatel `LPCTSTR`zobrazí jako parametr funkce, nahraďte .

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například znamená, že

`CString CStringArray::GetAt( int <nIndex> ) const;`

a

`void SetAt( int <nIndex>, CObject* <newElement> )`

překládá do

`void SetAt( int <nIndex>, LPCTSTR <newElement> )`

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CStringArray::CStringArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStringArray::Přidat](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CStringArray::Připojit](../../mfc/reference/cobarray-class.md#append)|Připojí k poli jiné pole; v případě potřeby pole zvětší.|
|[CStringArray::Kopírovat](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[CStringArray::Elementat](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel prvku v rámci pole.|
|[CStringArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CStringArray::Getat](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CStringArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CStringArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být **NULL**.|
|[CStringArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CStringArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CStringArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CStringArray::Jeprázdný](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CStringArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[cstringarray::Removeat](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v určitém indexu.|
|[CStringArray::Setat](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CStringArray::Setatgrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CStringArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CStringArray::operátor \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

`CStringArray`obsahuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Pokud pole `CString` objektů je uložen do archivu, buď s přetížené `Serialize` vložení operátor nebo s členovou funkcí, každý prvek je serializován a zase.

> [!NOTE]
> Před použitím pole `SetSize` použijte k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Pokud potřebujete výpis jednotlivých řetězcových prvků v poli, musíte nastavit hloubku kontextu výpisu na 1 nebo vyšší.

Při `CString` odstranění pole nebo při odebrání jeho prvky, řetězec paměti je uvolněna podle potřeby.

Další informace o `CStringArray`použití naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CStringArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
