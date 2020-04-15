---
title: Třída CAtlArray
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 85168af654d3d63e06559486b464938b7fd90ad3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321577"
---
# <a name="catlarray-class"></a>Třída CAtlArray

Tato třída implementuje objekt pole.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ dat, která mají být uložena v poli.

*ETraits*<br/>
Kód používaný ke kopírování nebo přesouvání prvků.

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Přidat](#add)|Volání této metody přidat prvek do objektu pole.|
|[Připojit](#append)|Volání této metody přidat obsah jednoho pole na konec jiného.|
|[AssertValid](#assertvalid)|Volání této metody k potvrzení, že objekt pole je platný.|
|[CAtlArray](#catlarray)|Konstruktor|
|[~CAtlArray](#dtor)|Destruktor.|
|[Kopírovat](#copy)|Volání této metody zkopírovat prvky jednoho pole do jiného.|
|[VolnýExtra](#freeextra)|Volání této metody odebrat všechny prázdné prvky z pole.|
|[Getat (Kvat)](#getat)|Volání této metody načíst jeden prvek z objektu pole.|
|[GetCount](#getcount)|Volání této metody vrátit počet prvků uložených v poli.|
|[GetData](#getdata)|Volání této metody vrátit ukazatel na první prvek v poli.|
|[InsertArrayAt](#insertarrayat)|Volání této metody vložit jedno pole do jiného.|
|[InsertAt](#insertat)|Volání této metody vložit nový prvek (nebo více kopií prvku) do objektu pole.|
|[Isempty](#isempty)|Volání této metody k testování, pokud je pole prázdné.|
|[Removeall](#removeall)|Volání této metody odebrat všechny prvky z objektu pole.|
|[Removeat](#removeat)|Volání této metody odebrat jeden nebo více prvků z pole.|
|[Setat (Setat)](#setat)|Volání této metody nastavit hodnotu prvku v objektu pole.|
|[Setatgrow](#setatgrow)|Volání této metody nastavit hodnotu prvku v objektu pole, rozbalení pole podle potřeby.|
|[SetCount](#setcount)|Volání této metody nastavit velikost objektu pole.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor &#91;&#93;](#operator_at)|Volání tohoto operátoru vrátit odkaz na prvek v poli.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYP](#inargtype)|Datový typ, který se má použít pro přidání prvků do pole.|
|[OUTARGTYP](#outargtype)|Datový typ, který se má použít pro načítání prvků z pole.|

## <a name="remarks"></a>Poznámky

`CAtlArray`poskytuje metody pro vytváření a správu pole prvků uživatelem definovaného typu. I když je podobný standardní `CAtlArray` mj. Index pole vždy začíná na pozici 0 a horní mez může být pevná nebo povolena rozbalení při přidání nových prvků.

Pro pole s malým počtem prvků lze použít třídu [ATL CSimpleArray.](../../atl/reference/csimplearray-class.md)

`CAtlArray`úzce souvisí s `CArray` mfc třídy a bude pracovat v projektu knihovny MFC, i když bez podpory serializace.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>CAtlArray::Přidat

Volání této metody přidat prvek do objektu pole.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parametry

*Prvek*<br/>
Prvek, který má být přidán do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí index přidaného prvku.

### <a name="remarks"></a>Poznámky

Nový prvek je přidán na konec pole. Pokud není k dispozici žádný prvek, je přidán prázdný prvek; to znamená, že pole je zvětšeno ve velikosti, jako by byl přidán skutečný prvek. Pokud se operace nezdaří, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) je volána s argumentem E_OUTOFMEMORY.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray::Připojit

Volání této metody přidat obsah jednoho pole na konec jiného.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Pole připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí index prvního připojeného prvku.

### <a name="remarks"></a>Poznámky

Prvky v zadaném poli jsou přidány na konec existujícího pole. V případě potřeby bude paměť přidělena pro nové prvky.

Pole musí být stejného typu a není možné připojit pole k sobě.

V sestavení ladění ATLASSERT bude aktivována, `CAtlArray` pokud argument není platné pole nebo *pokud aSrc* odkazuje na stejný objekt. Ve verzi sestavení neplatné argumenty může vést k nepředvídatelné chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid

Volání této metody k potvrzení, že objekt pole je platný.

```
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

Pokud objekt pole není platný, ATLASSERT vyvolá kontrolní výraz. Tato metoda je k dispozici pouze v případě, _DEBUG je definována.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray

Konstruktor

```
CAtlArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje objekt pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlArray::~CAtlArray

Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny prostředky používané objektem pole.

## <a name="catlarraycopy"></a><a name="copy"></a>CAtlArray::Kopírovat

Volání této metody zkopírovat prvky jednoho pole do jiného.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Zdroj prvků ke kopírování do pole.

### <a name="remarks"></a>Poznámky

Volání této metody přepsat prvky jednoho pole s prvky jiného pole. V případě potřeby bude paměť přidělena pro nové prvky. Není možné kopírovat prvky pole pro sebe.

Pokud mají být zachovány existující obsah pole, použijte [CAtlArray::Append](#append) místo.

V sestavení ladění ATLASSERT bude aktivována, `CAtlArray` pokud existující objekt není platný, nebo pokud *aSrc* odkazuje na stejný objekt. Ve verzi sestavení neplatné argumenty může vést k nepředvídatelné chování.

> [!NOTE]
> `CAtlArray::Copy`nepodporuje pole skládající se z prvků vytvořených pomocí třídy [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra

Volání této metody odebrat všechny prázdné prvky z pole.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Poznámky

Všechny prázdné prvky jsou odebrány, ale velikost a horní mez pole zůstávají beze změny.

V sestaveních ladění atlASSERT bude aktivována, pokud catlarray objekt není platný, nebo pokud pole by překročit jeho maximální velikost.

## <a name="catlarraygetat"></a><a name="getat"></a>CAtlArray::Získat

Volání této metody načte jeden prvek z objektu pole.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Hodnota indexu prvku pole, který chcete vrátit.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na povinný prvek pole.

### <a name="remarks"></a>Poznámky

V sestavení ladění ATLASSERT bude aktivována, pokud *iElement* překročí počet prvků v poli. V sestavení verze neplatný argument může vést k nepředvídatelné chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount

Volání této metody vrátit počet prvků uložených v poli.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků uložených v poli.

### <a name="remarks"></a>Poznámky

Jako první prvek v poli je na pozici `GetCount` 0, hodnota vrácená je vždy 1 větší než největší index.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlArray::GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData

Volání této metody vrátit ukazatel na první prvek v poli.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na umístění v paměti ukládání první prvek v poli. Pokud nejsou k dispozici žádné prvky, null je vrácena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE

Datový typ, který se má použít pro přidání prvků do pole.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Volání této metody vložit jedno pole do jiného.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parametry

*iStartovat*<br/>
Index, do kterého má být pole vloženo.

*paNový*<br/>
Pole, které má být vloženo.

### <a name="remarks"></a>Poznámky

Prvky z pole *paNew* jsou zkopírovány do objektu pole, počínaje elementem *iStart*. Existující prvky pole jsou přesunuty, aby nedošlo k přepsání.

V sestaveních ladění bude aktivována ATLASSERT, pokud `CAtlArray` objekt není platný nebo pokud je ukazatel *paNew* null nebo neplatný.

> [!NOTE]
> `CAtlArray::InsertArrayAt`nepodporuje pole skládající se z prvků vytvořených pomocí třídy [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt

Volání této metody vložit nový prvek (nebo více kopií prvku) do objektu pole.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index, kde mají být vloženy prvek nebo prvky.

*Prvek*<br/>
Hodnota prvku nebo prvků, které mají být vloženy.

*nCount*<br/>
Počet prvků, které chcete přidat.

### <a name="remarks"></a>Poznámky

Vloží jeden nebo více prvků do pole, počínaje index *iElement*. Existující prvky jsou přesunuty, aby nedošlo k přepsání.

V sestavení ladění ATLASSERT bude aktivována, `CAtlArray` pokud je objekt neplatný, počet prvků, které mají být přidány, je nula nebo kombinovaný počet prvků je příliš velký pro pole obsahovat. V maloobchodnísestavení předávání neplatné parametry může způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>CAtlArray::JePrázdný

Volání této metody k testování, pokud je pole prázdné.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je pole prázdné, false otherwise.

### <a name="remarks"></a>Poznámky

Pole je řekl, aby byl prázdný, pokud neobsahuje žádné prvky. Proto i v případě, že pole obsahuje prázdné prvky, není prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::operátor []

Volání tohoto operátoru vrátit odkaz na prvek v poli.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Hodnota indexu prvku pole, který chcete vrátit.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na povinný prvek pole.

### <a name="remarks"></a>Poznámky

Provádí podobnou funkci [jako CAtlArray::GetAt](#getat). Na rozdíl od třídy [MFC CArray](../../mfc/reference/carray-class.md)tento operátor nelze použít jako náhradu za [CAtlArray::SetAt](#setat).

V sestavení ladění ATLASSERT bude aktivována, pokud *iElement* překročí celkový počet prvků v poli. V maloobchodnísestavení neplatný parametr může způsobit nepředvídatelné výsledky.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z pole.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::OdstranitVše

Volání této metody odebrat všechny prvky z objektu pole.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Odebere všechny prvky z objektu pole.

Tato metoda volá [CAtlArray::SetCount](#setcount) změnit velikost pole a následně uvolní všechny přidělené paměti.

### <a name="example"></a>Příklad

Viz příklad [catlarray::IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt

Volání této metody odebrat jeden nebo více prvků z pole.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index první prvek odebrat.

*nCount*<br/>
Počet prvků odebrat.

### <a name="remarks"></a>Poznámky

Odebere jeden nebo více prvků z pole. Všechny zbývající prvky jsou posunuty dolů. Horní mez je snížena, ale paměť není uvolněna, dokud není provedeno volání [CAtlArray::FreeExtra.](#freeextra)

V sestavení ladění ATLASSERT bude aktivována, `CAtlArray` pokud objekt není platný, nebo pokud kombinovaný součet *iElement* a *nCount* překročí celkový počet prvků v poli. V maloobchodnísestavení neplatné parametry mohou způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt

Volání této metody nastavit hodnotu prvku v objektu pole.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index směřující na prvek pole nastavit.

*Prvek*<br/>
Nová hodnota zadaného prvku.

### <a name="remarks"></a>Poznámky

V sestavení ladění ATLASSERT bude aktivována, pokud *iElement* překročí počet prvků v poli. V maloobchodnísestavení neplatný parametr může mít za následek nepředvídatelné výsledky.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlArray::GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount

Volání této metody nastavit velikost objektu pole.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parametry

*nNová velikost*<br/>
Požadovaná velikost pole.

*nGrowBy*<br/>
Hodnota slouží k určení, jak velké vyrovnávací paměti. Hodnota -1 způsobí, že interně vypočtená hodnota má být použita.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je velikost pole úspěšně velikost, false jinak.

### <a name="remarks"></a>Poznámky

Pole může být zvýšena nebo zmenšena. Pokud zvýšena, extra prázdné prvky jsou přidány do pole. Pokud se sníží, prvky s největšími indexy budou odstraněny a paměť uvolněna.

Pomocí této metody nastavte velikost pole před jeho použitím. Pokud `SetCount` se nepoužívá, proces přidávání prvků – a následné přidělení paměti provádí – sníží výkon a fragment paměti.

### <a name="example"></a>Příklad

Viz příklad [catlarray::GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow

Volání této metody nastavit hodnotu prvku v objektu pole, rozbalení pole podle potřeby.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index směřující na prvek pole nastavit.

*Prvek*<br/>
Nová hodnota zadaného prvku.

### <a name="remarks"></a>Poznámky

Nahradí hodnotu prvku, na který je odkazováno indexem. Pokud je *iElement* větší než aktuální velikost pole, pole se automaticky zvýší pomocí volání [CAtlArray::SetCount](#setcount). V sestavení ladění ATLASSERT bude aktivována, `CAtlArray` pokud objekt není platný. V maloobchodnísestavení neplatné parametry mohou způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Ukázka dynamického spotřebitele](../../overview/visual-cpp-samples.md)<br/>
[Ukázka updatePV](../../overview/visual-cpp-samples.md)<br/>
[Vzorek výběru](../../overview/visual-cpp-samples.md)<br/>
[Třída CArray](../../mfc/reference/carray-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
