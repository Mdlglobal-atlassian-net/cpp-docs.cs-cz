---
title: Třída CArray
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: 3355e72c58365e97f8f3f8ce09754285f671915a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753975"
---
# <a name="carray-class"></a>Třída CArray

Podporuje pole, která jsou jako pole C, ale může dynamicky snížit a růst podle potřeby.

## <a name="syntax"></a>Syntaxe

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony, který určuje typ objektů uložených v poli. *TYP* je parametr, který `CArray`je vrácen .

*ARG_TYPE*<br/>
Parametr šablony, který určuje typ argumentu, který se používá pro přístup k objektům uloženým v poli. Často odkaz na *TYP*. *ARG_TYPE* je parametr, který `CArray`je předán .

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArray::CArray](#carray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CArray::Přidat](#add)|Přidá prvek na konec pole; v případě potřeby pole zvětší.|
|[CArray::Připojit](#append)|Připojí k poli jiné pole; v případě potřeby pole zvětšuje|
|[CArray::Kopírovat](#copy)|Zkopíruje do pole jiné pole. v případě potřeby pole zvětší.|
|[carray::elementát](#elementat)|Vrátí dočasný odkaz na ukazatel prvku v rámci pole.|
|[CArray::FreeExtra](#freeextra)|Uvolní veškerou nepoužitou paměť nad aktuální horní mez.|
|[CArray::Getat](#getat)|Vrátí hodnotu v daném indexu.|
|[CArray::GetCount](#getcount)|Získá počet prvků v tomto poli.|
|[CArray::GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může být NULL.|
|[CArray::GetSize](#getsize)|Získá počet prvků v tomto poli.|
|[CArray::GetUpperBound](#getupperbound)|Vrátí největší platný index.|
|[carray::insertat](#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) v zadaném indexu.|
|[CArray::Jeprázdný](#isempty)|Určuje, zda je pole prázdné.|
|[CArray::RemoveAll](#removeall)|Odebere všechny prvky z tohoto pole.|
|[carray::Removeat](#removeat)|Odebere prvek v určitém indexu.|
|[carray::Setat](#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[carray::Setatgrow](#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby pole zvětší.|
|[CArray::SetSize](#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor&#91;&#93;](#operator_at)|Nastaví nebo získá prvek na zadaný index.|

## <a name="remarks"></a>Poznámky

Indexy pole vždy začínají na pozici 0. Můžete se rozhodnout, zda chcete opravit horní mez nebo povolit pole rozbalit při přidání prvků za aktuální vazbu. Paměť je přidělena souvisle k horní mez, i v případě, že některé prvky jsou null.

> [!NOTE]
> Většina metod, `CArray` které změní velikost objektu nebo do něj přidají prvky, používá [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) k přesunutí prvků. To je problém, protože `memcpy_s` není kompatibilní s žádné objekty, které vyžadují konstruktoru, které mají být volány. Pokud položky `CArray` v části `memcpy_s`nejsou kompatibilní s `CArray` programem , je nutné vytvořit novou příslušnou velikost. Potom musíte použít [CArray::Copy](#copy) a [CArray::SetAt](#setat) k naplnění nového pole, protože tyto metody používají operátor přiřazení místo `memcpy_s`.

Stejně jako u pole C `CArray` je přístupová doba pro indexovaný prvek konstantní a je nezávislá na velikosti pole.

> [!TIP]
> Před použitím pole použijte [SetSize](#setsize) k vytvoření jeho velikosti a přidělení paměti pro něj. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Pokud potřebujete výpis jednotlivých prvků v poli, musíte nastavit hloubku [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objektu 1 nebo větší.

Některé členské funkce této třídy volají globální pomocné funkce, `CArray` které musí být přizpůsobeny pro většinu použití třídy. Podívejte se na téma [Pomocníky tříd kolekce](../../mfc/reference/collection-class-helpers.md) v části MFC MFC MFC MFC MFC MMacros and Globals.

Odvození třídy pole je jako odvození seznamu.

Další informace o použití `CArray`naleznete v článku [Kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray::Přidat

Přidá nový prvek na konec pole, rostoucí pole o 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ argumentů odkazujících na prvky v tomto poli.

*newElement*<br/>
Prvek, který má být přidán do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index přidaného prvku.

### <a name="remarks"></a>Poznámky

Pokud [SetSize](#setsize) byl použit `nGrowBy` s hodnotou větší než 1, pak může být přidělena další paměť. Horní mez se však zvýší pouze o 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray::Připojit

Volání této členské funkce přidat obsah jednoho pole na konec jiného.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvků, které mají být připojeny k poli.

### <a name="return-value"></a>Návratová hodnota

Index první ho připojit prvek.

### <a name="remarks"></a>Poznámky

Pole musí být stejného typu.

V případě `Append` potřeby může přidělit další paměť pro prvky připojené k poli.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray::CArray

Vytvoří prázdné pole.

```
CArray();
```

### <a name="remarks"></a>Poznámky

Pole zvětšuje jeden prvek najednou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray::Kopírovat

Tato členská funkce slouží ke kopírování prvků jednoho pole do druhého.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvků, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

Volání této členské funkce přepsat prvky jednoho pole s prvky jiného pole.

`Copy`neuvolňuje paměť; však v `Copy` případě potřeby může přidělit další paměť pro prvky zkopírované do pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>carray::elementát

Vrátí dočasný odkaz na zadaný prvek v rámci pole.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší než nebo rovno hodnotě vrácené [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek pole.

### <a name="remarks"></a>Poznámky

Používá se k implementaci operátoru přiřazení na levé straně pro pole.

### <a name="example"></a>Příklad

  Viz příklad pro [GetSize](#getsize).

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray::FreeExtra

Uvolní všechny další paměti, která byla přidělena, zatímco pole bylo pěstováno.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

Tato funkce nemá žádný vliv na velikost nebo horní mez pole.

### <a name="example"></a>Příklad

  Viz příklad pro [GetData](#getdata).

## <a name="carraygetat"></a><a name="getat"></a>CArray::Getat

Vrátí prvek pole v zadaném indexu.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků pole.

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší než nebo rovno hodnotě vrácené [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Návratová hodnota

Prvek pole aktuálně v tomto indexu.

### <a name="remarks"></a>Poznámky

Předání záporné hodnoty nebo hodnoty větší `GetUpperBound` než hodnota vrácená hodnotou bude mít za následek neúspěšnou kontrolní výraz.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray::GetCount

Vrátí počet prvků pole.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v poli.

### <a name="remarks"></a>Poznámky

Volání této metody načíst počet prvků v poli. Vzhledem k tomu, že indexy jsou založeny na nule, velikost je 1 větší než největší index. Volání této metody vygeneruje stejný výsledek jako metoda [CArray::GetSize.](#getsize)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray::GetData

Pomocí této členské funkce získat přímý přístup k prvkům v poli.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků pole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek pole.

### <a name="remarks"></a>Poznámky

Pokud nejsou k `GetData` dispozici žádné prvky, vrátí hodnotu null.

Zatímco přímý přístup k prvkům pole vám může pomoci pracovat `GetData`rychleji, buďte opatrní při volání ; všechny chyby, které provedete, přímo ovlivňují prvky pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray::GetSize

Vrátí velikost pole.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy jsou založeny na nule, velikost je 1 větší než největší index. Volání této metody vygeneruje stejný výsledek jako metoda [CArray::GetCount.](#getcount)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray::GetUpperBound

Vrátí aktuální horní mez tohoto pole.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy pole jsou `GetSize`od nuly, vrátí tato funkce hodnotu 1 menší než .

Podmínka `GetUpperBound( )` = -1 označuje, že pole neobsahuje žádné prvky.

### <a name="example"></a>Příklad

  Viz příklad [carray::GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a>carray::insertat

První verze `InsertAt` vloží jeden prvek (nebo více kopií prvku) na zadaný index v poli.

```cpp
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celého čísla, který může být `GetUpperBound`větší než hodnota vrácená .

*ARG_TYPE*<br/>
Parametr šablony určující typ prvků v tomto poli.

*newElement*<br/>
Prvek, který má být umístěn v tomto poli.

*nCount*<br/>
Počet, kolikrát by měl být tento prvek vložen (výchozí hodnota je 1).

*nStartIndex*<br/>
Integer index, který může být větší než hodnota vrácená [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Jiné pole, které obsahuje prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

V procesu posune nahoru (zvýšením indexu) existující prvek v tomto indexu a posune všechny prvky nad ním.

Druhá verze vloží všechny prvky `CArray` z jiné kolekce, počínaje pozici *nStartIndex.*

Funkce `SetAt` naopak nahradí jeden zadaný prvek pole a neposune žádné prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray::Jeprázdný

Určuje, zda je pole prázdné.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud pole neobsahuje žádné prvky; jinak 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::operátor\[\]

Tyto operátory dolního indexu jsou vhodnou náhradou za funkce [SetAt](#setat) a [GetAt.](#getat)

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v tomto poli.

*nIndex*<br/>
Index prvku, ke který má být přístup.

### <a name="remarks"></a>Poznámky

První operátor, volaný pro pole, která nejsou **const**, mohou být použity na pravé (r-hodnota) nebo vlevo (l-hodnota) příkazu přiřazení. Druhý, volal pro **const** pole, lze použít pouze na pravé straně.

Ladicí verze knihovny uplatňuje, pokud je dolní index (na levé nebo pravé straně příkazu přiřazení) mimo hranice.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray::Přemístit prvky

Přemístí data do nové vyrovnávací paměti, když by pole mělo zvětšovat nebo zmenšovat.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*pNewData*<br/>
Nová vyrovnávací paměť pro pole prvků.

*Pdata*<br/>
Staré pole prvků.

*nCount*<br/>
Počet prvků ve starém poli.

### <a name="remarks"></a>Poznámky

*pNewData* je vždy dostatečně velký, aby držel všechny *pData* prvky.

Implementace [CArray](../../mfc/reference/carray-class.md) používá tuto metodu ke kopírování starých dat do nové vyrovnávací paměti, když by se mělo pole zvětšovat nebo zmenšovat (při volání [SetSize](#setsize) nebo [FreeExtra).](#freeextra) Výchozí implementace pouze zkopíruje data.

Pro pole, ve kterém prvek obsahuje ukazatel na jeden z jeho vlastních členů nebo jiné struktury obsahuje ukazatel na jeden z prvků pole, ukazatele nejsou aktualizovány ve formátu prosté kopie. V takovém případě můžete opravit ukazatele implementací `RelocateElements` specializace s příslušnými typy. Jste také zodpovědní za kopírování dat.

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray::RemoveAll

Odebere všechny prvky z tohoto pole.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud je pole již prázdné, funkce stále funguje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>carray::Removeat

Odebere jeden nebo více prvků začínajících na zadaný index v poli.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší než nebo rovno hodnotě vrácené [GetUpperBound](#getupperbound).

*nCount*<br/>
Počet prvků odebrat.

### <a name="remarks"></a>Poznámky

V procesu posune dolů všechny prvky nad odstraněné prvky. Sníží horní mez pole, ale neuvolní paměť.

Pokud se pokusíte odebrat více prvků, než jsou obsaženy v poli nad bodem odebrání, pak ladicí verze knihovny tvrdí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>carray::Setat

Nastaví prvek pole na zadaný index.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celéčíslo, který je větší nebo roven 0 a menší než nebo rovno hodnotě vrácené [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parametr šablony určující typ argumentů použitých pro odkazování na prvky pole.

*newElement*<br/>
Hodnota nového prvku, která má být uložena na zadané pozici.

### <a name="remarks"></a>Poznámky

`SetAt`nezpůsobí, že pole zvětšovat. Pokud chcete, aby pole automaticky rostlo, použijte [SetAtGrow.](#setatgrow)

Je nutné zajistit, aby hodnota indexu představuje platnou pozici v poli. Pokud je mimo hranice, pak debug verze knihovny tvrdí.

### <a name="example"></a>Příklad

  Viz příklad pro [GetAt](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>carray::Setatgrow

Nastaví prvek pole na zadaný index.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index celého čísla, který je větší nebo roven 0.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvků v poli.

*newElement*<br/>
Prvek, který má být přidán do tohoto pole. Hodnota NULL je povolena.

### <a name="remarks"></a>Poznámky

Pole se v případě potřeby automaticky zvětší (to znamená, že horní mez je upravena tak, aby vyhovovala novému prvku).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray::SetSize

Vytvoří velikost prázdného nebo existujícího pole; v případě potřeby přidělí paměť.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNová velikost*<br/>
Nová velikost pole (počet prvků). Musí být větší než nebo rovno 0.

*nGrowBy*<br/>
Minimální počet slotů element udělit, pokud je nutné zvýšení velikosti.

### <a name="remarks"></a>Poznámky

Pokud je nová velikost menší než stará velikost, pole je zkráceno a uvolněna je všechna nevyužitá paměť.

Tato funkce slouží k nastavení velikosti pole před zahájením používání pole. Pokud nepoužijete `SetSize`, přidání prvků do pole způsobí, že často přerozděleny a zkopírovány. Časté přerozdělení a kopírování jsou neefektivní a může fragmentovat paměť.

Parametr *nGrowBy* ovlivňuje přidělení vnitřní paměti, zatímco pole roste. Jeho použití nikdy nemá vliv na velikost pole, jak je uvedeno [GetSize](#getsize) a [GetUpperBound](#getupperbound). Pokud je použita výchozí hodnota, knihovna MFC přiděluje paměť způsobem vypočteným tak, aby se zabránilo fragmentaci paměti a optimalizaci účinnosti ve většině případů.

### <a name="example"></a>Příklad

  Viz příklad pro [GetData](#getdata).

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CObArray](../../mfc/reference/cobarray-class.md)<br/>
[Pomocníci třídy kolekce](../../mfc/reference/collection-class-helpers.md)
