---
title: CMapPtrToWord – třída
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapPtrToWord::CMapPtrToWord
- AFXCOLL/CMapPtrToWord::GetCount
- AFXCOLL/CMapPtrToWord::GetHashTableSize
- AFXCOLL/CMapPtrToWord::GetNextAssoc
- AFXCOLL/CMapPtrToWord::GetSize
- AFXCOLL/CMapPtrToWord::GetStartPosition
- AFXCOLL/CMapPtrToWord::HashKey
- AFXCOLL/CMapPtrToWord::InitHashTable
- AFXCOLL/CMapPtrToWord::IsEmpty
- AFXCOLL/CMapPtrToWord::Lookup
- AFXCOLL/CMapPtrToWord::LookupKey
- AFXCOLL/CMapPtrToWord::RemoveAll
- AFXCOLL/CMapPtrToWord::RemoveKey
- AFXCOLL/CMapPtrToWord::SetAt
helpviewer_keywords:
- CMapPtrToWord [MFC], CMapPtrToWord
- CMapPtrToWord [MFC], GetCount
- CMapPtrToWord [MFC], GetHashTableSize
- CMapPtrToWord [MFC], GetNextAssoc
- CMapPtrToWord [MFC], GetSize
- CMapPtrToWord [MFC], GetStartPosition
- CMapPtrToWord [MFC], HashKey
- CMapPtrToWord [MFC], InitHashTable
- CMapPtrToWord [MFC], IsEmpty
- CMapPtrToWord [MFC], Lookup
- CMapPtrToWord [MFC], LookupKey
- CMapPtrToWord [MFC], RemoveAll
- CMapPtrToWord [MFC], RemoveKey
- CMapPtrToWord [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: 698e306896fd62888a84b6d6ce55fb4c9678187b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442657"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord – třída

Podporuje mapy 16bitových slov pomocí ukazatelů typu void.

## <a name="syntax"></a>Syntaxe

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapPtrToWord` jsou podobné členským funkcím třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CMapStringToOb` pro konkrétní členské funkce. Bez ohledu na to, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte slovo. Bez ohledu na to, kde vidíte `CString` nebo **const** ukazatel na **char** jako parametr funkce nebo návratovou hodnotu, nahraďte ukazatel na **void**.

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

například se přeloží na

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMapPtrToWord::CMapPtrToWord](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMapPtrToWord:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků v této mapě.|
|[CMapPtrToWord::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapPtrToWord::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iteraci.|
|[CMapPtrToWord:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků v této mapě.|
|[CMapPtrToWord::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapPtrToWord::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapPtrToWord::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapPtrToWord::-Empty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje podmínku prázdné mapy (žádné elementy).|
|[CMapPtrToWord:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá ukazatel void na základě klíče ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapPtrToWord:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapPtrToWord::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapPtrToWord::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere prvek určený klíčem.|
|[CMapPtrToWord::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud se najde shodný klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMapPtrToWord:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – nahrazení operátoru pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapWordToPtr` zahrnuje makro IMPLEMENT_DYNAMIC pro podporu přístupu k běhovým typům a výpisu do objektu `CDumpContext`. Pokud potřebujete výpis paměti jednotlivých prvků mapy, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Mapy ukazatele na slova nemusejí být serializovány.

Když se odstraní objekt `CMapPtrToWord` nebo když se jeho prvky odeberou, odeberou se ukazatelé a slova. Entity, na které odkazují klíčové ukazatele, se neodstraňují.

Další informace o `CMapPtrToWord`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
