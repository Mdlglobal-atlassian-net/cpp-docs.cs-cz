---
title: "Třída CAtlArray | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ffebf8289b7c1eb5ccaae5a6b6a5f2a3f939cbb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlarray-class"></a>CAtlArray – třída
Tato třída implementuje objekt array.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```  
  
#### <a name="parameters"></a>Parametry  
 *E*  
 Typ dat se neukládají v poli.  
  
 *ETraits*  
 Kód používaný k zkopírovat nebo přesunout elementy.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Přidat](#add)|Voláním této metody lze přidat element do objekt array.|  
|[Připojit](#append)|Voláním této metody lze přidat na konec jiné obsah jedno pole.|  
|[AssertValid](#assertvalid)|Volejte tuto metodu za účelem potvrzení, že je platný objekt array.|  
|[CAtlArray](#catlarray)|Konstruktor|  
|[~ CAtlArray](#dtor)|Destruktor.|  
|[Kopírování](#copy)|Volejte tuto metodu pro kopírování prvků jedno pole do jiného.|  
|[FreeExtra](#freeextra)|Voláním této metody lze odebrat všechny prázdné prvky z pole.|  
|[GetAt](#getat)|Volejte tuto metodu za účelem načtení jeden element z objektu pole.|  
|[GetCount –](#getcount)|Volejte tuto metodu za účelem vrátí počet prvků, které jsou uložené v poli.|  
|[GetData](#getdata)|Volejte tuto metodu vrátit ukazatel na první prvek v poli.|  
|[InsertArrayAt](#insertarrayat)|Volejte tuto metodu za účelem vložení do jiné jedno pole.|  
|[InsertAt](#insertat)|Volejte tuto metodu za účelem vložení nového elementu (nebo více kopií elementu) do pole objektu.|  
|[IsEmpty –](#isempty)|Volejte tuto metodu za účelem testování, je-li pole prázdné.|  
|[RemoveAll](#removeall)|Voláním této metody lze odebrat všechny elementy z objektu pole.|  
|[RemoveAt](#removeat)|Volejte tuto metodu za účelem odeberte jeden či více elementů z pole.|  
|[SetAt](#setat)|Volejte tuto metodu a nastavit hodnotu elementu v objektu pole.|  
|[SetAtGrow](#setatgrow)|Volejte tuto metodu a nastavit hodnotu elementu v objektu pole, rozšíření pole podle potřeby.|  
|[SetCount](#setcount)|Volejte tuto metodu a nastavit velikost pole objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor &#91; &#93;](#operator_at)|Volání tento operátor vrací odkaz na element v poli.|  

  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[INARGTYPE](#inargtype)|Datový typ pro použití při přidávání elementů do pole.|  
|[OUTARGTYPE](#outargtype)|Datový typ pro načítání elementy z pole.|  
  
## <a name="remarks"></a>Poznámky  
 **CAtlArray** poskytuje metody pro vytváření a správa elementů uživatelem definovaný typ pole. I když standardní C pole, podobně jako **CAtlArray** objekt dynamicky zmenšit a růst podle potřeby. Pole indexu je vždy spuštěn na pozici 0 a horní mez pevné, nebo moct rozšířit při přidávání nových elementů.  
  
 U polí s malý počet elementů třídy ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) lze použít.  
  
 **CAtlArray** souvisí s MFC na **carray –** třídy a bude fungovat v projektu knihovny MFC, i když bez podpory serializace.  
  
 Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="add"></a>CAtlArray::Add  
 Voláním této metody lze přidat element do objekt array.  
  
```
size_t Add(INARGTYPE element);
size_t Add();
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Element, který chcete přidat do pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí index přidaný prvek.  
  
### <a name="remarks"></a>Poznámky  
 Nový prvek přidán na konec pole. Pokud žádný element je zadané prázdné prvek přidán; To znamená pole se zvýší velikost, jako by byl přidán skutečné element. Pokud se operace nezdaří, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) je volána s argumentem E_OUTOFMEMORY.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]  
  
##  <a name="append"></a>CAtlArray::Append  
 Voláním této metody lze přidat na konec jiné obsah jedno pole.  
  
```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `aSrc`  
 Pole pro připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí index prvního připojení prvku.  
  
### <a name="remarks"></a>Poznámky  
 Prvky v zadaná pole jsou přidány na konec existující pole. V případě potřeby paměti se přidělí pro uložení nové prvky.  
  
 Pole musí být stejného typu a není možné připojit pole na sebe sama.  
  
 V sestavení pro ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` argument není platné pole nebo pokud `aSrc` odkazuje na stejný objekt. V sestavení pro vydání neplatné argumenty může způsobit nepředvídatelné chování.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]  
  
##  <a name="assertvalid"></a>CAtlArray::AssertValid  
 Volejte tuto metodu za účelem potvrzení, že je platný objekt array.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud objekt pole není platný, `ATLASSERT` vyvolá výjimku kontrolní výrazy. Tato metoda je dostupná pouze v případě, že _DEBUG – je definována.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]  
  
