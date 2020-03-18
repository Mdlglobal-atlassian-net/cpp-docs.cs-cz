---
title: CAtlArray – třída
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
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418088"
---
# <a name="catlarray-class"></a>CAtlArray – třída

Tato třída implementuje objekt Array.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parametry

*Cerebrální*<br/>
Typ dat, který bude uložen v poli.

*ETraits*<br/>
Kód použitý ke zkopírování nebo přesunutí prvků.

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Add](#add)|Voláním této metody přidáte element do objektu Array.|
|[Příloh](#append)|Voláním této metody přidáte obsah jednoho pole na konec jiného.|
|[AssertValid](#assertvalid)|Voláním této metody potvrďte, že je objekt pole platný.|
|[CAtlArray](#catlarray)|Konstruktor|
|[~ CAtlArray](#dtor)|Destruktor.|
|[Kopií](#copy)|Voláním této metody zkopírujte prvky jednoho pole do jiného.|
|[FreeExtra](#freeextra)|Voláním této metody odeberete z pole všechny prázdné prvky.|
|[GetAt](#getat)|Voláním této metody načtete jeden prvek z objektu Array.|
|[GetCount](#getcount)|Voláním této metody vrátíte počet prvků uložených v poli.|
|[GetData](#getdata)|Voláním této metody vrátíte ukazatel na první prvek v poli.|
|[InsertArrayAt](#insertarrayat)|Voláním této metody vložíte jedno pole do jiného.|
|[InsertAt](#insertat)|Zavolejte tuto metodu pro vložení nového prvku (nebo více kopií elementu) do objektu Array.|
|[IsEmpty](#isempty)|Voláním této metody otestujete, zda je pole prázdné.|
|[RemoveAll](#removeall)|Voláním této metody odeberete všechny prvky z objektu Array.|
|[Funkce RemoveAt](#removeat)|Voláním této metody odeberete jeden nebo více prvků z pole.|
|[SetAt](#setat)|Voláním této metody nastavíte hodnotu prvku v objektu Array.|
|[SetAtGrow](#setatgrow)|Voláním této metody nastavíte hodnotu prvku v objektu Array a rozbalíte pole podle potřeby.|
|[SetCount](#setcount)|Voláním této metody nastavíte velikost objektu Array.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel&#91;&#93;](#operator_at)|Voláním tohoto operátora vrátíte odkaz na prvek v poli.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do pole.|
|[OUTARGTYPE](#outargtype)|Datový typ, který má být použit pro načtení prvků z pole.|

## <a name="remarks"></a>Poznámky

`CAtlArray` poskytuje metody pro vytváření a správu pole prvků uživatelsky definovaného typu. I když se podobá standardním polím C, objekt `CAtlArray` se může dynamicky zmenšovat a zvětšovat podle potřeby. Index pole vždy začíná na pozici 0 a horní mez může být opravena nebo může být rozšířena při přidání nových prvků.

Pro pole s malým počtem prvků lze použít třídu ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) .

`CAtlArray` úzce souvisí s `CArray` třídou MFC a bude fungovat v projektu knihovny MFC, i když bez podpory serializace.

Další informace naleznete v tématu [třídy kolekcí ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll. h

##  <a name="add"></a>CAtlArray:: Add

Voláním této metody přidáte element do objektu Array.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parametry

*objekt*<br/>
Prvek, který má být přidán do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí index přidaného prvku.

### <a name="remarks"></a>Poznámky

Nový prvek je přidán na konec pole. Pokud není zadán žádný element, je přidán prázdný prvek; To znamená, že pole je zvětšeno, jako by byl přidán skutečný prvek. Pokud se operace nezdařila, je volána metoda [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) s argumentem E_OUTOFMEMORY.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>CAtlArray:: Append

Voláním této metody přidáte obsah jednoho pole na konec jiného.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Pole, které se má připojit

### <a name="return-value"></a>Návratová hodnota

Vrátí index prvního připojené elementu.

### <a name="remarks"></a>Poznámky

Prvky v zadaném poli jsou přidány na konec existujícího pole. V případě potřeby bude přidělena paměť pro přizpůsobení nových prvků.

Pole musí být stejného typu a není možné připojit pole k sobě samému.

V sestavení ladění bude ATLASSERT vyvolána, pokud argument `CAtlArray` není platným polem nebo pokud *aSrc* odkazuje na stejný objekt. V sestavení vydaných verzí můžou neplatné argumenty vést k nepředvídatelnému chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>CAtlArray::AssertValid

Voláním této metody potvrďte, že je objekt pole platný.

```
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

Pokud objekt Array není platný, ATLASSERT vyvolá kontrolní výraz. Tato metoda je k dispozici pouze v případě, že je definována _DEBUG.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>CAtlArray::CAtlArray

Konstruktor

```
CAtlArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje objekt Array.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>CAtlArray:: ~ CAtlArray

Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny prostředky používané objektem Array.

##  <a name="copy"></a>CAtlArray:: Copy

Voláním této metody zkopírujte prvky jednoho pole do jiného.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Zdroj prvků, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

Zavolejte tuto metodu pro přepsání prvků jednoho pole s prvky jiného pole. V případě potřeby bude přidělena paměť pro přizpůsobení nových prvků. Prvky pole není možné zkopírovat do sebe samé.

Pokud se má zachovat existující obsah pole, použijte místo toho [CAtlArray:: Append](#append) .

V sestavení ladění bude ATLASSERT vyvolána, pokud existující objekt `CAtlArray` není platný, nebo pokud *aSrc* odkazuje na stejný objekt. V sestavení vydaných verzí můžou neplatné argumenty vést k nepředvídatelnému chování.

> [!NOTE]
> `CAtlArray::Copy` nepodporuje pole sestávající z prvků vytvořených pomocí třídy [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>CAtlArray::FreeExtra

Voláním této metody odeberete z pole všechny prázdné prvky.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Poznámky

Všechny prázdné prvky jsou odebrány, ale velikost a horní mez pole zůstávají beze změny.

V sestavení ladění bude ATLASSERT vyvolána, pokud objekt CAtlArray není platný, nebo pokud by pole překročilo maximální velikost.

##  <a name="getat"></a>CAtlArray::GetAt

Voláním této metody načtete jeden prvek z objektu Array.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Hodnota indexu prvku pole, který se má vrátit

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na požadovaný prvek pole.

### <a name="remarks"></a>Poznámky

V sestavení ladění bude ATLASSERT vyvolána, pokud *IElement* překročí počet prvků v poli. V sestavení vydaných verzí může neplatný argument vést k nepředvídatelnému chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>CAtlArray:: GetCount

Voláním této metody vrátíte počet prvků uložených v poli.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků uložených v poli.

### <a name="remarks"></a>Poznámky

Protože první prvek v poli je na pozici 0, hodnota vrácená `GetCount` je vždy 1 větší než největší index.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray:: GetAt](#getat).

##  <a name="getdata"></a>CAtlArray:: GetData

Voláním této metody vrátíte ukazatel na první prvek v poli.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na umístění v paměti, kde je uložen první prvek v poli. Pokud nejsou k dispozici žádné prvky, je vrácena hodnota NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>CAtlArray::INARGTYPE

Datový typ, který se má použít pro přidání prvků do pole.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Voláním této metody vložíte jedno pole do jiného.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parametry

*-zahájení*<br/>
Index, na kterém má být pole vloženo.

*paNew*<br/>
Pole, které se má vložit

### <a name="remarks"></a>Poznámky

Prvky z pole *paNew* jsou zkopírovány do objektu Array, počínaje prvkem- *Start*. Existující prvky pole jsou přesunuty, aby nedocházelo k přepsání.

V sestavení ladění bude ATLASSERT vyvolána, pokud objekt `CAtlArray` není platný nebo pokud má ukazatel *paNew* hodnotu null nebo je neplatný.

> [!NOTE]
> `CAtlArray::InsertArrayAt` nepodporuje pole sestávající z prvků vytvořených pomocí třídy [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>CAtlArray::InsertAt

Zavolejte tuto metodu pro vložení nového prvku (nebo více kopií elementu) do objektu Array.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index, do kterého mají být vloženy elementy nebo elementy

*objekt*<br/>
Hodnota elementu nebo elementů, které mají být vloženy.

*nCount*<br/>
Počet prvků, které mají být přidány.

### <a name="remarks"></a>Poznámky

Vloží jeden nebo více prvků do pole, počínaje indexem *IElement*. Existující prvky jsou přesunuty, aby nedocházelo k přepsání.

V sestavení ladění bude ATLASSERT vyvolána, pokud je objekt `CAtlArray` neplatný, počet prvků, které mají být přidány, je nula nebo kombinovaný počet prvků je příliš velký, aby pole obsahovalo. V maloobchodních sestaveních může předávání neplatných parametrů způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>CAtlArray::-Empty

Voláním této metody otestujete, zda je pole prázdné.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je pole prázdné, jinak false.

### <a name="remarks"></a>Poznámky

V případě, že pole neobsahuje žádné prvky, je toto pole prázdné. Proto i v případě, že pole obsahuje prázdné prvky, není prázdné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>CAtlArray:: operator [] – operátor

Voláním tohoto operátora vrátíte odkaz na prvek v poli.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Hodnota indexu prvku pole, který se má vrátit

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na požadovaný prvek pole.

### <a name="remarks"></a>Poznámky

Provede podobnou funkci pro [CAtlArray:: GetAt](#getat). Na rozdíl od třídy MFC [CArray –](../../mfc/reference/carray-class.md)nemůže být tento operátor použit jako náhrada za [CAtlArray:: SetAt](#setat).

V sestavení ladění bude ATLASSERT vyvolána, pokud *IElement* překročí celkový počet prvků v poli. V maloobchodních sestaveních může neplatný parametr způsobovat nepředvídatelné výsledky.

##  <a name="outargtype"></a>CAtlArray::OUTARGTYPE

Datový typ, který má být použit pro načtení prvků z pole.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>CAtlArray::RemoveAll

Voláním této metody odeberete všechny prvky z objektu Array.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Odebere všechny prvky z objektu Array.

Tato metoda volá [CAtlArray:: SetCount](#setcount) pro změnu velikosti pole a následně uvolní veškerou přidělenou paměť.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray::-Empty](#isempty).

##  <a name="removeat"></a>CAtlArray:: funkce RemoveAt

Voláním této metody odeberete jeden nebo více prvků z pole.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index prvního elementu, který se má odebrat

*nCount*<br/>
Počet prvků, které mají být odebrány.

### <a name="remarks"></a>Poznámky

Odebere z pole jeden nebo více prvků. Všechny zbývající prvky se posunou dolů. Horní mez je snížena, ale paměť není uvolněna, dokud není provedeno volání [CAtlArray:: FreeExtra](#freeextra) .

V sestavení ladění bude ATLASSERT vyvolána, pokud objekt `CAtlArray` není platný, nebo pokud kombinovaný součet *IElement* a *nCount* překračuje celkový počet prvků v poli. V maloobchodních sestavách můžou neplatné parametry způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>CAtlArray::SetAt

Voláním této metody nastavíte hodnotu prvku v objektu Array.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index odkazující na prvek pole, který má být nastaven.

*objekt*<br/>
Nová hodnota zadaného elementu.

### <a name="remarks"></a>Poznámky

V sestavení ladění bude ATLASSERT vyvolána, pokud *IElement* překročí počet prvků v poli. V maloobchodních sestaveních může neplatný parametr vést k nepředvídatelným výsledkům.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray:: GetAt](#getat).

##  <a name="setcount"></a>CAtlArray::SetCount

Voláním této metody nastavíte velikost objektu Array.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Požadovaná velikost pole.

*nGrowBy*<br/>
Hodnota, pomocí které se určí, jak velký má být vyrovnávací paměť. Hodnota-1 způsobí použití interní počítané hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je úspěšně změněna velikost pole, v opačném případě false.

### <a name="remarks"></a>Poznámky

Velikost pole je možné zvětšit nebo zmenšit. Při vyšším se do pole přidá nadbytečné prázdné prvky. Pokud se snížilo, prvky s největšími indexy se odstraní a uvolní se paměť.

Tuto metodu použijte, chcete-li nastavit velikost pole před jeho použitím. Pokud se `SetCount` nepoužívá, proces přidávání prvků – a následné přidělení paměti způsobí snížení výkonu a fragmentaci paměti.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray:: GetData](#getdata).

##  <a name="setatgrow"></a>CAtlArray::SetAtGrow

Voláním této metody nastavíte hodnotu prvku v objektu Array a rozbalíte pole podle potřeby.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index odkazující na prvek pole, který má být nastaven.

*objekt*<br/>
Nová hodnota zadaného elementu.

### <a name="remarks"></a>Poznámky

Nahradí hodnotu prvku, na který odkazuje index. Pokud je *IElement* větší než aktuální velikost pole, pole se automaticky zvýší pomocí volání [CAtlArray:: SetCount](#setcount). V sestavení ladění bude ATLASSERT vyvolána, pokud je objekt `CAtlArray` neplatný. V maloobchodních sestavách můžou neplatné parametry způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Ukázka DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Ukázka UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Ukázka běžícího textu](../../overview/visual-cpp-samples.md)<br/>
[CArray – třída](../../mfc/reference/carray-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
