---
title: Carray – třída
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
ms.openlocfilehash: e97a50b2687029ddff3d946f634e145f6709aa48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557674"
---
# <a name="carray-class"></a>Carray – třída

Podporuje pole, které se podobají polím jazyka C, ale můžete dynamicky zmenšit nebo zvětšit podle potřeby.

## <a name="syntax"></a>Syntaxe

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony, který určuje typ objektů uložených v poli. *TYP* je parametr, který je vrácený `CArray`.

*ARG_TYPE*<br/>
Parametr šablony určující typ argumentu, který se používá pro přístup k objektům, které jsou uloženy v poli. Často odkaz na *typ*. *ARG_TYPE* je parametr, který je předán `CArray`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArray::CArray](#carray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CArray::Add](#add)|Přidá prvek na konec pole. v případě potřeby se zvětší pole.|
|[CArray::Append](#append)|Připojí další pole k poli; v případě potřeby roste pole|
|[CArray::Copy](#copy)|Zkopíruje jiného objektu array do pole. v případě potřeby se zvětší pole.|
|[CArray::ElementAt](#elementat)|Vrátí dočasný odkaz na ukazatel na prvek v poli.|
|[CArray::FreeExtra](#freeextra)|Uvolní všechny nevyužité paměti nad aktuální horní mez.|
|[CArray::GetAt](#getat)|Vrátí hodnotu na daném indexu.|
|[CArray::GetCount](#getcount)|Získá počet elementů v tomto poli.|
|[CArray::GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CArray::GetSize](#getsize)|Získá počet elementů v tomto poli.|
|[CArray::GetUpperBound](#getupperbound)|Vrátí největší platný index.|
|[CArray::InsertAt](#insertat)|Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).|
|[CArray::IsEmpty](#isempty)|Určuje, zda je pole prázdné.|
|[CArray::RemoveAll](#removeall)|Odebere všechny prvky z tohoto pole.|
|[CArray::RemoveAt](#removeat)|Odebere element na konkrétní indexu.|
|[CArray::SetAt](#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby se zvětší pole.|
|[CArray::SetSize](#setsize)|Nastaví počet prvků, které mají být obsažena v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[– operátor&#91;&#93;](#operator_at)|Nastaví nebo získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

Indexy pole vždy spustit na pozici 0. Můžete se rozhodnout, zda chcete opravit horní mez nebo povolit pole, které chcete rozbalit přidat prvky za aktuální vázán. Paměť je přidělena souvisle horní mez, i když některé prvky jsou null.

> [!NOTE]
>  Většina metod, které mění velikost `CArray` objektu nebo přidat prvky do ní použít [memcpy_s –](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) se mají přesunout prvky. Protože se jedná o problém `memcpy_s` není kompatibilní s objekty, které vyžadují konstruktoru, která se má volat. Pokud se položky v `CArray` nejsou kompatibilní s `memcpy_s`, musíte vytvořit nový `CArray` odpovídající velikost. Pak musíte použít [CArray::Copy](#copy) a [CArray::SetAt](#setat) k naplnění nové pole, protože tyto metody používat operátor přiřazení místo `memcpy_s`.

Stejně jako u pole jazyka C, čas přístupu `CArray` indexovaný prvek je konstantní a je nezávislý na velikost pole.

> [!TIP]
>  Před použitím pole, použijte [SetSize](#setsize) vytvoření jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidání prvků pole způsobí, že ho bude často nevyčerpané a zkopírovat. Časté realokace a kopírování jsou neefektivní a může fragmentovat paměti.

Pokud potřebujete s výpisem paměti jednotlivých prvků v poli, je nutné nastavit hloubka [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objektu na hodnotu 1 nebo větší.

Určité členské funkce třídy volání globální pomocné funkce, které je nutné upravit pro většina použití `CArray` třídy. Naleznete v tématu [pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md) v makrech MFC a Globals části.

Odvození třídy pole je stejná jako seznam odvození.

Další informace o tom, jak používat `CArray`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

##  <a name="add"></a>  CArray::Add

Přidá nový prvek na konec pole, stále se rozšiřující pole o 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr šablony určující typ argumentů odkazující na prvky v tomto poli.

*newElement*<br/>
Elementu, který chcete přidat do tohoto pole.

### <a name="return-value"></a>Návratová hodnota

Index elementu přidal.

### <a name="remarks"></a>Poznámky

Pokud [SetSize](#setsize) se používá se `nGrowBy` hodnotu větší než 1, pak paměť navíc mohou být přiděleny. Horní mez, ale zvýší pouze 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>  CArray::Append

Voláním této členské funkce přidat obsah jednoho pole za účelem jiného.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvky, které je připojeno k matici.

### <a name="return-value"></a>Návratová hodnota

Index první připojený prvek.

### <a name="remarks"></a>Poznámky

Pole musí být stejného typu.

V případě potřeby `Append` může přidělit extra paměť pro plnění prvky k poli.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>  CArray::CArray

Vytvoří prázdné pole.

```
CArray();
```

### <a name="remarks"></a>Poznámky

Pole roste současně jeden element.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>  CArray::Copy

Tuto funkci člena můžete použijte pro kopírování prvků sady jednoho pole do jiného.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Zdroj prvky, které mají být zkopírovány do pole.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce přepsat prvky sady jednoho pole prvků jiného pole.

`Copy` Nelze uvolnit paměť; Nicméně, v případě potřeby `Copy` může přidělit extra paměť pro plnění elementů zkopírovaných k poli.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>  CArray::ElementAt

Vrátí odkaz na dočasný Zadaný prvek v poli.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek pole.

### <a name="remarks"></a>Poznámky

Používá se k implementaci levé straně operátoru pro pole.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [getsize –](#getsize).

##  <a name="freeextra"></a>  CArray::FreeExtra

Uvolní všechny další paměť, která byla přidělena, zatímco se zvětšil na velikost pole.

```
void FreeExtra();
```

### <a name="remarks"></a>Poznámky

Tato funkce nemá žádný vliv na velikost nebo horní hranice pole.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetData](#getdata).

##  <a name="getat"></a>  CArray::GetAt

Vrátí prvek pole v zadaném indexu.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků pole.

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Návratová hodnota

Element pole momentálně na tomto indexu.

### <a name="remarks"></a>Poznámky

Předání zápornou hodnotu nebo hodnotu větší než hodnota vrácená `GetUpperBound` způsobí neplatnost kontrolního výrazu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>  CArray::GetCount

Vrátí počet prvků pole.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v tomto poli.

### <a name="remarks"></a>Poznámky

Voláním této metody lze načíst počet prvků v poli. Vzhledem k tomu, že indexy jsou počítány od nuly, velikost je větší než nejvyšší index 1. Voláním této metody bude generovat stejný výsledek jako [CArray::GetSize](#getsize) metody.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>  CArray::GetData

Tuto funkci člena můžete použijte k získání přímý přístup k prvkům v poli.

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

Pokud nejsou k dispozici, žádné elementy `GetData` vrátí hodnotu null.

Zatímco přímý přístup k prvkům pole můžete pracovat rychleji, buďte opatrní při volání metody `GetData`; všechny chyby, můžete provést přímo vliv na elementy vaše pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>  CArray::GetSize

Vrátí velikost pole.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že indexy jsou počítány od nuly, velikost je větší než nejvyšší index 1. Voláním této metody bude generovat stejný výsledek jako [CArray::GetCount](#getcount) metody.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>  CArray::GetUpperBound

Vrátí aktuální horní mez tohoto pole.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Poznámky

Protože pole indexy jsou počítány od nuly, tato funkce vrátí hodnotu 1 menší než `GetSize`.

Podmínka `GetUpperBound( )` = -1 znamená, že pole neobsahuje žádné elementy.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArray::GetAt](#getat).

##  <a name="insertat"></a>  CArray::InsertAt

První verze `InsertAt` vloží jeden prvek (nebo více kopií prvku) na zadaný index v poli.

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
Elementu, který chcete umístit do tohoto pole.

*nCount*<br/>
Počet pokusů, které tento prvek by měl být vložen (výchozí nastavení: 1).

*nStartIndex*<br/>
Celočíselný index, který může být větší než hodnota vrácená [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Další pole obsahující prvky, které mají být přidány do tohoto pole.

### <a name="remarks"></a>Poznámky

Probíhající, posune (zvýšením index) existující element v indexu a posune všech prvků nad ním.

Druhá verze vloží všechny prvky z jiného `CArray` kolekce počínaje *nStartIndex* pozici.

`SetAt` Funkce naproti tomu nahradí jeden prvek určeného pole a nepřesune žádné prvky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>  CArray::IsEmpty

Určuje, zda je pole prázdné.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud matice neobsahuje žádné elementy. jinak 0.

##  <a name="operator_at"></a>  CArray::operator \[\]

Tyto operátoru dolního indexu jsou vhodné náhradou za [SetAt](#setat) a [GetAt](#getat) funkce.

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků v tomto poli.

*nIndex*<br/>
Index prvku přístup.

### <a name="remarks"></a>Poznámky

Volá se, první operátor pro pole, která nejsou **const**, může být použita na pravé straně (r) nebo (l hodnota) levé straně příkazu přiřazení. Druhý, volá se pro **const** pole, může být použita pouze na pravé straně.

Ladicí verze knihovny vyhodnotí, pokud hodnota argumentu subscript (buď v levé nebo pravé straně příkazu přiřazení) je mimo rozsah.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>  CArray::RelocateElements

Když pole by měly rozšiřovat nebo zmenšovat přemístí dat vyrovnávací paměť nového.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*pNewData*<br/>
Vyrovnávací paměť nového pole prvků.

*pData*<br/>
Původní pole elementů.

*nCount*<br/>
Počet prvků v poli staré.

### <a name="remarks"></a>Poznámky

*pNewData* je vždy dostatečně velký pro uložení všech *pData* elementy.

[Carray –](../../mfc/reference/carray-class.md) implementace používá tato metoda kopírování stará data do nové vyrovnávací paměti při pole by měly rozšiřovat nebo zmenšovat (když [SetSize](#setsize) nebo [FreeExtra](#freeextra) se nazývají). Výchozí implementace právě kopíruje data.

Pro pole, ve kterých prvek obsahuje ukazatel na jeden z jeho vlastní členů nebo jiné struktuře obsahuje ukazatel na jeden z prvků pole se neaktualizují ukazatelů v jednoduché kopírování. V takovém případě můžete opravit ukazatele implementací specializací `RelocateElements` pomocí odpovídajících typů. Nesete také zodpovědnost za kopírování dat.

##  <a name="removeall"></a>  CArray::RemoveAll

Odebere všechny prvky z tohoto pole.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Pokud už je pole prázdné, tato funkce stále pracuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>  CArray::RemoveAt

Odebere jeden nebo více prvků počínaje zadaným indexem v poli.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).

*nCount*<br/>
Počet prvků, které mají odebrat.

### <a name="remarks"></a>Poznámky

Probíhající Posune dolů všechny prvky nad odebrání těchto elementů. To sníží horní mez pole, ale ne uvolnění paměti.

Pokud se pokusíte odebrat více elementů než jsou obsaženy v poli výše odebrání bodu, pak vyhodnotí ladicí verze knihovny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>  CArray::SetAt

Nastaví prvek pole v zadaném indexu.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0 a menší nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parametr šablony určující typ používá jako odkaz prvky pole argumentů.

*newElement*<br/>
Nová hodnota elementu ukládaly na zadané pozici.

### <a name="remarks"></a>Poznámky

`SetAt` nezpůsobí pole, které chcete zvětšit. Použití [SetAtGrow](#setatgrow) Pokud chcete, aby pole, které chcete automaticky zvětšovat.

Ujistěte se, že představuje hodnotu indexu platná pozice v poli. Pokud je mimo rozsah, pak vyhodnotí ladicí verze knihovny.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetAt](#getat).

##  <a name="setatgrow"></a>  CArray::SetAtGrow

Nastaví prvek pole v zadaném indexu.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Celočíselný index, který je větší než nebo rovna 0.

*ARG_TYPE*<br/>
Parametr šablony určující typ prvků v poli.

*newElement*<br/>
Elementu, který chcete přidat do tohoto pole. Je povolena hodnota NULL.

### <a name="remarks"></a>Poznámky

Pole se automaticky zvětší v případě potřeby (to znamená, horní mez objektů je upravena podle nového prvku posouvají).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>  CArray::SetSize

Vytvoří velikost existující nebo prázdné pole. přidělí paměť v případě potřeby.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Nová velikost pole (počet prvků). Musí být větší než nebo rovna 0.

*nGrowBy*<br/>
Minimální počet slotů element přidělit, pokud je nutné zvýšit velikost.

### <a name="remarks"></a>Poznámky

Pokud nová velikost je menší než původní velikost, pole jsou oříznuté a všechny nevyužité paměti se uvolní.

Pomocí této funkce můžete nastavit velikost vašeho pole, než začnete používat pole. Pokud nepoužijete `SetSize`, přidání prvků pole způsobí, že ho bude často nevyčerpané a zkopírovat. Časté realokace a kopírování jsou neefektivní a může fragmentovat paměti.

*NGrowBy* parametr ovlivňuje přidělení vnitřní paměti, zatímco roste pole. Jeho použití nikdy ovlivňuje velikost pole, jak je hlásí [getsize –](#getsize) a [GetUpperBound](#getupperbound). Pokud je použita výchozí hodnota, MFC přidělí paměť způsobem vypočítat vyhnout fragmentace paměti a zajištění optimální efektivity většině případů.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetData](#getdata).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC shromažďování](../../visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)<br/>
[Pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md)
