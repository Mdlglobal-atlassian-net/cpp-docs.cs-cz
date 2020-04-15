---
title: Třída CMapStringToString
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370122"
---
# <a name="cmapstringtostring-class"></a>Třída CMapStringToString

Podporuje mapy `CString` objektů zakódovaných objekty. `CString`

## <a name="syntax"></a>Syntaxe

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapStringToString` jsou podobné členské funkce třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti můžete `CMapStringToOb` použít referenční dokumentaci pro specifika členské funkce. Všude tam, kde vidíte `CObject` ukazatel jako návratovou hodnotu nebo parametr funkce "výstup", nahraďte ukazatel **char**. Všude tam, kde vidíte `CObject` ukazatel jako parametr funkce "vstup", nahraďte ukazatel **char**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

například znamená, že

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Veřejné struktury

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Vnořená struktura obsahující hodnotu klíče a hodnotu přidruženého objektu řetězce.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToString::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků v této mapě.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet prvků v tabulce hash.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iterace.|
|[CMapStringToString::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků v této mapě.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje tabulku hash.|
|[CMapStringToString::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testy pro podmínku prázdné mapy (žádné prvky).|
|[CMapStringToString::Vyhledávání](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá ukazatel void na základě klávesy ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapStringToString::Vyhledávací klíč](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Získá ukazatel na `CString` první v mapě.|
|[CMapStringToString::PGetNextAsSoc](#pgetnextassoc)|Získá ukazatel na `CString` další pro iterace.|
|[CMapStringToString::PVyhledávání](#plookup)|Vrátí ukazatel na `CString` jehož hodnota odpovídá zadané hodnotě.|
|[CMapStringToString::Removeall](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere prvek určený klíčem.|
|[CMapStringToString::Setat](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CMapStringToString::operátor \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – substituce operátora pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapStringToString`obsahuje `IMPLEMENT_SERIAL` makro pro podporu serializace a dumpingu jeho prvků. Každý prvek je serializován v pořadí, pokud je mapa uložena do **<<** archivu, buď `Serialize` s přetíženým operátorem insertion ( nebo s členovou funkcí.

Pokud potřebujete výpis jednotlivých `CString` -  `CString` prvků, musíte nastavit hloubku kontextu výpisu na 1 nebo vyšší.

Při `CMapStringToString` odstranění objektu nebo při odebrání jeho `CString` prvků jsou objekty odebrány podle potřeby.

Další informace `CMapStringToString`naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::CPair

Obsahuje hodnotu klíče a hodnotu přidruženého objektu řetězce.

### <a name="remarks"></a>Poznámky

Toto je vnořená struktura v rámci třídy [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

Struktura se skládá ze dvou polí:

- `key`Skutečná hodnota typu klíče.

- `value`Hodnota přidruženého objektu.

Používá se k uložení vrácené hodnoty z [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)a [CMapStringToString::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Příklad

  Příklad použití naleznete v příkladu [cmapstringtostring::PLookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc

Vrátí první položku objektu mapy.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první položku v mapě; viz [CMapStringToString::CPair](#cpair). Pokud je mapa prázdná, je hodnota NULL.

### <a name="remarks"></a>Poznámky

Volání této funkce vrátí ukazatel první prvek v objektu mapy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::PGetNextAsSoc

Načte prvek mapy, na který se vztahuje *zpráva pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parametry

*pAsoc*<br/>
Odkazuje na položku mapy vrácené předchozí [PGetNextAssoc](#pgetnextassoc) nebo [PGetFirstAssoc](#pgetfirstassoc) volání.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku v mapě; viz [CMapStringToString::CPair](#cpair). Pokud je prvek poslední v mapě, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Volání této metody iterát přes všechny prvky v mapě. Načíst první prvek s `PGetFirstAssoc` voláním a pak iterate `PGetNextAssoc`prostřednictvím mapy s následná volání .

### <a name="example"></a>Příklad

  Viz příklad [cmapstringtostring::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString::PVyhledávání

Vyhledá hodnotu namapovanou na daný klíč.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Ukazatel na klíč pro prvek, který má být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zadaný klíč.

### <a name="remarks"></a>Poznámky

Volání této metody k hledání prvku mapy s klíčem, který přesně odpovídá daný klíč.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
