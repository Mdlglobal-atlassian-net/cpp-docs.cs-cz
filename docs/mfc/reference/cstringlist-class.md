---
title: CStringList – třída
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CStringList::CStringList
- AFXCOLL/CStringList::AddHead
- AFXCOLL/CStringList::AddTail
- AFXCOLL/CStringList::Find
- AFXCOLL/CStringList::FindIndex
- AFXCOLL/CStringList::GetAt
- AFXCOLL/CStringList::GetCount
- AFXCOLL/CStringList::GetHead
- AFXCOLL/CStringList::GetHeadPosition
- AFXCOLL/CStringList::GetNext
- AFXCOLL/CStringList::GetPrev
- AFXCOLL/CStringList::GetSize
- AFXCOLL/CStringList::GetTail
- AFXCOLL/CStringList::GetTailPosition
- AFXCOLL/CStringList::InsertAfter
- AFXCOLL/CStringList::InsertBefore
- AFXCOLL/CStringList::IsEmpty
- AFXCOLL/CStringList::RemoveAll
- AFXCOLL/CStringList::RemoveAt
- AFXCOLL/CStringList::RemoveHead
- AFXCOLL/CStringList::RemoveTail
- AFXCOLL/CStringList::SetAt
helpviewer_keywords:
- CStringList [MFC], CStringList
- CStringList [MFC], AddHead
- CStringList [MFC], AddTail
- CStringList [MFC], Find
- CStringList [MFC], FindIndex
- CStringList [MFC], GetAt
- CStringList [MFC], GetCount
- CStringList [MFC], GetHead
- CStringList [MFC], GetHeadPosition
- CStringList [MFC], GetNext
- CStringList [MFC], GetPrev
- CStringList [MFC], GetSize
- CStringList [MFC], GetTail
- CStringList [MFC], GetTailPosition
- CStringList [MFC], InsertAfter
- CStringList [MFC], InsertBefore
- CStringList [MFC], IsEmpty
- CStringList [MFC], RemoveAll
- CStringList [MFC], RemoveAt
- CStringList [MFC], RemoveHead
- CStringList [MFC], RemoveTail
- CStringList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 9eb7a713fc02cd3e51135d1985a41688d4c885d9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447557"
---
# <a name="cstringlist-class"></a>CStringList – třída

Podporuje seznamy `CString` objektů.

## <a name="syntax"></a>Syntaxe

```
class CStringList : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CStringList` jsou podobné členským funkcím třídy [CObList](../../mfc/reference/coblist-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CObList` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako návratovou hodnotu, nahraďte `CString` (nikoli ukazatel `CString`). Všude, kde vidíte `CObject` ukazatel jako parametr funkce, nahraďte `LPCTSTR`.

`CObject*& CObList::GetHead() const;`

například se přeloží na

`CString& CStringList::GetHead() const;`

a

`POSITION AddHead( CObject* <newElement> );`

překládá se

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStringList::CStringList](../../mfc/reference/coblist-class.md#coblist)|Vytvoří prázdný seznam.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Přidá prvek (nebo všechny prvky v jiném seznamu) do záhlaví seznamu (vytvoří novou hlavu).|
|[CStringList:: AddTail –](../../mfc/reference/coblist-class.md#addtail)|Přidá prvek (nebo všechny prvky v jiném seznamu) na konec seznamu (vytvoří nový konec).|
|[CStringList:: Find](../../mfc/reference/coblist-class.md#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CStringList:: FindIndex –](../../mfc/reference/coblist-class.md#findindex)|Získá pozici prvku určeného indexem založeným na nule.|
|[CStringList::GetAt](../../mfc/reference/coblist-class.md#getat)|Získá prvek na dané pozici.|
|[CStringList:: GetCount](../../mfc/reference/coblist-class.md#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CStringList:: GetHead](../../mfc/reference/coblist-class.md#gethead)|Vrátí element head seznamu (nemůže být prázdný).|
|[CStringList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Vrátí pozici elementu Head v seznamu.|
|[CStringList:: GetNext](../../mfc/reference/coblist-class.md#getnext)|Získá další prvek pro iteraci.|
|[CStringList:: getpředchozí](../../mfc/reference/coblist-class.md#getprev)|Získá předchozí prvek pro iteraci.|
|[CStringList:: GetSize](../../mfc/reference/coblist-class.md#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CStringList:: GetTail](../../mfc/reference/coblist-class.md#gettail)|Vrátí element Tail seznamu (nemůže být prázdný).|
|[CStringList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Vrátí pozici koncového prvku seznamu.|
|[CStringList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Vloží nový prvek za danou pozici.|
|[CStringList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Vloží nový prvek před danou pozici.|
|[CStringList::-Empty](../../mfc/reference/coblist-class.md#isempty)|Testuje podmínku prázdného seznamu (žádné elementy).|
|[CStringList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[CStringList:: funkce RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Odebere prvek z tohoto seznamu, který je určen pozicí.|
|[CStringList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Odebere prvek ze záhlaví seznamu.|
|[CStringList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Odebere prvek ze strany seznamu.|
|[CStringList::SetAt](../../mfc/reference/coblist-class.md#setat)|Nastaví prvek na dané pozici.|

## <a name="remarks"></a>Poznámky

Všechna porovnání jsou prováděna hodnotou, což znamená, že znaky v řetězci jsou porovnány namísto adres řetězců.

`CStringList` zahrnuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Pokud je seznam objektů `CString` uložen do archivu, buď pomocí přetíženého operátoru vložení nebo pomocí `Serialize` členské funkce, je každý prvek `CString` serializován.

Pokud potřebujete výpis paměti jednotlivých `CString` prvků, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Další informace o používání `CStringList`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[Ukázka MFC – shromáždit](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
