---
title: Třída CRBTree
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 56c9db9d1a7bcd7fe2a2647d8b1339d223c4b66b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331240"
---
# <a name="crbtree-class"></a>Třída CRBTree

Tato třída poskytuje metody pro vytváření a využití červeno-černý strom.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Typ klíčového prvku.

*V*<br/>
Typ prvku hodnoty.

*KTraity*<br/>
Kód používaný ke kopírování nebo přesunutí klíčových prvků. Další podrobnosti najdete v [části CElementTraits Class.](../../atl/reference/celementtraits-class.md)

*VTraits*<br/>
Kód používaný ke kopírování nebo přesouvání prvků hodnoty.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Typ použitý při předání klíče jako vstupní argument.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ použitý při vrácení klíče jako výstupního argumentu.|
|[CRBTree::VINARGTYPE](#vinargtype)|Typ použitý při předání hodnoty jako vstupní argument.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ použitý při předání hodnoty jako výstupní argument.|

### <a name="public-classes"></a>Veřejné třídy

|Name (Název)|Popis|
|----------|-----------------|
|[CRBTree::Třída CPair](#cpair_class)|Třída obsahující klíčové a hodnotové prvky.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CRBTree::~CRBTree](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Volání této metody najít pozici prvku, který používá další dostupný klíč.|
|[CRBTree::Getat](#getat)|Volání této metody získat prvek na dané pozici ve stromu.|
|[CRBTree::GetCount](#getcount)|Volání této metody získat počet prvků ve stromu.|
|[CRBTree::GetheadPozice](#getheadposition)|Volání této metody získat hodnotu pozice pro prvek v čele stromu.|
|[CRBTree::GetKeyat](#getkeyat)|Volání této metody získat klíč z dané pozice ve stromu.|
|[CRBTree::GetNext](#getnext)|Volání této metody získat ukazatel na prvek `CRBTree` uložený v objektu a posunut pozici na další prvek.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Volání této metody získat klíč a hodnotu prvku uloženého v mapě a posunut pozici na další prvek.|
|[CRBTree::GetNextKey](#getnextkey)|Volání této metody získat klíč prvku uloženého ve stromu a posunut pozici na další prvek.|
|[CRBTree::GetNextValue](#getnextvalue)|Volání této metody získat hodnotu prvku uloženého ve stromu a posunut pozici na další prvek.|
|[CRBTree::GetPrev](#getprev)|Volání této metody získat ukazatel na prvek `CRBTree` uložený v objektu a potom aktualizovat pozici předchozí prvek.|
|[CRBTree::GettailPosition](#gettailposition)|Volání této metody získat hodnotu pozice pro prvek na konci stromu.|
|[CRBTree::GetValueAt](#getvalueat)|Volání této metody načíst hodnotu uloženou `CRBTree` na dané pozici v objektu.|
|[CRBTree::Jeprázdný](#isempty)|Volání této metody k testování objektu prázdné stromu.|
|[CRBTree::RemoveAll](#removeall)|Volání této metody odebrat `CRBTree` všechny prvky z objektu.|
|[CRBTree::RemoveAt](#removeat)|Volání této metody odebrat prvek na `CRBTree` dané pozici v objektu.|
|[CRBTree::SetValueAt](#setvalueat)|Volání této metody změnit hodnotu uloženou `CRBTree` na dané pozici v objektu.|

## <a name="remarks"></a>Poznámky

Red-Black strom je binární vyhledávací strom, který používá další bit informací na uzel k zajištění, že zůstane "vyvážený", to znamená, že výška stromu neroste nepřiměřeně velké a ovlivnit výkon.

Tato třída šablony je určena pro použití [CRBMap](../../atl/reference/crbmap-class.md) a [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Převážná část metod, které tvoří tyto odvozené `CRBTree`třídy jsou poskytovány .

Podrobnější diskusi o různých třídách kolekce a jejich funkcích a vlastnostech výkonu naleznete [v tématu TŘÍDY kolekce atl](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree::Třída CPair

Třída obsahující klíčové a hodnotové prvky.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Poznámky

Tato třída je používána metodami [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext)a [CRBTree::GetPrev](#getprev) pro přístup k prvkům klíče a hodnot uložených ve stromové struktuře.

Členové jsou následující:

|||
|-|-|
|`m_key`|Datový člen ukládání klíčový prvek.|
|`m_value`|Datový člen ukládání elementvalue.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree::~CRBTree

Destruktor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje. Volá [CRBTree::RemoveAll](#removeall) odstranit všechny prvky.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAfter

Volání této metody najít pozici prvku, který používá další dostupný klíč.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice prvku, který používá další dostupný klíč. Pokud neexistují žádné další prvky, null je vrácena.

### <a name="remarks"></a>Poznámky

Tato metoda usnadňuje procházení stromu bez nutnosti předem vypočítat hodnoty polohy.

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree::Getat

Volání této metody získat prvek na dané pozici ve stromu.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota pozice.

*key*<br/>
Proměnná, která přijímá klíč.

*Hodnotu*<br/>
Proměnná, která přijímá hodnotu.

### <a name="return-value"></a>Návratová hodnota

První dva formuláře vrátí ukazatel [CPair](#cpair_class). Třetí formulář získá klíč a hodnotu pro danou pozici.

### <a name="remarks"></a>Poznámky

Hodnotu pozice lze dříve určit voláním metody, jako je [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::GetTailPosition](#gettailposition).

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree::GetCount

Volání této metody získat počet prvků ve stromu.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků (každý klíč/hodnota pár je jeden prvek) uložené ve stromu.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree::GetheadPozice

Volání této metody získat hodnotu pozice pro prvek v čele stromu.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice prvku v čele stromu.

### <a name="remarks"></a>Poznámky

Hodnotu vrácenou pomocí lze použít s metodami, `GetHeadPosition` jako je [NAPříklad CRBTree::GetKeyAt](#getkeyat) nebo [CRBTree::GetNext](#getnext) procházet stroma a načíst hodnoty.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::GetKeyat

Volání této metody získat klíč z dané pozice ve stromu.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Hodnota pozice.

### <a name="return-value"></a>Návratová hodnota

Vrátí klíč uložený ve *stromu* pozice.

### <a name="remarks"></a>Poznámky

Pokud *pos* není platná hodnota pozice, výsledky jsou nepředvídatelné. V sestaveních ladění dojde k selhání kontrolního výrazu, pokud *se pos* rovná hodnotě NULL.

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree::GetNext

Volání této metody získat ukazatel na prvek `CRBTree` uložený v objektu a posunut pozici na další prvek.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další hodnotu [CPair](#cpair_class) ve stromu.

### <a name="remarks"></a>Poznámky

Čítač pozice *pos* je aktualizován po každém volání. Pokud načtený prvek je poslední ve stromu, *pos* je nastavena na HODNOTU NULL.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::GetNextAssoc

Volání této metody získat klíč a hodnotu prvku uloženého v mapě a posunut pozici na další prvek.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Parametr šablony určující typ klíče stromu.

*Hodnotu*<br/>
Parametr šablony určující typ hodnoty stromu.

### <a name="remarks"></a>Poznámky

Čítač pozice *pos* je aktualizován po každém volání. Pokud načtený prvek je poslední ve stromu, *pos* je nastavena na HODNOTU NULL.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::GetNextKey

Volání této metody získat klíč prvku uloženého ve stromu a posunut pozici na další prvek.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další klíč ve stromu.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální čítač *pozice, pos*. Pokud ve stromu nejsou žádné další položky, čítač pozice je nastaven na hodnotu NULL.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree::GetNextValue

Volání této metody získat hodnotu prvku uloženého ve stromu a posunut pozici na další prvek.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na další hodnotu ve stromu.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální čítač *pozice, pos*. Pokud ve stromu nejsou žádné další položky, čítač pozice je nastaven na hodnotu NULL.

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev

Volání této metody získat ukazatel na prvek `CRBTree` uložený v objektu a potom aktualizovat pozici předchozí prvek.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí hodnotu [CPair](#cpair_class) uloženou ve stromu.

### <a name="remarks"></a>Poznámky

Aktualizuje aktuální čítač *pozice, pos*. Pokud ve stromu nejsou žádné další položky, čítač pozice je nastaven na hodnotu NULL.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::GettailPosition

Volání této metody získat hodnotu pozice pro prvek na konci stromu.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pozice prvku na konci stromu.

### <a name="remarks"></a>Poznámky

Hodnotu vrácenou pomocí lze použít s metodami, `GetTailPosition` jako je [NAPříklad CRBTree::GetKeyAt](#getkeyat) nebo [CRBTree::GetPrev](#getprev) procházet stroma a načíst hodnoty.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::GetValueAt

Volání této metody načíst hodnotu uloženou `CRBTree` na dané pozici v objektu.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na hodnotu uloženou na `CRBTree` dané pozici v objektu.

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree::Jeprázdný

Volání této metody k testování objektu prázdné stromu.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je strom prázdný, jinak NEPRAVDA.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::KINARGTYPE

Typ použitý při předání klíče jako vstupní argument.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::KOUTARGTYPE

Typ použitý při vrácení klíče jako výstupního argumentu.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree::RemoveAll

Volání této metody odebrat `CRBTree` všechny prvky z objektu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Vymaže `CRBTree` objekt, uvolnění paměti používané k uložení prvků.

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree::RemoveAt

Volání této metody odebrat prvek na `CRBTree` dané pozici v objektu.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Poznámky

Odebere dvojici klíč/hodnota uloženou na zadané pozici. Paměť použitá k uložení prvku je uvolněna. POZICE odkazuje *pos* stane neplatným a zatímco POZICE jiných prvků ve stromu zůstává v platnosti, nemusí nutně zachovat stejné pořadí.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::SetValueAt

Volání této metody změnit hodnotu uloženou `CRBTree` na dané pozici v objektu.

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Čítač pozice vrácený předchozím voláním metod, jako je [NAPŘÍKLAD CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*Hodnotu*<br/>
Hodnota, kterou chcete `CRBTree` přidat k objektu.

### <a name="remarks"></a>Poznámky

Změní prvek hodnoty uložený v `CRBTree` dané pozici v objektu.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::VINARGTYPE

Typ použitý při předání hodnoty jako vstupní argument.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE

Typ použitý při předání hodnoty jako výstupní argument.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
