---
title: CStringList – třída
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 08e481f010be688fb0b9c219caa1954c9960846f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346264"
---
# <a name="cstringlist-class"></a>CStringList – třída

Podporuje seznamy `CString` objekty.

## <a name="syntax"></a>Syntaxe

```
class CStringList : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CStringList` jsou podobné jako u členských funkcí třídy [coblist –](../../mfc/reference/coblist-class.md). Z důvodu podobnosti, můžete použít `CObList` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení `CObject` ukazatel jako návratová hodnota, nahraďte `CString` (není `CString` ukazatele). Po zobrazení `CObject` ukazatele jako parametr funkce, použijte `LPCTSTR`.

`CObject*& CObList::GetHead() const;`

například se přeloží na

`CString& CStringList::GetHead() const;`

and

`POSITION AddHead( CObject* <newElement> );`

přeloží na

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Vytvoří prázdný seznam.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Přidá k začátku seznamu (novou vedoucí díky) elementu (nebo všechny prvky v jiném seznamu).|
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Přidá na konec seznamu (umožňuje nové funkce tail) elementu (nebo všechny prvky v jiném seznamu).|
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Získá pozici prvku určeného hodnotou ukazatele.|
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Získá pozici prvku určený index založený na nule.|
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Získá prvek na dané pozici.|
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Vrátí počet prvků v tomto seznamu.|
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Vrátí element head seznamu (nemůže být prázdný).|
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Vrátí pozici element head seznamu.|
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Získá další prvek pro iterace.|
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Získá předchozí prvek pro iterace.|
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Vrátí počet prvků v tomto seznamu.|
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Vrátí pozici prvku tail seznamu.|
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Vloží nový prvek za danou pozici.|
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Vloží nový prvek před danou pozici.|
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Testy pro prázdný seznam podmínku (žádné elementy).|
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Odebere všechny prvky z tohoto seznamu.|
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Odebere element z tohoto seznamu, určené pozici.|
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Odebere element z prvního seznamu.|
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Odebere element z konec seznamu.|
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Nastaví element na dané pozici.|

## <a name="remarks"></a>Poznámky

Všechna porovnání provádí hodnotou, což znamená, že jsou místo adresy řetězce porovnány znaků v řetězci.

`CStringList` zahrnuje IMPLEMENT_SERIAL – makro na podporu serializace a výpis z jeho prvků. Pokud seznam `CString` objekty je uložit do archivu, s operátorem vložení přetížené nebo se `Serialize` členské funkce se každý `CString` zase serializuje jako element.

Pokud potřebujete s výpisem paměti jednotlivých `CString` prvky, hloubka kontextu výpisu stavu systému je nutné nastavit na 1 nebo větší.

Další informace o používání `CStringList`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC shromažďování](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
