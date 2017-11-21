---
title: "Carray – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4087cfb584059923e4e05620c1f33d3cc11c3bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="carray-class"></a>Carray – třída
Podporuje pole, které jsou podobné C pole, ale může dynamicky snížit a růst podle potřeby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class TYPE, class ARG_TYPE = const TYPE&>  
class CArray : public CObject  
```  
  
#### <a name="parameters"></a>Parametry  
 `TYPE`  
 Parametr šablony, která určuje typ objektů, které jsou uložené v poli. `TYPE`je parametr, který je vrácen `CArray`.  
  
 `ARG` *_* `TYPE`  
 Parametr šablony, která určuje typ argumentu, který se používá pro přístup k objektům, které jsou uložené v poli. Často odkaz na `TYPE`. `ARG_TYPE`je parametr, který je předán `CArray`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CArray::CArray](#carray)|Vytvoří prázdné pole.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CArray::Add](#add)|Přidá prvek na konec pole; zvětšování pole v případě potřeby.|  
|[CArray::Append](#append)|Připojí další pole k poli; zvětšování pole v případě potřeby|  
|[CArray::Copy](#copy)|Zkopíruje jiného pole k poli; zvětšování pole v případě potřeby.|  
|[CArray::ElementAt](#elementat)|Vrátí dočasné odkaz na element ukazatele v rámci pole.|  
|[CArray::FreeExtra](#freeextra)|Uvolní všechny nevyužitou paměť nad aktuální horní mez.|  
|[CArray::GetAt](#getat)|Vrátí hodnotu v daném indexu.|  
|[CArray::GetCount](#getcount)|Získá počet elementů v toto pole.|  
|[CArray::GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může být **NULL**.|  
|[CArray::GetSize](#getsize)|Získá počet elementů v toto pole.|  
|[CArray::GetUpperBound](#getupperbound)|Vrátí největší platný index.|  
|[CArray::InsertAt](#insertat)|Vloží zadaný index elementu (nebo všechny elementy v jiném poli).|  
|[CArray::IsEmpty](#isempty)|Určuje, zda je pole prázdné.|  
|[CArray::RemoveAll](#removeall)|Odebere všechny elementy z tohoto pole.|  
|[CArray::RemoveAt](#removeat)|Odebere element na konkrétním indexu.|  
|[CArray::SetAt](#setat)|Nastaví hodnotu pro daného indexu; pole není povoleno zvětšovat.|  
|[CArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daného indexu; zvětšování pole v případě potřeby.|  
|[CArray::SetSize](#setsize)|Nastaví počet prvků mají být obsažena v toto pole.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor &#91; &#93;](#operator_at)|Nastaví nebo získá element v zadaném indexu.|  
  
## <a name="remarks"></a>Poznámky  
 Indexy pole vždy spustit na pozici 0. Můžete se rozhodnout, zda pro opravu horní mez nebo povolit pole pro rozbalit, pokud přidáte elementy za aktuální vázána. Se přidělí paměť souvisle horní mez, i když některé prvky jsou null.  
  
> [!NOTE]
>  Většinu metod, které změnit velikost `CArray` objektu, nebo přidejte elementy, aby ji používat [memcpy_s –](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) přesunout elementy. Protože se jedná o problém `memcpy_s` není kompatibilní s objekty, které vyžadují konstruktor, který má být volána. Pokud položky v `CArray` nejsou kompatibilní s `memcpy_s`, musíte vytvořit nový `CArray` příslušný formát. Pak musíte použít [CArray::Copy](#copy) a [CArray::SetAt](#setat) k naplnění nové pole, protože tyto metody použít operátor přiřazení místo `memcpy_s`.  
  
 Stejně jako u pole C, čas přístupu `CArray` indexované element konstantní a je nezávislý na velikost pole.  
  
> [!TIP]
>  Před použitím pole, použijte [SetSize](#setsize) k zahájení jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidávání elementů do pole způsobí, že se často znovu přidělit a zkopírovat. Časté opakované přidělení a kopírování jsou neefektivní a může fragmentovat paměti.  
  
 Pokud potřebujete výpis jednotlivých prvků v poli, je nutné nastavit hloubka [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objekt, který má 1 nebo větší.  
  
 Určité funkce člena třídy volání globální pomocné funkce, které je nutné upravit pro většiny použití `CArray` třídy. Podívejte se na téma [pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md) v části MFC – makra a globální prvky.  
  
 Odvození třídy pole je jako odvození seznamu.  
  
 Další informace o tom, jak používat `CArray`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## <a name="requirements"></a>Požadavky  
 `Header:`afxtempl.h  
  
##  <a name="add"></a>CArray::Add  
 Přidá nový prvek na konec pole, pole narůstají o 1.  
  
```  
INT_PTR Add(ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Parametr šablony určení typu argumentů odkazy na elementy v toto pole.  
  
 `newElement`  
 Element, který se má přidat do tohoto pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index přidaný prvek.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [SetSize](#setsize) je použito `nGrowBy` mohou být přiděleny hodnotu větší než 1, pak paměť navíc. Horní mez však bude zvýšit pouze 1.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]  
  
##  <a name="append"></a>CArray::Append  
 Volání této funkce člen přidat na konec jiné obsah jedno pole.  
  
```  
INT_PTR Append(const CArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Zdroj prvky, které je připojeno k matici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index prvního připojení prvku.  
  
### <a name="remarks"></a>Poznámky  
 Pole musí být stejného typu.  
  
 V případě potřeby **připojení** může přidělit paměť navíc, aby dokázala pojmout elementy k poli.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]  
  
##  <a name="carray"></a>CArray::CArray  
 Vytvoří prázdné pole.  
  
```  
CArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Pole zvětšování jeden element najednou.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]  
  
##  <a name="copy"></a>CArray::Copy  
 Pomocí této funkce člen kopírování prvků jedno pole do jiné.  
  
```  
void Copy(const CArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Zdroj elementy zkopírovány do pole.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člena přepsat prvky jednoho pole s prvky jiné pole.  
  
 **Kopírování** není uvolnit paměť, nicméně v případě potřeby **kopie** může přidělit paměť navíc, aby dokázala pojmout elementů zkopírovaných do pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]  
  
##  <a name="elementat"></a>CArray::ElementAt  
 Vrátí dočasné odkaz na zadaný element v rámci pole.  
  
```  
TYPE& ElementAt(INT_PTR nIndex);  
const TYPE& ElementAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na element pole.  
  
### <a name="remarks"></a>Poznámky  
 Slouží k implementaci přiřazení levé straně operátor pro pole.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [getsize –](#getsize).  
  
##  <a name="freeextra"></a>CArray::FreeExtra  
 Uvolní všechny paměť navíc, který byl přidělen při se zvětšil pole.  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nemá žádný vliv na velikost nebo horní mez pole.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetData](#getdata).  
  
##  <a name="getat"></a>CArray::GetAt  
 Vrátí pole element v zadaném indexu.  
  
```  
TYPE& GetAt(INT_PTR nIndex);  
const TYPE& GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Určení typu prvků pole parametr šablony.  
  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).  
  
### <a name="return-value"></a>Návratová hodnota  
 Element pole aktuálně v tohoto indexu.  
  
### <a name="remarks"></a>Poznámky  
 Předávání zápornou hodnotu nebo hodnotu větší než hodnoty vrácené `GetUpperBound` způsobí selhání kontrolního výrazu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]  
  
##  <a name="getcount"></a>CArray::GetCount  
 Vrátí počet prvků pole.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v poli.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení počet prvků v poli. Protože indexy jsou od nuly, velikost je větší než největší index 1. Voláním této metody bude generovat stejný výsledek jako [CArray::GetSize](#getsize) metoda.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]  
  
##  <a name="getdata"></a>CArray::GetData  
 Pomocí této funkce člen můžete získat přímý přístup k prvků v poli.  
  
```  
const TYPE* GetData() const; 
TYPE* GetData();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Určení typu prvků pole parametr šablony.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na element pole.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou k dispozici žádné elementy `GetData` vrátí hodnotu null.  
  
 Při přímý přístup k elementům pole vám může pomoci pracovat rychleji, buďte opatrní při volání metody `GetData`; případné chyby přímo provedete ovlivnit prvků pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]  
  
##  <a name="getsize"></a>CArray::GetSize  
 Vrátí velikost pole.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Protože indexy jsou od nuly, velikost je větší než největší index 1. Voláním této metody bude generovat stejný výsledek jako [CArray::GetCount](#getcount) metoda.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>CArray::GetUpperBound  
 Vrátí aktuální horní mez toto pole.  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Protože indexy pole jsou od nuly, tato funkce vrátí hodnotu 1 menší než `GetSize`.  
  
 Podmínka **(GetUpperBound)** = -1 označuje, že pole neobsahuje žádné elementy.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CArray::GetAt](#getat).  
  
##  <a name="insertat"></a>CArray::InsertAt  
 První verze součásti `InsertAt` Vloží jednu elementu (nebo více kopií elementu) na zadaný index v poli.  
  
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
 `nIndex`  
 Celé číslo index, který může být větší než hodnoty vrácené `GetUpperBound`.  
  
 `ARG_TYPE`  
 Parametr šablony určující typ elementů v toto pole.  
  
 `newElement`  
 Element umístit do tohoto pole.  
  
 `nCount`  
 Počet, který tento element musí být vložen (výchozí hodnota je 1).  
  
 `nStartIndex`  
 Celé číslo index, který může být větší než hodnoty vrácené [GetUpperBound](#getupperbound).  
  
 `pNewArray`  
 Další pole, které obsahuje prvky, který se má přidat do tohoto pole.  
  
### <a name="remarks"></a>Poznámky  
 V procesu posune (podle zvyšování index) existující element v indexu a posune až všechny elementy nad ním.  
  
 Druhá verze vloží všechny elementy z jiné `CArray` kolekce, začínající `nStartIndex` pozici.  
  
 `SetAt` Funkce, naproti tomu nahrazuje jeden element zadané pole a není posunutí žádné elementy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]  
  
##  <a name="isempty"></a>CArray::IsEmpty  
 Určuje, zda je pole prázdné.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud toto pole neobsahuje žádné elementy. jinak 0.  
  
##  <a name="operator_at"></a>CArray::operator\[\]  
 Tyto dolního indexu jsou vhodnou náhradu za [SetAt](#setat) a [GetAt](#getat) funkce.  
  
```  
TYPE& operator[](int_ptr nindex);  
const TYPE& operator[](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů v toto pole.  
  
 `nIndex`  
 Index elementu nelze přistupovat.  
  
### <a name="remarks"></a>Poznámky  
 Volá se první operátor pro pole, které nejsou **const**, mohou být použity na právo (hodnota r) nebo doleva (l-value) příkazu přiřazení. Druhá s názvem volat pro **const** pole, mohou být použity pouze na pravé straně.  
  
 Ladicí verze knihovny vyhodnotí, pokud dolní index (buď na levé nebo pravé straně příkazu přiřazení) je mimo rozsah.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]  
  
##  <a name="relocateelements"></a>CArray::RelocateElements  
 Když toto pole by měl zvětšovat a zmenšovat přemístí vyrovnávací paměť nového data.  
  
```  
template<class TYPE, class ARG_TYPE>  
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,  
    const TYPE* pData,  
    INT_PTR nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `pNewData`  
 Vyrovnávací paměť nového pole elementů.  
  
 `pData`  
 Původní pole elementů.  
  
 `nCount`  
 Počet prvků v poli starý.  
  
### <a name="remarks"></a>Poznámky  
 `pNewData`je vždy dostatečně velký pro uložení všech `pData` elementy.  
  
 [Carray –](../../mfc/reference/carray-class.md) implementace používá tato metoda zkopírovat stará data do vyrovnávací paměť nového, pokud má pole zvětšovat a zmenšovat (když [SetSize](#setsize) nebo [FreeExtra](#freeextra) se nazývají). Výchozí implementace právě zkopíruje data.  
  
 Pro pole, ve kterých element obsahující ukazatel na jednoho ze svých vlastních členů, nebo jinou strukturu obsahuje ukazatel na jeden z elementů pole: neaktualizují následující ukazatele v prostý kopií. V takovém případě můžete opravit ukazatele implementací specializace z `RelocateElements` s příslušných typů. Také jste zodpovědní za data kopírování.  
  
##  <a name="removeall"></a>CArray::RemoveAll  
 Odebere všechny elementy z tohoto pole.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud toto pole je již prázdný, funkce stále funguje.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]  
  
##  <a name="removeat"></a>CArray::RemoveAt  
 Odebere jeden či více elementů počínaje zadaným indexem v matici.  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).  
  
 `nCount`  
 Počet elementů k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 V procesu Posune dolů všechny elementy výše odebrané elementy. Se snižuje horní svázané pole, ale není volné paměti.  
  
 Pokud se pokusíte odebrat další prvky, než jsou obsaženy v poli výše odebrání bodu, pak vyhodnotí ladicí verze knihovny.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]  
  
##  <a name="setat"></a>CArray::SetAt  
 Nastaví element pole u zadaného indexu.  
  
```  
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené [GetUpperBound](#getupperbound).  
  
 `ARG_TYPE`  
 Parametr šablony určení typu používá pro odkazování na elementy pole argumentů.  
  
 `newElement`  
 Nová hodnota elementu ukládaly na zadané pozici.  
  
### <a name="remarks"></a>Poznámky  
 `SetAt`nezpůsobí pole pro růst. Použití [SetAtGrow](#setatgrow) Pokud chcete, aby pole automaticky zvětšovat.  
  
 Je nutné zajistit, že hodnota indexu představuje platnou pozici v poli. Pokud je mimo rozsah, pak vyhodnotí ladicí verze knihovny.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetAt](#getat).  
  
##  <a name="setatgrow"></a>CArray::SetAtGrow  
 Nastaví element pole u zadaného indexu.  
  
```  
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0.  
  
 `ARG_TYPE`  
 Parametr šablony určující typ elementů v poli.  
  
 `newElement`  
 Element, který se má přidat do tohoto pole. A **NULL** je povolena hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Pole zvětšování automaticky v případě potřeby (horní mez se upraví pro umístění nového elementu).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]  
  
##  <a name="setsize"></a>CArray::SetSize  
 Určuje velikost prázdný nebo stávajícímu poli; v případě potřeby přidělí paměť.  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewSize`  
 Novou velikost pole (počet elementů). Musí být větší než nebo rovna 0.  
  
 `nGrowBy`  
 Minimální počet element sloty přidělit, pokud je nutné zvýšit velikost.  
  
### <a name="remarks"></a>Poznámky  
 Pokud novou velikost je menší než původní velikost, se zkrátí pole a vydání všechny nepoužívané paměti.  
  
 Pomocí této funkce můžete nastavit velikost pole, než začnete používat pole. Pokud nepoužijete `SetSize`, přidávání elementů do pole způsobí, že se často znovu přidělit a zkopírovat. Časté opakované přidělení a kopírování jsou neefektivní a může fragmentovat paměti.  
  
 `nGrowBy` Parametr ovlivňuje přidělení interní paměť, když se pole zvětšuje. Jeho použití nikdy ovlivňuje velikost pole, podle [getsize –](#getsize) a [GetUpperBound](#getupperbound). Pokud je použita výchozí hodnota, MFC přidělí paměť způsobem, počítáno tak, že vyhnout fragmentace paměti a optimalizaci efektivity pro většině případů.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetData](#getdata).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CObArray – třída](../../mfc/reference/cobarray-class.md)   
 [Pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md)
