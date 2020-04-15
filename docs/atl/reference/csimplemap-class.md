---
title: Třída CSimpleMap
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: b8650f36ac3d190207870616754dcd596cb7cc45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330798"
---
# <a name="csimplemap-class"></a>Třída CSimpleMap

Tato třída poskytuje podporu pro jednoduché mapování pole.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Parametry

*Tkey*<br/>
Typ klíčového prvku.

*Tval (Tval)*<br/>
Typ prvku hodnoty.

*TEqual (TEqual)*<br/>
Objekt vlastnosti, definování testu rovnosti pro `T`prvky typu .

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Typedef pro typ hodnoty.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Typedef pro typ klíče.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Konstruktor|
|[CSimpleMap::~CSimpleMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSimpleMap::Přidat](#add)|Přidá klíč a přidruženou hodnotu do mapového pole.|
|[CSimpleMap::FindKey](#findkey)|Najde konkrétní klíč.|
|[CSimpleMap::FindVal](#findval)|Najde určitou hodnotu.|
|[CSimpleMap::GetKeyat](#getkeyat)|Načte zadaný klíč.|
|[CSimpleMap::GetSize](#getsize)|Vrátí počet položek v poli mapování.|
|[CSimpleMap::GetValueAt](#getvalueat)|Načte zadanou hodnotu.|
|[CSimpleMap::Vyhledávání](#lookup)|Vrátí hodnotu přidruženou k danému klíči.|
|[CSimpleMap::Odebrat](#remove)|Odebere klíč a odpovídající hodnotu.|
|[CSimpleMap::RemoveAll](#removeall)|Odebere všechny klíče a hodnoty.|
|[CSimpleMap::Removeat](#removeat)|Odebere konkrétní klíč a odpovídající hodnotu.|
|[CSimpleMap::Zpětné vyhledávání](#reverselookup)|Vrátí klíč přidružený k dané hodnotě.|
|[CSimpleMap::Setat](#setat)|Nastaví hodnotu přidruženou k danému klíči.|
|[CSimpleMap::SetatIndex](#setatindex)|Nastaví konkrétní klíč a hodnotu.|

## <a name="remarks"></a>Poznámky

`CSimpleMap`poskytuje podporu pro jednoduché mapování pole `T`libovolného typu , správa neuspořádané pole klíčových prvků a jejich přidružené hodnoty.

Parametr `TEqual` poskytuje prostředky definování funkce rovnosti pro dva `T`prvky typu . Vytvořením třídy podobné [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), je možné změnit chování testu rovnosti pro dané pole. Například při práci s pole ukazatelů, může být užitečné definovat rovnost jako v závislosti na hodnotách ukazatele odkaz. Výchozí implementace využívá **operator==()**.

Oba `CSimpleMap` a [CSimpleArray](../../atl/reference/csimplearray-class.md) jsou k dispozici pro kompatibilitu s předchozími verzemi ATL a úplnější a efektivnější implementace kolekce jsou poskytovány [CAtlArray](../../atl/reference/catlarray-class.md) a [CAtlMap](../../atl/reference/catlmap-class.md).

Na rozdíl od jiných kolekcí map v knihovnách ATL a MFC je tato třída implementována pomocí jednoduchého pole a vyhledávání vyhledávání vyžaduje lineární vyhledávání. `CAtlMap`by měl být použit, pokud pole obsahuje velký počet prvků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>CSimpleMap::Přidat

Přidá klíč a přidruženou hodnotu do mapového pole.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

*Val*<br/>
Přidružená hodnota.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl klíč a hodnota úspěšně přidány, jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Každý klíč a pár přidané hodnoty způsobí, že mapování paměti pole, které mají být uvolněny a přerozděleny, aby bylo zajištěno, že data pro každý je vždy uložen souvisle. To znamená, že druhý klíčový prvek vždy přímo následuje první klíčový prvek v paměti a tak dále.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType

Typedef pro typ klíče.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType

A typedef pro typ hodnoty.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap

Konstruktor

```
CSimpleMap();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap::~CSimpleMap

Destruktor.

```
~CSimpleMap();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey

Najde konkrétní klíč.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč k hledání.

### <a name="return-value"></a>Návratová hodnota

Vrátí index klíče, pokud byl nalezen, jinak vrátí hodnotu -1.

## <a name="csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal

Najde určitou hodnotu.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota, pro kterou chcete hledat.

### <a name="return-value"></a>Návratová hodnota

Vrátí index hodnoty, pokud je nalezena, jinak vrátí -1.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyat

Načte klíč na zadaný index.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index klíč vrátit.

### <a name="return-value"></a>Návratová hodnota

Vrátí klíč odkazovaný *nIndex*.

### <a name="remarks"></a>Poznámky

Index předaný *nIndex* musí být platný pro vrácenou hodnotu, která má být smysluplná.

## <a name="csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize

Vrátí počet položek v poli mapování.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek (klíč a hodnota je jedna položka) v poli mapování.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt

Načte hodnotu v konkrétním indexu.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index hodnoty, která má být vrácena.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, na kterou odkazuje *nIndex*.

### <a name="remarks"></a>Poznámky

Index předaný *nIndex* musí být platný pro vrácenou hodnotu, která má být smysluplná.

## <a name="csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Vyhledávání

Vrátí hodnotu přidruženou k danému klíči.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

### <a name="return-value"></a>Návratová hodnota

Vrátí přidruženou hodnotu. Pokud není nalezen žádný odpovídající klíč, je vrácena hodnota NULL.

## <a name="csimplemapremove"></a><a name="remove"></a>CSimpleMap::Odebrat

Odebere klíč a odpovídající hodnotu.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl klíč a odpovídající hodnota úspěšně odebrány, jinak NEPRAVDA.

## <a name="csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll

Odebere všechny klíče a hodnoty.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Odebere všechny klíče a hodnoty z objektu pole mapování.

## <a name="csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::Removeat

Odebere klíč a přidruženou hodnotu v zadaném indexu.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index klíče a přidružené hodnoty odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda, pokud je zadaný index neplatným indexem.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::Zpětné vyhledávání

Vrátí klíč přidružený k dané hodnotě.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí přidružený klíč. Pokud není nalezen žádný odpovídající klíč, je vrácena hodnota NULL.

## <a name="csimplemapsetat"></a><a name="setat"></a>CSimpleMap::Setat

Nastaví hodnotu přidruženou k danému klíči.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

*Val*<br/>
Nová hodnota přiřadit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl klíč nalezen a hodnota byla úspěšně změněna, jinak NEPRAVDA.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetatIndex

Nastaví klíč a hodnotu na zadaný index.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index, odkazující na klíč a hodnotu párování změnit.

*key*<br/>
Nový klíč.

*Val*<br/>
Nová hodnota.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšný, neplatí, pokud index nebyl platný.

### <a name="remarks"></a>Poznámky

Aktualizuje klíč i hodnotu, na kterou poukazuje *nIndex*.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
