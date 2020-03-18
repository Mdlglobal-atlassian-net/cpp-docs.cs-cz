---
title: CMapPtrToPtr – třída
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::GetCount
- AFXCOLL/CMapPtrToPtr::GetHashTableSize
- AFXCOLL/CMapPtrToPtr::GetNextAssoc
- AFXCOLL/CMapPtrToPtr::GetSize
- AFXCOLL/CMapPtrToPtr::GetStartPosition
- AFXCOLL/CMapPtrToPtr::HashKey
- AFXCOLL/CMapPtrToPtr::InitHashTable
- AFXCOLL/CMapPtrToPtr::IsEmpty
- AFXCOLL/CMapPtrToPtr::Lookup
- AFXCOLL/CMapPtrToPtr::LookupKey
- AFXCOLL/CMapPtrToPtr::RemoveAll
- AFXCOLL/CMapPtrToPtr::RemoveKey
- AFXCOLL/CMapPtrToPtr::SetAt
helpviewer_keywords:
- CMapPtrToPtr [MFC], CMapPtrToPtr
- CMapPtrToPtr [MFC], GetCount
- CMapPtrToPtr [MFC], GetHashTableSize
- CMapPtrToPtr [MFC], GetNextAssoc
- CMapPtrToPtr [MFC], GetSize
- CMapPtrToPtr [MFC], GetStartPosition
- CMapPtrToPtr [MFC], HashKey
- CMapPtrToPtr [MFC], InitHashTable
- CMapPtrToPtr [MFC], IsEmpty
- CMapPtrToPtr [MFC], Lookup
- CMapPtrToPtr [MFC], LookupKey
- CMapPtrToPtr [MFC], RemoveAll
- CMapPtrToPtr [MFC], RemoveKey
- CMapPtrToPtr [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: b4ae511caab8278daf723bbcb8ffc5d57f5a1cd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442667"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr – třída

Podporuje mapy ukazatelů typu void pomocí ukazatelů typu void.

## <a name="syntax"></a>Syntaxe

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapPtrToPtr` jsou podobné členským funkcím třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CMapStringToOb` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte ukazatel na **void**. Bez ohledu na to, kde vidíte `CString` nebo **const** ukazatel na **char** jako parametr funkce nebo návratovou hodnotu, nahraďte ukazatel na **void**.

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

například se přeloží na

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMapPtrToPtr::CMapPtrToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMapPtrToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků v této mapě.|
|[CMapPtrToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapPtrToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iteraci.|
|[CMapPtrToPtr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků v této mapě.|
|[CMapPtrToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapPtrToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapPtrToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapPtrToPtr::-Empty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje podmínku prázdné mapy (žádné elementy).|
|[CMapPtrToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá ukazatel void na základě klíče ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapPtrToPtr:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapPtrToPtr::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapPtrToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere prvek určený klíčem.|
|[CMapPtrToPtr::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud se najde shodný klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMapPtrToPtr:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – nahrazení operátoru pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapPtrToPtr` zahrnuje makro IMPLEMENT_DYNAMIC pro podporu přístupu k běhovým typům a výpisu do objektu `CDumpContext`. Pokud potřebujete výpis paměti jednotlivých prvků mapy (hodnoty ukazatelů), je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Mapy ukazatelů na ukazatele nelze serializovat.

Když je odstraněn objekt `CMapPtrToPtr` nebo když jsou jeho prvky odebrány, jsou odebrány pouze ukazatele, nikoli entity, na které odkazují.

Další informace o `CMapPtrToPtr`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
