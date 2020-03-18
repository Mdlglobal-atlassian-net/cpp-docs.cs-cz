---
title: CMapWordToPtr Class
ms.date: 11/04/2016
f1_keywords:
- CMapWordToPtr
- AFXCOLL/CMapWordToPtr
- AFXCOLL/CMapWordToPtr::CMapWordToPtr
- AFXCOLL/CMapWordToPtr::GetCount
- AFXCOLL/CMapWordToPtr::GetHashTableSize
- AFXCOLL/CMapWordToPtr::GetNextAssoc
- AFXCOLL/CMapWordToPtr::GetSize
- AFXCOLL/CMapWordToPtr::GetStartPosition
- AFXCOLL/CMapWordToPtr::HashKey
- AFXCOLL/CMapWordToPtr::InitHashTable
- AFXCOLL/CMapWordToPtr::IsEmpty
- AFXCOLL/CMapWordToPtr::Lookup
- AFXCOLL/CMapWordToPtr::LookupKey
- AFXCOLL/CMapWordToPtr::RemoveAll
- AFXCOLL/CMapWordToPtr::RemoveKey
- AFXCOLL/CMapWordToPtr::SetAt
helpviewer_keywords:
- CMapWordToPtr [MFC], CMapWordToPtr
- CMapWordToPtr [MFC], GetCount
- CMapWordToPtr [MFC], GetHashTableSize
- CMapWordToPtr [MFC], GetNextAssoc
- CMapWordToPtr [MFC], GetSize
- CMapWordToPtr [MFC], GetStartPosition
- CMapWordToPtr [MFC], HashKey
- CMapWordToPtr [MFC], InitHashTable
- CMapWordToPtr [MFC], IsEmpty
- CMapWordToPtr [MFC], Lookup
- CMapWordToPtr [MFC], LookupKey
- CMapWordToPtr [MFC], RemoveAll
- CMapWordToPtr [MFC], RemoveKey
- CMapWordToPtr [MFC], SetAt
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
ms.openlocfilehash: 71d79f9f57be2cdfe16c526bd50173a8ec3c5829
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442571"
---
# <a name="cmapwordtoptr-class"></a>CMapWordToPtr Class

Podporuje mapy ukazatelů typu void označených pomocí 16bitových slov.

## <a name="syntax"></a>Syntaxe

```
class CMapWordToPtr : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapWordToPtr` jsou podobné členským funkcím třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CMapStringToOb` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte ukazatel na **void**. Bez ohledu na to, kde vidíte `CString` nebo **const** ukazatel na **char** jako parametr funkce nebo návratovou hodnotu, nahraďte slovo.

`BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`

například se přeloží na

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMapWordToPtr::CMapWordToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMapWordToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků v této mapě.|
|[CMapWordToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapWordToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iteraci.|
|[CMapWordToPtr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků v této mapě.|
|[CMapWordToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapWordToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapWordToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapWordToPtr::-Empty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje podmínku prázdné mapy (žádné elementy).|
|[CMapWordToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá ukazatel void na základě klíče ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapWordToPtr:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapWordToPtr::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapWordToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere prvek určený klíčem.|
|[CMapWordToPtr::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud se najde shodný klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMapWordToPtr:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – nahrazení operátoru pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapWordToPtr` zahrnuje makro IMPLEMENT_DYNAMIC pro podporu přístupu k běhovým typům a výpisu do objektu `CDumpContext`. Pokud potřebujete výpis paměti jednotlivých prvků mapy, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Mapy na ukazateli nelze serializovat.

Když je odstraněn objekt `CMapWordToPtr` nebo když jsou jeho prvky odebrány, jsou slova a odkazy odebrány. Entity odkazované ukazateli nejsou odebrány.

Další informace o `CMapWordToPtr`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
