---
title: Cmapptrtoptr – třída
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: ec635ea00c9659d43d148c55e02a70a7c759279a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540826"
---
# <a name="cmapptrtoptr-class"></a>Cmapptrtoptr – třída

Podporuje mapy ukazatelů typu void označenými pomocí ukazatelů typu void.

## <a name="syntax"></a>Syntaxe

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapPtrToPtr` jsou podobné jako u členských funkcí třídy [cmapstringtoob –](../../mfc/reference/cmapstringtoob-class.md). Z důvodu podobnosti, můžete použít `CMapStringToOb` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení `CObject` ukazatele jako parametr funkce nebo návratová hodnota, nahraďte ukazatel na **void**. Po zobrazení `CString` nebo **const** ukazatel na **char** jako parametr funkce nebo návratová hodnota, nahraďte ukazatelem na **void**.

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

například se přeloží na

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků, které na této mapě.|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iterace.|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků, které na této mapě.|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaný klíč.|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testy pro podmínku prázdný mapy (žádné elementy).|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá neplatný ukazatel na základě klíče ukazatele. Hodnota ukazatele, není entita, na kterou odkazuje, je použita pro porovnání klíčů.|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč přidružený k zadanou hodnotou klíče.|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere element určený klíč.|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[[] Č. CMapStringToOb::operator](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – operátor nahrazení pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapPtrToPtr` zahrnuje IMPLEMENT_DYNAMIC – makro pro podporu přístupu typu modulu runtime a k vypsání `CDumpContext` objektu. Pokud potřebujete s výpisem paměti jednotlivých prvků (ukazatel hodnoty), nastavte na 1 nebo větší hloubky kontextu s výpisem paměti.

Ukazatel na ukazatel mapy nesmí být serializován.

Když `CMapPtrToPtr` odstranění objektu nebo při jeho prvky jsou odebrány, odeberou se jenom ukazatele, není entity, které odkazují.

Další informace o `CMapPtrToPtr`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