##  <a name="catlarray"></a>CAtlArray::CAtlArray  
 Konstruktor  
  
```
CAtlArray() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje objekt pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]  
  
##  <a name="dtor"></a>CAtlArray:: ~ CAtlArray  
 Destruktor.  
  
```
~CAtlArray() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny prostředky využívané objektem pole.  
  
##  <a name="copy"></a>CAtlArray::Copy  
 Volejte tuto metodu pro kopírování prvků jedno pole do jiného.  
  
```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `aSrc`  
 Zdroj elementy zkopírovat do pole.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu přepsat prvky jednoho pole s prvky jiné pole. V případě potřeby paměti se přidělí pro uložení nové prvky. Není možné zkopírovat prvky pole na sebe sama.  
  
 Pokud stávajícího obsahu pole se má zachovat, použijte [CAtlArray::Append](#append) místo.  
  
 V sestavení pro ladění, bude vyvolána ATLASSERT, pokud existující `CAtlArray` objekt není platný, nebo pokud `aSrc` odkazuje na stejný objekt. V sestavení pro vydání neplatné argumenty může způsobit nepředvídatelné chování.  
  
> [!NOTE]
> `CAtlArray::Copy`nepodporuje pole skládající se z prvků vytvořených pomocí [CAutoPtr](../../atl/reference/cautoptr-class.md) třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]  
  
##  <a name="freeextra"></a>CAtlArray::FreeExtra  
 Voláním této metody lze odebrat všechny prázdné prvky z pole.  
  
```
void FreeExtra() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Budou odebrány všechny prázdné prvky, ale velikost a horní mez pole zůstanou beze změny.  
  
 V sestavení pro ladění ATLASSERT, bude vyvolána pokud CAtlArray objekt není platný, nebo pokud pole by překročila maximální velikosti.  
  
##  <a name="getat"></a>CAtlArray::GetAt  
 Volání, že tuto metodu za účelem načte jeden element z objektu pole.  
  
```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Hodnota indexu pole elementu, který chcete vrátit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na element požadované pole.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, bude-li vyvolána ATLASSERT `iElement` překračuje maximální počet prvků v poli. V sestavení pro vydání neplatný argument. může způsobit nepředvídatelné chování.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]  
  
##  <a name="getcount"></a>CAtlArray::GetCount  
 Volejte tuto metodu za účelem vrátí počet prvků, které jsou uložené v poli.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků, které jsou uložené v poli.  
  
### <a name="remarks"></a>Poznámky  
 Jako první prvek v poli je na pozici 0, hodnota vrácený `GetCount` je vždy 1 větší než největší index.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlArray::GetAt](#getat).  
  
##  <a name="getdata"></a>CAtlArray::GetData  
 Volejte tuto metodu vrátit ukazatel na první prvek v poli.  
  
```
E* GetData() throw();
const E* GetData() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na ukládání první prvek v poli místo v paměti. Pokud jsou k dispozici žádné elementy, vrátí se hodnota NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]  
  
##  <a name="inargtype"></a>CAtlArray::INARGTYPE  
 Datový typ pro použití při přidávání elementů do pole.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertarrayat"></a>CAtlArray::InsertArrayAt  
 Volejte tuto metodu za účelem vložení do jiné jedno pole.  
  
```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```  
  
### <a name="parameters"></a>Parametry  
 `iStart`  
 Index, na které má být vložen pole.  
  
 `paNew`  
 Pole, která má být vložen.  
  
### <a name="remarks"></a>Poznámky  
 Elementy z pole `paNew` se zkopírují do objekt pole, počínaje na element `iStart`. Stávající elementy pole přesunou do vyhnout přepsáním.  
  
 V sestavení pro ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt není platný, nebo pokud `paNew` ukazatel má hodnotu NULL nebo neplatná.  
  
> [!NOTE]
> `CAtlArray::InsertArrayAt`nepodporuje pole skládající se z prvků vytvořených pomocí [CAutoPtr](../../atl/reference/cautoptr-class.md) třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]  
  
##  <a name="insertat"></a>CAtlArray::InsertAt  
 Volejte tuto metodu za účelem vložení nového elementu (nebo více kopií elementu) do pole objektu.  
  
```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Index, kde element nebo elementy, jsou má být vložen.  
  
 `element`  
 Hodnota elementu nebo elementy, aby bylo možné vložit.  
  
 `nCount`  
 Počet elementů přidat.  
  
### <a name="remarks"></a>Poznámky  
 Vloží jeden či více elementů do pole, počínaje indexem `iElement`. Stávající elementy přesunou do vyhnout přepsáním.  
  
 V sestavení pro ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt je neplatný, počet prvků který se má přidat nulová nebo kombinovaný počet elementů je příliš velký pro pole tak, aby obsahovala. V sestavení pro maloobchodní předáním neplatné parametry může způsobit nepředvídatelné výsledky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]  
  
##  <a name="isempty"></a>CAtlArray::IsEmpty  
 Volejte tuto metodu za účelem testování, je-li pole prázdné.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud pole je prázdné, jinak hodnota false.  
  
### <a name="remarks"></a>Poznámky  
 Pole se říká být prázdný, pokud obsahuje žádné elementy. Proto i když pole obsahuje prázdné prvky, není prázdná.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]  
  
##  <a name="operator_at"></a>[CAtlArray::operator]  
 Volání tento operátor vrací odkaz na element v poli.  
  
```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Hodnota indexu pole elementu, který chcete vrátit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na element požadované pole.  
  
