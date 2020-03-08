---
title: CArray – – třída
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
ms.openlocfilehash: f82dbf7dce2e14bf760bb76d23d23f667797ee0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874508"
---
# <a name="carray-class"></a>CArray – – třída

Podporuje pole, která jsou jako pole jazyka C, ale mohou se dynamicky snižovat a zvětšovat podle potřeby.

## <a name="syntax"></a>Syntaxe

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parametry

*TEXTOVÝ*<br/>
Parametr šablony, který určuje typ objektů uložených v poli. *Typ* je parametr, který vrací `CArray`.

*ARG_TYPE*<br/>
Parametr šablony, který určuje typ argumentu, který se používá pro přístup k objektům uloženým v poli. Často se jedná o odkaz na *typ*. *ARG_TYPE* je parametr, který se předává do `CArray`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArray –:: CArray –](#carray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CArray –:: Add](#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CArray –:: Append](#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CArray –:: Copy](#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CArray –:: ElementAt](#elementat)|Vrátí dočasný odkaz na ukazatel elementu v rámci pole.|
|[CArray –:: FreeExtra](#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CArray –:: GetAt](#getat)|Vrátí hodnotu v daném indexu.|
|[CArray –:: GetCount](#getcount)|Získá počet prvků v tomto poli.|
|[CArray –:: GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CArray –:: GetSize](#getsize)|Získá počet prvků v tomto poli.|
|[CArray –:: GetUpperBound](#getupperbound)|Vrátí největší platný index.|
|[CArray –:: InsertAt](#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CArray –::-Empty](#isempty)|Určuje, zda je pole prázdné.|
|[CArray –:: RemoveAll](#removeall)|Odebere všechny prvky z tohoto pole.|
|[CArray –:: funkce RemoveAt](#removeat)|Odebere prvek v konkrétním indexu.|
|[CArray –:: SetAt](#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CArray –:: SetAtGrow](#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CArray –:: SetSize](#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[podnikatel&#91;&#93;](#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

Indexy polí vždy začínají na pozici 0. Můžete rozhodnout, zda chcete opravit horní mez, nebo povolit, aby se pole rozšířilo při přidávání prvků za aktuální vazbou. Paměť je rozdělena do horní meze, a to i v případě, že některé prvky mají hodnotu null.

> [!NOTE]
>  Většina metod, které mění velikost objektu `CArray` nebo přidává prvky do něj, používá [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) k přesunu prvků. Jedná se o problém, protože `memcpy_s` není kompatibilní s žádnými objekty, které vyžadují volání konstruktoru. Pokud nejsou položky v `CArray` kompatibilní s `memcpy_s`, je nutné vytvořit novou `CArray` příslušné velikosti. Pak je nutné použít [CArray –:: Copy](#copy) a [CArray –:: SetAt](#setat) k naplnění nového pole, protože tyto metody používají operátor přiřazení namísto `memcpy_s`.

Stejně jako u pole C je doba přístupu indexovaného elementu `CArray` konstantní a je nezávislá na velikosti pole.

> [!TIP]
>  Před použitím pole použijte příkaz [setSize](#setsize) k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Pokud potřebujete výpis paměti jednotlivých prvků v poli, je nutné nastavit hloubku objektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) na hodnotu 1 nebo větší.

Některé členské funkce této třídy volají funkce globálních pomocných funkcí, které je nutné přizpůsobit pro většinu použití třídy `CArray`. V části makra knihovny MFC a části Globals naleznete informace o pomocníkech [třídy kolekce](../../mfc/reference/collection-class-helpers.md) tématu.

Odvození třídy pole je podobné odvození seznamu.

Další informace o tom, jak používat `CArray`, najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl. h

##  <a name="add"></a>CArray –:: Add

Přidá nový prvek na konec pole a zvětšuje pole o 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ argumentů odkazujících na prvky v tomto poli.

*newElement*<br/>
Prvek, který má být přidán do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index přidaného elementu.

### <a name="remarks"></a>Poznámky

Pokud byla funkce [setSize](#setsize) použita s hodnotou `nGrowBy` větší než 1, může být přidělena další paměť. Horní hranice se ale zvýší jenom o 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>CArray –:: Append

Zavolejte tuto členskou funkci pro přidání obsahu jednoho pole na konec jiného.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvků, které mají být připojeny k poli.

### <a name="return-value"></a>Návratová hodnota

Index prvního připojené elementu.

### <a name="remarks"></a>Poznámky

Pole musí být stejného typu.

V případě potřeby může `Append` přidělit dodatečnou paměť pro přizpůsobení prvků, které jsou připojeny k poli.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>CArray –:: CArray –

Vytvoří prázdné pole.

```
CArray();
```

### <a name="remarks"></a>Poznámky

Pole rozroste jeden prvek po druhém.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>CArray –:: Copy

Tuto členskou funkci použijte ke zkopírování prvků jednoho pole do jiného.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvků, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

Zavolejte tuto členskou funkci pro přepsání prvků jednoho pole s prvky jiného pole.

`Copy` nemá volnou paměť. v případě potřeby ale `Copy` může přidělit dodatečnou paměť pro přizpůsobení prvků zkopírovaných do pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>CArray –:: ElementAt

Vrátí dočasný odkaz na určený prvek v rámci pole.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší nebo roven nule a menší nebo roven hodnotě vrácené funkcí [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek pole.

### <a name="remarks"></a>Poznámky

Slouží k implementaci operátoru přiřazení na levé straně pro pole.

### <a name="example"></a>Příklad

  Podívejte se na příklad [GetSize](#getsize).

##  <a name="freeextra"></a>CArray –:: FreeExtra

Uvolní veškerou dodatečnou paměť, která byla přidělena v době, kdy bylo pole vypěstováno.

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

Tato funkce nemá žádný vliv na velikost nebo horní mez pole.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetData](#getdata).

##  <a name="getat"></a>CArray –:: GetAt

Vrátí prvek pole v zadaném indexu.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TEXTOVÝ*<br/>
Parametr šablony určující typ prvků pole.

*nIndex*<br/>
Celočíselný index, který je větší nebo roven nule a menší nebo roven hodnotě vrácené funkcí [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Návratová hodnota

Prvek pole, který je aktuálně v tomto indexu.

### <a name="remarks"></a>Poznámky

Předáním záporné hodnoty nebo hodnoty větší než hodnota vrácená `GetUpperBound` dojde k selhání kontrolního výrazu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>CArray –:: GetCount

Vrátí počet prvků pole.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v poli.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete počet prvků v poli. Vzhledem k tomu, že indexy jsou založené na nule, je velikost 1 větší než největší index. Volání této metody vytvoří stejný výsledek jako metoda [CArray –:: GetSize](#getsize) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>CArray –:: GetData

Pomocí této členské funkce získáte přímý přístup k prvkům v poli.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parametry

*TEXTOVÝ*<br/>
Parametr šablony určující typ prvků pole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek pole.

### <a name="remarks"></a>Poznámky

Pokud nejsou k dispozici žádné prvky, `GetData` vrátí hodnotu null.

Přímý přístup k prvkům pole vám může přispět k rychlejší práci, při volání `GetData`buďte opatrní. všechny chyby, které přímo provedete, ovlivňují prvky pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>CArray –:: GetSize

Vrátí velikost pole.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy jsou založené na nule, je velikost 1 větší než největší index. Volání této metody vytvoří stejný výsledek jako metoda [CArray –:: GetCount](#getcount) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>CArray –:: GetUpperBound

Vrátí aktuální horní mez tohoto pole.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy polí jsou založené na nule, tato funkce vrátí hodnotu 1 menší než `GetSize`.

Podmínka `GetUpperBound( )` =-1 označuje, že pole neobsahuje žádné prvky.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArray –:: GetAt](#getat).

##  <a name="insertat"></a>CArray –:: InsertAt

První verze `InsertAt` vloží jeden prvek (nebo více kopií elementu) do zadaného indexu v poli.

```
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
Celočíselný index, který může být větší než hodnota vrácená `GetUpperBound`.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvků v tomto poli.

*newElement*<br/>
Prvek, který má být umístěn v tomto poli.

*nCount*<br/>
Počet, kolikrát by měl být tento prvek vložen (výchozí hodnota je 1).

*nStartIndex*<br/>
Celočíselný index, který může být větší než hodnota vrácená funkcí [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Jiné pole obsahující prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

V tomto procesu se posune nahoru (zvýšením indexu) stávajícího elementu v tomto indexu a posune všechny prvky nad ním.

Druhá verze vloží všechny prvky z jiné kolekce `CArray`, počínaje na pozici *nStartIndex* .

Funkce `SetAt`, na rozdíl od, nahrazuje jeden zadaný prvek pole a nepřesouvá žádné prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>CArray –::-Empty

Určuje, zda je pole prázdné.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud pole neobsahuje žádné elementy; v opačném případě 0.

##  <a name="operator_at"></a>CArray –:: operator \[\]

Tyto operátory dolního indexu představují pohodlný náhradu za funkce [SetAt](#setat) a [GetAt](#getat) .

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TEXTOVÝ*<br/>
Parametr šablony určující typ prvků v tomto poli.

*nIndex*<br/>
Index prvku, který se má použít

### <a name="remarks"></a>Poznámky

První operátor, který je volán pro pole, která nejsou **const**, lze použít buď na pravé straně (r-hodnota), nebo na levé (l-value) příkazu přiřazení. Druhý, volaný pro pole **const** , lze použít pouze na pravé straně.

Ladicí verze knihovny vyhodnotí, pokud je dolní index (buď na levé nebo pravé straně příkazu přiřazení) mimo hranice.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>CArray –:: RelocateElements

Přemístí data do nové vyrovnávací paměti, pokud by pole mělo zvětšit nebo zmenšit.

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

*pData*<br/>
Staré pole prvků.

*nCount*<br/>
Počet prvků ve starém poli.

### <a name="remarks"></a>Poznámky

*pNewData* je vždy dostatečně velký pro uložení všech prvků *PDATA* .

Implementace [CArray –](../../mfc/reference/carray-class.md) používá tuto metodu ke zkopírování starých dat do nové vyrovnávací paměti, pokud by pole mělo zvětšit nebo zmenšit (při volání metody [setSize](#setsize) nebo [FreeExtra](#freeextra) ). Výchozí implementace pouze kopíruje data.

Pro pole, ve kterých prvek obsahuje ukazatel na jeden z vlastních členů nebo jiná struktura obsahuje ukazatel na jeden z prvků pole, nejsou ukazatelé aktualizovány v prostém kopírování. V takovém případě můžete opravit ukazatele implementací specializace `RelocateElements` s příslušnými typy. Zodpovídáte také za kopírování dat.

##  <a name="removeall"></a>CArray –:: RemoveAll

Odebere všechny prvky z tohoto pole.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud je pole již prázdné, funkce stále funguje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>CArray –:: funkce RemoveAt

Odebere jeden nebo více prvků začínajících zadaným indexem v poli.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší nebo roven nule a menší nebo roven hodnotě vrácené funkcí [GetUpperBound](#getupperbound).

*nCount*<br/>
Počet prvků, které mají být odebrány.

### <a name="remarks"></a>Poznámky

V tomto procesu posune dolů všechny prvky nad odebranými prvky. Snižuje horní mez pole, ale neuvolní paměť.

Pokud se pokusíte odebrat více prvků, než jsou obsaženy v poli nad bodem odebrání, pak ladicí verze v knihovně vyhodnotí výrazy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>CArray –:: SetAt

Nastaví prvek pole na zadaném indexu.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší nebo roven nule a menší nebo roven hodnotě vrácené funkcí [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parametr šablony určující typ argumentů použitých pro odkazování na prvky pole.

*newElement*<br/>
Hodnota nového prvku, která má být uložena na zadané pozici.

### <a name="remarks"></a>Poznámky

`SetAt` nezpůsobí, že pole bude zvětšeno. Použijte [SetAtGrow](#setatgrow) , pokud chcete, aby se pole automaticky zvětšoval.

Je nutné zajistit, aby hodnota indexu představovala platnou pozici v poli. Pokud je mimo rozsah, ladicí verze vyhodnotí knihovnu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetAt](#getat).

##  <a name="setatgrow"></a>CArray –:: SetAtGrow

Nastaví prvek pole na zadaném indexu.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší nebo roven 0.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvků v poli.

*newElement*<br/>
Prvek, který má být přidán do tohoto pole. Hodnota NULL je povolena.

### <a name="remarks"></a>Poznámky

V případě potřeby se pole zvětšuje automaticky (to znamená, že horní mez je upravena tak, aby vyhovovala novému elementu).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>CArray –:: SetSize

Určuje velikost prázdného nebo existujícího pole. v případě potřeby přidělí paměť.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Nová velikost pole (počet prvků). Musí být větší než nebo rovno 0.

*nGrowBy*<br/>
Minimální počet slotů pro prvky, které mají být přiděleny, je-li nutné zvětšit velikost.

### <a name="remarks"></a>Poznámky

Pokud je nová velikost menší než stará, pole se zkrátí a uvolní se veškerá nevyužitá paměť.

Pomocí této funkce můžete nastavit velikost pole před tím, než začnete používat pole. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Parametr *nGrowBy* má vliv na přidělení interní paměti v době, kdy se pole zvětšuje. Jeho použití nikdy nemá vliv na velikost pole hlášené pomocí [GetSize](#getsize) a [GetUpperBound](#getupperbound). Pokud je použita výchozí hodnota, knihovna MFC přidělí paměť způsobem, který je vypočítán, aby nedocházelo k fragmentaci paměti a optimalizace efektivity ve většině případů.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetData](#getdata).

## <a name="see-also"></a>Viz také

[Ukázka MFC – shromáždit](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)<br/>
[Pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md)
