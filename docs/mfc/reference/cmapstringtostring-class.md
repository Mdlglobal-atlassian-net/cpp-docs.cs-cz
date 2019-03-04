---
title: CMapStringToString Class
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
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
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
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
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: d18cad73f9cf42ffd04ecbcde840d50f6167743a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266221"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString Class

Podporuje mapy `CString` označenými pomocí objektů `CString` objekty.

## <a name="syntax"></a>Syntaxe

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CMapStringToString` jsou podobné jako u členských funkcí třídy [cmapstringtoob –](../../mfc/reference/cmapstringtoob-class.md). Z důvodu podobnosti, můžete použít `CMapStringToOb` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení `CObject` ukazatele jako parametr, návratová hodnota nebo "výstupní" funkce nahraďte ukazatelem na **char**. Po zobrazení `CObject` nahraďte ukazatel na ukazatel jako parametr funkce "input" **char**.

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

například se přeloží na

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

### <a name="public-structures"></a>Veřejné struktury

|Název|Popis|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Vnořené struktury obsahující hodnotu klíče a hodnoty objektu přidruženými řetězcovými.|

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
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Získá ukazatel na první `CString` v objektu map.|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Získá ukazatel na další `CString` pro iterace.|
|[CMapStringToString::PLookup](#plookup)|Vrací ukazatel `CString` jejíž hodnota odpovídá zadané hodnotě.|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny prvky z této mapy.|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere element určený klíč.|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží prvek do mapy – operátor nahrazení pro `SetAt`.|

## <a name="remarks"></a>Poznámky

`CMapStringToString` zahrnuje `IMPLEMENT_SERIAL` – makro na podporu serializace a výpis z jeho prvků. Každý prvek je zase serializovat, když mapy je uložit do archivu, buď pomocí přetížených vložení ( **<<**) – operátor nebo se `Serialize` členskou funkci.

Pokud potřebujete s výpisem paměti jednotlivých `CString` -  `CString` prvky, hloubka kontextu výpisu stavu systému je nutné nastavit na 1 nebo větší.

Když `CMapStringToString` odstranění objektu, nebo když se odeberou jeho prvky, `CString` odeberou objekty podle potřeby.

Další informace o `CMapStringToString`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

##  <a name="cpair"></a>  CMapStringToString::CPair

Obsahuje hodnotu klíče a hodnoty objektu přidruženými řetězcovými.

### <a name="remarks"></a>Poznámky

Toto je vnořené struktury v rámci třídy [cmapstringtostring –](../../mfc/reference/cmapstringtostring-class.md).

Struktura se skládá ze dvou polí:

- `key` Skutečná hodnota typ klíče.

- `value` Hodnota přidruženého objektu.

Se používá k ukládání vrácené hodnoty z [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc), a [CMapStringToString::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Příklad

  Příklad použití, podívejte se na příklad pro [CMapStringToString::PLookup](#plookup).

##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc

Vrátí první položku v objektu map.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první položku v mapě. Zobrazit [CMapStringToString::CPair](#cpair). Pokud mapa je prázdné, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrací ukazatel první prvek v objektu map.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc

Načte prvek mapy, na které odkazuje *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parametry

*pAssoc*<br/>
Odkazuje na položku mapování vrácený předchozím [PGetNextAssoc](#pgetnextassoc) nebo [PGetFirstAssoc](#pgetfirstassoc) volání.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položky na mapě; Zobrazit [CMapStringToString::CPair](#cpair). Pokud prvek je poslední v objektu map, hodnota je NULL.

### <a name="remarks"></a>Poznámky

Voláním této metody lze iterovat přes všechny prvky v objektu map. Načíst první prvek voláním `PGetFirstAssoc` a potom iteraci v rámci mapy při následných voláních na `PGetNextAssoc`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).

##  <a name="plookup"></a>  CMapStringToString::PLookup

Vyhledá hodnotu namapována na daný klíč.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Ukazatel na klíč pro prvek, který má být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Ukazatel se zadaným klíčem.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem vyhledání prvek mapy s klíčem, který přesně odpovídá danému klíči.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC shromažďování](../../visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