### <a name="remarks"></a>Poznámky  
 Podobné funkce, která se provede [CAtlArray::GetAt](#getat). Na rozdíl od třídy MFC [carray –](../../mfc/reference/carray-class.md), tento operátor nelze použít jako náhrada za [CAtlArray::SetAt](#setat).  
  
 V sestavení pro ladění, bude-li vyvolána ATLASSERT `iElement` překračuje celkový počet prvků v poli. V sestavení pro maloobchodní neplatný parametr může způsobit nepředvídatelné výsledky.  
  
##  <a name="outargtype"></a>CAtlArray::OUTARGTYPE  
 Datový typ pro načítání elementy z pole.  
  
```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```  
  
##  <a name="removeall"></a>CAtlArray::RemoveAll  
 Voláním této metody lze odebrat všechny elementy z objektu pole.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny elementy pole objektu.  
  
 Tato metoda volá [CAtlArray::SetCount](#setcount) ke změně velikosti pole a následně uvolní všechny přidělené paměti.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlArray::IsEmpty](#isempty).  
  
##  <a name="removeat"></a>CAtlArray::RemoveAt  
 Volejte tuto metodu za účelem odeberte jeden či více elementů z pole.  
  
```
void RemoveAt(size_t iElement, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Index první prvek chcete odebrat.  
  
 `nCount`  
 Počet elementů k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 Odebere jeden či více elementů z pole. Všechny zbývající elementy posunuty. Horní mez se odečte, ale není uvolnit paměť, dokud volání [CAtlArray::FreeExtra](#freeextra) Přišla žádost.  
  
 V sestavení pro ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt není platný, nebo, pokud celkový počet `iElement` a `nCount` překračuje celkový počet prvků v poli. V sestavení pro maloobchodní neplatné parametry může způsobit nepředvídatelné výsledky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]  
  
##  <a name="setat"></a>CAtlArray::SetAt  
 Volejte tuto metodu a nastavit hodnotu elementu v objektu pole.  
  
```
void SetAt(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Index odkazující na pole elementu, který chcete nastavit.  
  
 `element`  
 Nová hodnota zadaného elementu.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, bude-li vyvolána ATLASSERT `iElement` překračuje maximální počet prvků v poli. V sestavení pro maloobchodní neplatný parametr může způsobit nepředvídatelné výsledky.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlArray::GetAt](#getat).  
  
##  <a name="setcount"></a>CAtlArray::SetCount  
 Volejte tuto metodu a nastavit velikost pole objektu.  
  
```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewSize`  
 Požadovaná velikost pole.  
  
 `nGrowBy`  
 Hodnotu sloužící k určení na něm vyrovnávací paměti. Hodnota -1 způsobí, že interně počítanou hodnotu, který se má použít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je pole úspěšně po změně velikosti, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Toto pole můžete zvětšit nebo zmenšit velikost. Pokud je vyšší, velmi prázdné prvky se přidají do pole. Pokud zmenšit, se odstraní elementy největší indexy a uvolnit paměť.  
  
 Tuto metodu použijte k nastavení velikosti pole před jeho použitím. Pokud `SetCount` se nepoužívá, proces přidávání elementů – a provést přidělení dalších paměti – se sníží výkon a fragmentovat paměti.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlArray::GetData](#getdata).  
  
##  <a name="setatgrow"></a>CAtlArray::SetAtGrow  
 Volejte tuto metodu a nastavit hodnotu elementu v objektu pole, rozšíření pole podle potřeby.  
  
```
void SetAtGrow(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Index odkazující na pole elementu, který chcete nastavit.  
  
 `element`  
 Nová hodnota zadaného elementu.  
  
### <a name="remarks"></a>Poznámky  
 Nahradí hodnotu elementu ukazující na index. Pokud `iElement` je větší než aktuální velikost pole, je pole automaticky zvětšit pomocí volání do [CAtlArray::SetCount](#setcount). V sestavení pro ladění, bude vyvolána ATLASSERT, pokud `CAtlArray` objekt není platný. V sestavení pro maloobchodní neplatné parametry může způsobit nepředvídatelné výsledky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MMXSwarm](../../visual-cpp-samples.md)   
 [Příklad DynamicConsumer](../../visual-cpp-samples.md)   
 [Příklad UpdatePV](../../visual-cpp-samples.md)   
 [Ukázka rámeček](../../visual-cpp-samples.md)   
 [Carray – třída](../../mfc/reference/carray-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
