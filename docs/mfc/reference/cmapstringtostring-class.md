---
title: CMapStringToString – třída
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
ms.openlocfilehash: a2ffcf7ce7ee6eccc56382501a5969ddec6c9e22
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442594"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString – třída

Podporuje mapy `CString` objektů pomocí objektů `CString`.

## <a name="syntax"></a>Syntaxe

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapStringToString` jsou podobné členským funkcím třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CMapStringToOb` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako návratovou hodnotu nebo parametr funkce Output, nahraďte ukazatel na **char**. Všude, kde vidíte `CObject` ukazatel jako vstupní parametr funkce, nahraďte ukazatel na **char**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

například se přeloží na

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Veřejné struktury

|Název|Popis|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Vnořená struktura obsahující hodnotu klíče a hodnotu objektu přidruženého řetězce.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMapStringToString:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků v této mapě.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet prvků v zatřiďovací tabulce.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iteraci.|
|[CMapStringToString:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků v této mapě.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaného klíče.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje zatřiďovací tabulku.|
|[CMapStringToString::-Empty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje podmínku prázdné mapy (žádné elementy).|
|[CMapStringToString:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá ukazatel void na základě klíče ukazatele void. Hodnota ukazatele, nikoli entita, na kterou odkazuje, se používá pro porovnání klíčů.|
|[CMapStringToString:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč přidružený k zadané hodnotě klíče.|
|[CMapStringToString::P GetFirstAssoc](#pgetfirstassoc)|Získá ukazatel na první `CString` v mapě.|
|[CMapStringToString::P GetNextAssoc](#pgetnextassoc)|Získá ukazatel na další `CString` pro iteraci.|
|[CMapStringToString::P vyhledávání](#plookup)|Vrátí ukazatel na `CString`, jehož hodnota odpovídá zadané hodnotě.|
|[CMapStringToString::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere prvek určený klíčem.|
|[CMapStringToString::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud se najde shodný klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMapStringToString:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – nahrazení operátoru pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapStringToString` zahrnuje makro `IMPLEMENT_SERIAL` pro podporu serializace a dumpingu jeho prvků. Každý prvek je serializován v případě, že je mapa uložena do archivu, buď pomocí operátoru přetížení ( **<<** ), nebo pomocí členské funkce `Serialize`.

Pokud potřebujete výpis paměti jednotlivých `CString`- `CString` prvků, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Když je odstraněn objekt `CMapStringToString` nebo když jsou jeho prvky odebrány, objekty `CString` jsou podle potřeby odebrány.

Další informace o `CMapStringToString`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

##  <a name="cpair"></a>CMapStringToString::CPair

Obsahuje hodnotu klíče a hodnotu přidruženého objektu řetězce.

### <a name="remarks"></a>Poznámky

Toto je vnořená struktura ve třídě [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

Struktura se skládá ze dvou polí:

- `key` skutečnou hodnotu typu klíče.

- `value` hodnotu přidruženého objektu.

Slouží k ukládání vrácených hodnot z [CMapStringToString: lookup:P](#plookup), [CMapStringToString::P getfirstassoc](#pgetfirstassoc)a [CMapStringToString::P GetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Příklad

  Příklad použití naleznete v příkladu pro [CMapStringToString::P Lookup](#plookup).

##  <a name="pgetfirstassoc"></a>CMapStringToString::P GetFirstAssoc

Vrátí první položku objektu map.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první položku v mapě; viz [CMapStringToString:: CPair](#cpair). Pokud je mapa prázdná, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrátíte ukazatel na první prvek v objektu map.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>CMapStringToString::P GetNextAssoc

Načte prvek mapy, na který odkazuje *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parametry

*pAssoc*<br/>
Odkazuje na položku mapování vrácenou předchozím voláním [PGetNextAssoc](#pgetnextassoc) nebo [PGetFirstAssoc](#pgetfirstassoc) .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku v mapě; viz [CMapStringToString:: CPair](#cpair). Pokud je element na mapě poslední, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Voláním této metody můžete iterovat všechny prvky v mapě. Načtěte první prvek s voláním `PGetFirstAssoc` a potom proveďte iteraci přes mapu s následnými voláními pro `PGetNextAssoc`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMapStringToString::P getfirstassoc](#pgetfirstassoc).

##  <a name="plookup"></a>CMapStringToString::P vyhledávání

Vyhledá hodnotu namapovanou na daný klíč.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Ukazatel na klíč pro element, který má být prohledán.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zadaný klíč.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro vyhledání prvku mapy s klíčem, který přesně odpovídá zadanému klíči.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka MFC – shromáždit](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
