---
title: Catlarray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c08387d5c1a2a9b9b757bab7a8112783a3810065
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097793"
---
# <a name="catlarray-class"></a>Catlarray – třída

Tato třída implementuje objekt typu pole.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ dat uložených v poli.

*ETraits*<br/>
Kód použitý má zkopírovat nebo přesunout prvky.

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Add](#add)|Voláním této metody lze přidat element do objektu array.|
|[Připojení](#append)|Voláním této metody lze přidat na konec jiné obsah jednoho pole.|
|[AssertValid](#assertvalid)|Volejte tuto metodu za účelem potvrzení, že objekt pole je platný.|
|[CAtlArray](#catlarray)|Konstruktor|
|[~ Catlarray –](#dtor)|Destruktor.|
|[kopírování](#copy)|Volejte tuto metodu pro zkopírování prvků z jednoho pole do jiného.|
|[FreeExtra](#freeextra)|Voláním této metody lze odebrat všechny prázdné prvky z pole.|
|[GetAt](#getat)|Volejte tuto metodu za účelem načtení jeden element z objektu array.|
|[GetCount](#getcount)|Voláním této metody vrátí počet prvků uložených v poli.|
|[GetData](#getdata)|Voláním této metody vrátí ukazatel na první prvek v poli.|
|[InsertArrayAt](#insertarrayat)|Voláním této metody lze vložit jednoho pole do jiného.|
|[InsertAt](#insertat)|Volejte tuto metodu za účelem vkládání nového elementu (nebo více kopií prvku) do objektu array.|
|[IsEmpty](#isempty)|Volejte tuto metodu za účelem testování, pokud je pole prázdné.|
|[RemoveAll](#removeall)|Voláním této metody lze odebrat všechny prvky z objektu array.|
|[RemoveAt](#removeat)|Volejte tuto metodu za účelem odebrání jednoho nebo více prvků pole.|
|[SetAt](#setat)|Voláním této metody nastavte hodnotu prvku v objektu array.|
|[SetAtGrow](#setatgrow)|Voláním této metody nastavte hodnotu prvku v objektu array, rozbalení pole podle potřeby.|
|[SetCount](#setcount)|Voláním této metody lze nastavit velikost objektu array.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[– operátor&#91;&#93;](#operator_at)|Volání tento operátor vrací odkaz na prvek v poli.|  

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků pole.|
|[OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z pole.|

## <a name="remarks"></a>Poznámky

`CAtlArray` poskytuje metody pro vytváření a správu pole prvků uživatelem definovaného typu. Ačkoli standardní polím jazyka C, podobně jako `CAtlArray` objektu můžete dynamicky zmenšit nebo zvětšit podle potřeby. Index pole je vždy začíná na pozici 0 a horní mez pevnou, nebo můžou rostoucí nové prvky jsou přidány.

Pro pole s malý počet elementů třídy ATL [csimplearray –](../../atl/reference/csimplearray-class.md) lze použít.

`CAtlArray` úzce souvisí s MFC `CArray` třídy a bude fungovat v projektu knihovny MFC, i když spolu bez podpory serializace.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="add"></a>  CAtlArray::Add

Voláním této metody lze přidat element do objektu array.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parametry

*– Element*<br/>
Elementu, který chcete přidat do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí index elementu přidané hodnoty.

### <a name="remarks"></a>Poznámky

Nový prvek přidán na konec pole. Pokud žádný element je zadaný prázdný element přidá; To znamená, že pole je zvýšit velikost jakoby skutečný element byl přidán. Pokud se operace nezdaří, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) je volána s argumentem E_OUTOFMEMORY.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>  CAtlArray::Append

Voláním této metody lze přidat na konec jiné obsah jednoho pole.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Pole, které chcete připojit.

### <a name="return-value"></a>Návratová hodnota

Vrátí index první připojený prvek.

### <a name="remarks"></a>Poznámky

Prvky v zadané pole se přidávají na konci existujícího pole. V případě potřeby se tak, aby vyhovovaly nové prvky přidělena paměť.

Pole musí být stejného typu a není možné přidat pole na sebe sama.

V sestavení ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` argument není platné pole nebo, pokud *aSrc* odkazuje na stejný objekt. V sestaveních pro vydání může způsobit nepředvídatelné chování. neplatné argumenty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>  CAtlArray::AssertValid

Volejte tuto metodu za účelem potvrzení, že objekt pole je platný.

```
void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

Pokud se objekt pole není platný, ATLASSERT vyvolá kontrolní výraz. Tato metoda je k dispozici pouze v případě, že je definován _DEBUG.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>  CAtlArray::CAtlArray

Konstruktor

```
CAtlArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje objekt array.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>  Catlarray –:: ~ catlarray –

Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny prostředky používané objektu array.

##  <a name="copy"></a>  CAtlArray::Copy

Volejte tuto metodu pro zkopírování prvků z jednoho pole do jiného.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Zdroj prvků ke zkopírování do pole.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu přepsat prvky sady jednoho pole prvků jiného pole. V případě potřeby se tak, aby vyhovovaly nové prvky přidělena paměť. Není možné pro kopírování prvků pole na sebe sama.

Pokud stávající obsah pole se mají uchovávat, použijte [CAtlArray::Append](#append) místo.

V sestavení ladění, bude-li vyvolána ATLASSERT existující `CAtlArray` objekt není platný, nebo pokud *aSrc* odkazuje na stejný objekt. V sestaveních pro vydání může způsobit nepředvídatelné chování. neplatné argumenty.

> [!NOTE]
> `CAtlArray::Copy` nepodporuje pole skládající se z prvků vytvořených pomocí [CAutoPtr](../../atl/reference/cautoptr-class.md) třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>  CAtlArray::FreeExtra

Voláním této metody lze odebrat všechny prázdné prvky z pole.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Poznámky

Všechny prázdné prvky jsou odebrány, ale velikost a dolní mez pole zůstanou beze změny.

V sestavení ladění bude vyvolána ATLASSERT catlarray – objekt není platný nebo pokud pole by být delší než maximální velikost.

##  <a name="getat"></a>  CAtlArray::GetAt

Volání, že tuto metodu za účelem načte jeden element z objektu array.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Hodnota indexu elementu pole k vrácení.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na prvek povinné pole.

### <a name="remarks"></a>Poznámky

V sestavení ladění, bude-li vyvolána ATLASSERT *iElement* překračuje počet prvků v poli. V sestaveních pro vydání neplatný argument může být nepředvídatelné chování.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>  CAtlArray::GetCount

Voláním této metody vrátí počet prvků uložených v poli.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků uložených v poli.

### <a name="remarks"></a>Poznámky

Jako první prvek v poli je na pozici 0, hodnoty vrácené `GetCount` je vždy 1 větší než nejvyšší index.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray::GetAt](#getat).

##  <a name="getdata"></a>  CAtlArray::GetData

Voláním této metody vrátí ukazatel na první prvek v poli.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na umístění v paměti ukládání první prvek v poli. Pokud nejsou k dispozici žádné elementy, vrátí se hodnota NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>  CAtlArray::INARGTYPE

Datový typ pro použití při přidávání prvků pole.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt

Voláním této metody lze vložit jednoho pole do jiného.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parametry

*iStart*<br/>
Index, ve kterém má být vložen pole.

*paNew*<br/>
Pole, která se má vložit.

### <a name="remarks"></a>Poznámky

Prvky z pole *paNew* jsou zkopírovány do objektu pole, počínaje element *iStart*. Stávající prvky pole se přesouvají na vyhnout přepsání.

V sestavení ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt není platný, nebo pokud *paNew* je ukazatel NULL nebo je neplatný.

> [!NOTE]
> `CAtlArray::InsertArrayAt` nepodporuje pole skládající se z prvků vytvořených pomocí [CAutoPtr](../../atl/reference/cautoptr-class.md) třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>  CAtlArray::InsertAt

Volejte tuto metodu za účelem vkládání nového elementu (nebo více kopií prvku) do objektu array.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index, kde prvek nebo prvky mají být vloženy.

*– Element*<br/>
Hodnota elementu nebo prvků, které mají být vloženy.

*nCount*<br/>
Počet prvků, které mají přidat.

### <a name="remarks"></a>Poznámky

Vloží jednu nebo více prvků do pole, počínaje indexem *iElement*. Stávající elementy budou přesunuty do vyhnout přepsání.

V sestavení ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt je neplatný, počet prvků, které mají být přidány je nulový nebo je příliš velká pro pole tak, aby obsahovala souhrnný počet prvků. V prodejní buildy předáním neplatné parametry může způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>  CAtlArray::IsEmpty

Volejte tuto metodu za účelem testování, pokud je pole prázdné.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud pole je prázdné, jinak hodnota false.

### <a name="remarks"></a>Poznámky

Pole je označen jako prázdný, pokud neobsahuje žádné elementy. Proto i když pole obsahuje prázdné prvky, není prázdný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>  [] CAtlArray::operator

Volání tento operátor vrací odkaz na prvek v poli.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Hodnota indexu elementu pole k vrácení.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na prvek povinné pole.

### <a name="remarks"></a>Poznámky

Podobně jako funkce, která se provede [CAtlArray::GetAt](#getat). Na rozdíl od třídy knihovny MFC [carray –](../../mfc/reference/carray-class.md), tento operátor nelze použít jako náhradu [CAtlArray::SetAt](#setat).

V sestavení ladění, bude-li vyvolána ATLASSERT *iElement* překročí celkový počet prvků v poli. V prodejní buildy neplatný parametr může způsobit nepředvídatelné výsledky.

##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE

Datový typ použitý pro získání prvky z pole.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>  CAtlArray::RemoveAll

Voláním této metody lze odebrat všechny prvky z objektu array.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Poznámky

Odebere všechny prvky objektu pole.

Tato metoda volá [CAtlArray::SetCount](#setcount) ke změně velikosti pole a následně uvolní všechny přidělené paměti.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray::IsEmpty](#isempty).

##  <a name="removeat"></a>  CAtlArray::RemoveAt

Volejte tuto metodu za účelem odebrání jednoho nebo více prvků pole.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index prvního prvku odebrat.

*nCount*<br/>
Počet prvků, které mají odebrat.

### <a name="remarks"></a>Poznámky

Odebere jeden nebo více prvků z pole. Všechny zbývající prvky posunuty. Horní mez je snížen, ale není paměť uvolněna až do volání [CAtlArray::FreeExtra](#freeextra) tvoří.

V sestavení ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt není platný, nebo pokud celkový počet *iElement* a *nCount* překročí celkový počet prvků v poli. Neplatné parametry může v prodejní buildy, způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>  CAtlArray::SetAt

Voláním této metody nastavte hodnotu prvku v objektu array.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index odkazuje na element pole nastavení.

*– Element*<br/>
Nová hodnota zadaného prvku.

### <a name="remarks"></a>Poznámky

V sestavení ladění, bude-li vyvolána ATLASSERT *iElement* překračuje počet prvků v poli. V prodejní buildy neplatný parametr může vést k nepředvídatelným výsledkům.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray::GetAt](#getat).

##  <a name="setcount"></a>  CAtlArray::SetCount

Voláním této metody lze nastavit velikost objektu array.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Požadovaná velikost pole.

*nGrowBy*<br/>
Hodnota umožňuje určit, jak velký, aby vyrovnávací paměti. Hodnota -1 způsobí, že interně vypočtená hodnota má být použit.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud je pole úspěšně, jehož velikost byla změněna, false, jinak.

### <a name="remarks"></a>Poznámky

Pole může být zvýší nebo sníží velikosti. Je-li zvýšit, velmi prázdné prvky jsou přidány do pole. Pokud sníží, odstraní prvky s největší indexy a paměť uvolněna.

Tuto metodu použijte k nastavení velikosti pole před jeho použitím. Pokud `SetCount` nepoužívá, proces přidávání prvků – a provést přidělení paměti následné – sníží výkon, který se fragment paměti.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlArray::GetData](#getdata).

##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow

Voláním této metody nastavte hodnotu prvku v objektu array, rozbalení pole podle potřeby.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Index odkazuje na element pole nastavení.

*– Element*<br/>
Nová hodnota zadaného prvku.

### <a name="remarks"></a>Poznámky

Nahradí hodnota elementu, na které odkazuje index. Pokud *iElement* je větší než aktuální velikost pole, pole automaticky navýšena prostřednictvím volání do [CAtlArray::SetCount](#setcount). V sestavení ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt není platný. Neplatné parametry může v prodejní buildy, způsobit nepředvídatelné výsledky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka MMXSwarm](../../visual-cpp-samples.md)<br/>
[Příklad DynamicConsumer](../../visual-cpp-samples.md)<br/>
[Příklad UpdatePV](../../visual-cpp-samples.md)<br/>
[Výběr ukázky](../../visual-cpp-samples.md)<br/>
[CArray – třída](../../mfc/reference/carray-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
