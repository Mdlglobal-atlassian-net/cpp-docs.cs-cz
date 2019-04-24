---
title: Csimplemap – třída
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
ms.openlocfilehash: afd9f017bb0fb9a95a0ed4fd135dcbd5ea4ddba2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277939"
---
# <a name="csimplemap-class"></a>Csimplemap – třída

Tato třída poskytuje podporu pro jednoduché mapování pole.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Parametry

*TKey*<br/>
Typ klíče prvku.

*TVal*<br/>
Typ elementu hodnota.

*TEqual*<br/>
Objekt vlastností definující test rovnosti pro prvky typu `T`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Definice typu pro typ hodnoty.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Definice typu pro typ klíče.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Konstruktor|
|[CSimpleMap::~CSimpleMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSimpleMap::Add](#add)|Přidá klíč a přidružené hodnoty pole mapování.|
|[CSimpleMap::FindKey](#findkey)|Vyhledá konkrétní klíč.|
|[CSimpleMap::FindVal](#findval)|Vyhledá konkrétní hodnotu.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Načte se zadaným klíčem.|
|[CSimpleMap::GetSize](#getsize)|Vrátí počet položek v mapování pole.|
|[CSimpleMap::GetValueAt](#getvalueat)|Načte zadanou hodnotu.|
|[CSimpleMap::Lookup](#lookup)|Vrátí hodnotu přidruženou k danému klíči.|
|[CSimpleMap::Remove](#remove)|Odebere klíč a odpovídající hodnotu.|
|[CSimpleMap::RemoveAll](#removeall)|Odebere všechny klíče a hodnoty.|
|[CSimpleMap::RemoveAt](#removeat)|Odebere specifický klíč a odpovídající hodnotu.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Vrátí klíč přidružený k dané hodnoty hodnotu.|
|[CSimpleMap::SetAt](#setat)|Nastaví hodnotu přidruženou k danému klíči.|
|[CSimpleMap::SetAtIndex](#setatindex)|Nastaví konkrétní klíče a hodnoty.|

## <a name="remarks"></a>Poznámky

`CSimpleMap` poskytuje podporu pro jednoduché mapování pole daného typu `T`, Správa Neseřazený pole klíčové prvky a jejich přidružené hodnoty.

Parametr `TEqual` poskytuje způsob definice funkce protokolem rovnosti dvou prvků typu `T`. Vytvořením třídy podobný [csimplemapequalhelper –](../../atl/reference/csimplemapequalhelper-class.md), je možné změnit chování test rovnosti pro jakékoli dané pole. Například při práci s pole ukazatelů, může být vhodné definovat rovnost jako v závislosti na hodnoty, které odkazují ukazatele. Výchozí implementace využívá **operator==()**.

Obě `CSimpleMap` a [csimplearray –](../../atl/reference/csimplearray-class.md) jsou k dispozici pro kompatibilitu s předchozím ATL uvolní a dokončení a efektivní implementace kolekcí jsou k dispozici v [catlarray –](../../atl/reference/catlarray-class.md) a [ Catlmap –](../../atl/reference/catlmap-class.md).

Na rozdíl od jiných kolekcí mapy v ATL a MFC Tato třída implementuje pomocí jednoduchých polí a vyhledávání vyhledávání vyžaduje lineárního hledání. `CAtlMap` je třeba použít, když pole obsahuje velký počet prvků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

##  <a name="add"></a>  CSimpleMap::Add

Přidá klíč a přidružené hodnoty pole mapování.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

*Val*<br/>
Přidružená hodnota.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud klíč a hodnotu byly úspěšně přidal, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Každý pár klíč a hodnotu přidá mapování pole paměť uvolněno a nevyčerpané, aby se zajistilo, že jsou data pro každou vždy uložena souvisle příčiny. To znamená druhý klíčovým prvkem vždy přímo následuje po první klíče prvku v paměti a tak dále.

##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType

Definice typu pro typ klíče.

```
typedef TVal _ArrayElementType;
```

##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType

Definice typu pro typ hodnoty.

```
typedef TKey _ArrayKeyType;
```

##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap

Konstruktor

```
CSimpleMap();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy.

##  <a name="dtor"></a>  CSimpleMap::~CSimpleMap

Destruktor.

```
~CSimpleMap();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="findkey"></a>  CSimpleMap::FindKey

Vyhledá konkrétní klíč.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Vrátí index klíče if nalezena, jinak vrátí hodnotu -1.

##  <a name="findval"></a>  CSimpleMap::FindVal

Vyhledá konkrétní hodnotu.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota, pro který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Vrátí že index hodnoty je-li nalezeno, jinak vrátí hodnotu -1.

##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt

Načte klíč v zadaném indexu.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index klíče k vrácení.

### <a name="return-value"></a>Návratová hodnota

Vrátí klíč odkazuje *nIndex*.

### <a name="remarks"></a>Poznámky

Index předávány *nIndex* musí být platná pro návratovou hodnotu smysl.

##  <a name="getsize"></a>  CSimpleMap::GetSize

Vrátí počet položek v mapování pole.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek (klíče a hodnoty je jedna položka), které v mapování pole.

##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt

Načte hodnotu na konkrétní pozici indexu.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index vrácenou hodnotu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu odkazuje *nIndex*.

### <a name="remarks"></a>Poznámky

Index předávány *nIndex* musí být platná pro návratovou hodnotu smysl.

##  <a name="lookup"></a>  CSimpleMap::Lookup

Vrátí hodnotu přidruženou k danému klíči.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

### <a name="return-value"></a>Návratová hodnota

Vrátí související hodnotu. Pokud není žádný odpovídající klíč nalezen, NULL, je vrácena.

##  <a name="remove"></a>  CSimpleMap::Remove

Odebere klíč a odpovídající hodnotu.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud klíč a odpovídající hodnotu, byly úspěšně se odebral, FALSE, jinak.

##  <a name="removeall"></a>  CSimpleMap::RemoveAll

Odebere všechny klíče a hodnoty.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Odebere všechny klíče a hodnoty z objektu mapování pole.

##  <a name="removeat"></a>  CSimpleMap::RemoveAt

Odebere klíč a přidruženou hodnotu v zadaném indexu.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index klíč a hodnotu přiřazenou k odebrání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; FALSE, pokud zadaný index je neplatný index.

##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup

Vrátí klíč přidružený k dané hodnoty hodnotu.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota

### <a name="return-value"></a>Návratová hodnota

Vrátí přidružený klíč. Pokud není žádný odpovídající klíč nalezen, NULL, je vrácena.

##  <a name="setat"></a>  CSimpleMap::SetAt

Nastaví hodnotu přidruženou k danému klíči.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč

*Val*<br/>
Nová hodnota pro přiřazení.

### <a name="return-value"></a>Návratová hodnota

Pokud byl nalezen klíč a hodnota byla úspěšně změněná, FALSE, v opačném případě vrátí hodnotu TRUE.

##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex

Nastaví klíč a hodnotu v zadaném indexu.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index, odkazující na klíč a hodnotu párování, díky kterému změnit.

*key*<br/>
Nový klíč.

*Val*<br/>
Nová hodnota.

### <a name="return-value"></a>Návratová hodnota

Vrací TRUE, pokud úspěšné, FALSE, pokud index nebyl platný.

### <a name="remarks"></a>Poznámky

Aktualizace klíče a hodnoty, na které odkazuje *nIndex*.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
