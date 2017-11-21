---
title: "Třída CAtlList | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
dev_langs: C++
helpviewer_keywords: CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 80f8f66787d2268c6543f8f7a66ca7d13ae167ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="catllist-class"></a>CAtlList – třída
Tato třída poskytuje metody pro vytváření a správu objekt seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class ETraits = CElementTraits<E>>  
class CAtlList
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ elementu.  
  
 `ETraits`  
 Kód používaný k zkopírovat nebo přesunout elementy. V tématu [CElementTraits třída](../../atl/reference/celementtraits-class.md) další podrobnosti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlList::INARGTYPE](#inargtype)||  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlList::CAtlList](#catllist)|Konstruktor|  
|[CAtlList:: ~ CAtlList](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlList::AddHead](#addhead)|Voláním této metody lze přidat element do první pozice v seznamu.|  
|[CAtlList::AddHeadList](#addheadlist)|Volejte tuto metodu za účelem přidání existujícího seznamu do první pozice v seznamu.|  
|[CAtlList::AddTail](#addtail)|Voláním této metody lze přidat element do konec tohoto seznamu.|  
|[CAtlList::AddTailList](#addtaillist)|Volejte tuto metodu za účelem přidání existujícího seznamu na konec tohoto seznamu.|  
|[CAtlList::AssertValid](#assertvalid)|Volejte tuto metodu za účelem potvrďte, že v seznamu je platný.|  
|[CAtlList::Find](#find)|Volání této metody na hledání v seznamu daného elementu.|  
|[CAtlList::FindIndex](#findindex)|Volejte tuto metodu za účelem získání pozice elementu, danou hodnotu indexu.|  
|[CAtlList::GetAt](#getat)|Volejte tuto metodu za účelem vrátí prvek na zadané pozici v seznamu.|  
|[CAtlList::GetCount](#getcount)|Volejte tuto metodu, která vrátí počet objektů v seznamu.|  
|[CAtlList::GetHead](#gethead)|Volejte tuto metodu za účelem vrátí prvek na první pozice v seznamu.|  
|[CAtlList::GetHeadPosition](#getheadposition)|Volejte tuto metodu za účelem získání pozice první pozice v seznamu.|  
|[CAtlList::GetNext](#getnext)|Volejte tuto metodu vrátit na další prvek ze seznamu.|  
|[CAtlList::GetPrev](#getprev)|Voláním této metody vrátit předchozí element ze seznamu.|  
|[CAtlList::GetTail](#gettail)|Volejte tuto metodu za účelem vrátí prvek na konec seznamu.|  
|[CAtlList::GetTailPosition](#gettailposition)|Volejte tuto metodu za účelem získání pozici konec seznamu.|  
|[CAtlList::InsertAfter](#insertafter)|Volejte tuto metodu za účelem vložení nového elementu do seznamu za konkrétní pozici.|  
|[CAtlList::InsertBefore](#insertbefore)|Volejte tuto metodu za účelem vložení nového elementu do seznamu před konkrétní pozici.|  
|[CAtlList::IsEmpty](#isempty)|Volejte tuto metodu za účelem určení, zda je seznam prázdný.|  
|[CAtlList::MoveToHead](#movetohead)|Voláním této metody lze přesunout do první pozice v seznamu daného elementu.|  
|[CAtlList::MoveToTail](#movetotail)|Voláním této metody lze přesunout na konec seznamu daného elementu.|  
|[CAtlList::RemoveAll](#removeall)|Voláním této metody lze odebrat všechny elementy ze seznamu.|  
|[CAtlList::RemoveAt](#removeat)|Voláním této metody lze odebrat ze seznamu jediným elementem.|  
|[CAtlList::RemoveHead](#removehead)|Volejte tuto metodu za účelem odebrání element v první pozice v seznamu.|  
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Voláním této metody lze odebrat element v první pozice v seznamu bez návrat hodnoty.|  
|[CAtlList::RemoveTail](#removetail)|Volejte tuto metodu za účelem odebrání prvek na konec seznamu.|  
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Voláním této metody lze odebrat prvek na konec seznamu bez návrat hodnoty.|  
|[CAtlList::SetAt](#setat)|Volejte tuto metodu a nastavit hodnotu prvku na dané pozici v seznamu.|  
|[CAtlList::SwapElements](#swapelements)|Volejte tuto metodu za účelem odkládacího souboru v seznamu elementů.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlList` Třídy podporuje seřazené seznamy nejedinečný objekty přístupné postupně nebo podle hodnoty. `CAtlList`Zobrazí se chovají jako dvakrát propojený seznamy. Každý seznam má head a koncovou část a nové prvky (nebo seznamy v některých případech) lze přidat na libovolném konci seznamu, nebo vložit před nebo po konkrétní prvky.  
  
 Většina `CAtlList` metody zkontrolujte použít hodnoty pozice. Tato hodnota se používá metodami tak, aby odkazovaly skutečné paměti umístění, kde elementy jsou uloženy a by neměl být počítané nebo předpovědět přímo. Pokud je nutné k přístupu  *n* element TD v seznamu, metoda [CAtlList::FindIndex](#findindex) vrátí s odpovídající hodnotou pozice pro daného indexu. Metody [CAtlList::GetNext](#getnext) a [CAtlList::GetPrev](#getprev) lze použít k iteraci v rámci objektů v seznamu.  
  
 Další informace týkající se třídy kolekce, která je k dispozici s technologií ATL najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="addhead"></a>CAtlList::AddHead  
 Voláním této metody lze přidat element do první pozice v seznamu.  
  
```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Nového elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici nově přidaný prvek.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se použije první verze, je prázdný element vytvořený pomocí jeho výchozí konstruktor, nikoli jeho kopírovacího konstruktoru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]  
  
##  <a name="addheadlist"></a>CAtlList::AddHeadList  
 Volejte tuto metodu za účelem přidání existujícího seznamu do první pozice v seznamu.  
  
```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Parametry  
 `plNew`  
 Seznam, který má být přidán.  
  
### <a name="remarks"></a>Poznámky  
 V seznamu na kterou odkazuje `plNew` vloží na začátek seznamu existující. V sestavení pro ladění k chybě assertion dojde v případě `plNew` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]  
  
##  <a name="addtail"></a>CAtlList::AddTail  
 Voláním této metody lze přidat element do konec tohoto seznamu.  
  
```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Elementu, který chcete přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí POZICI nově přidaný prvek.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se použije první verze, je prázdný element vytvořený pomocí jeho výchozí konstruktor, nikoli jeho kopírovacího konstruktoru. Bude prvek přidán na konec seznamu, a proto nyní začne poškozené databáze. Tuto metodu můžete použít s prázdným seznamem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]  
  
##  <a name="addtaillist"></a>CAtlList::AddTailList  
 Volejte tuto metodu za účelem přidání existujícího seznamu na konec tohoto seznamu.  
  
```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Parametry  
 `plNew`  
 Seznam, který má být přidán.  
  
### <a name="remarks"></a>Poznámky  
 V seznamu na kterou odkazuje `plNew` je vložen za posledním elementem (pokud existuje) do seznamu objektů. Posledním prvkem v `plNew` seznamu proto stane poškozené databáze. V sestavení pro ladění k chybě assertion dojde v případě *plNew* rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]  
  
##  <a name="assertvalid"></a>CAtlList::AssertValid  
 Volejte tuto metodu za účelem potvrďte, že v seznamu je platný.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění chybu assertion dojde, pokud objekt seznamu není platný. Aby byl platný, musí mít prázdný seznam head i tail odkazující na hodnotu NULL a musí mít seznam, který není prázdný, head i tail odkazující na platné adresy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]  
  
##  <a name="catllist"></a>CAtlList::CAtlList  
 Konstruktor  
  
```
CAtlList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Velikost bloku.  
  
### <a name="remarks"></a>Poznámky  
 V konstruktoru pro `CAtlList` objektu. Velikost bloku se rozumí míra množství paměti přidělené, pokud je potřeba nového elementu. Bloky o větší velikosti snížit volání rutiny přidělení paměti, ale spotřebovávají více prostředků.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]  
  
##  <a name="dtor"></a>CAtlList:: ~ CAtlList  
 Destruktor.  
  
```
~CAtlList() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky, včetně volání [CAtlList::RemoveAll](#removeall) odebrat všechny elementy ze seznamu.  
  
 V sestavení pro ladění k selhání assertion dojde v případě seznam stále obsahuje některé prvky po volání `RemoveAll`.  
  
##  <a name="find"></a>CAtlList::Find  
 Volání této metody na hledání v seznamu daného elementu.  
  
```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Elementu, který chcete nalézt v seznamu.  
  
 `posStartAfter`  
 Počáteční pozice pro vyhledávání. Pokud není zadaná žádná hodnota, hledání začíná head element.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice elementu, pokud najde, jinak vrátí hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění k selhání assertion dojde, pokud objekt seznamu není platný, nebo pokud `posStartAfter` hodnota je mimo rozsah.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]  
  
##  <a name="findindex"></a>CAtlList::FindIndex  
 Volejte tuto metodu za účelem získání pozice elementu, danou hodnotu indexu.  
  
```
POSITION FindIndex(size_t iElement) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Index založený na nule požadované seznamu elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odpovídající pozice hodnotu nebo hodnotu NULL, pokud `iElement` je mimo rozsah.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí POZICI odpovídající hodnotu daného indexu povolení přístupu k  *n* element TD v seznamu.  
  
 V sestavení pro ladění chybu assertion dojde, pokud objekt seznamu není platný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]  
  
##  <a name="getat"></a>CAtlList::GetAt  
 Volejte tuto metodu za účelem vrátí prvek na zadané pozici v seznamu.  
  
```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice zadání určitý element.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na nebo kopii elementu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je seznam **const**, `GetAt` vrátí kopii elementu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetAt` vrátí odkaz na element. To umožňuje metoda má být použit na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
 V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::FindIndex](#findindex).  
  
##  <a name="getcount"></a>CAtlList::GetCount  
 Volejte tuto metodu, která vrátí počet objektů v seznamu.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků v seznamu.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::Find](#find).  
  
##  <a name="gethead"></a>CAtlList::GetHead  
 Volejte tuto metodu za účelem vrátí prvek na první pozice v seznamu.  
  
```
E& GetHead() throw();
const E& GetHead() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na nebo kopii, element v první pozice v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je seznam **const**, `GetHead` vrátí kopii elementu na první pozice v seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetHead` vrátí odkaz na element v první pozice v seznamu. To umožňuje metoda má být použit na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
 V sestavení pro ladění dojde výraz je neplatný. Pokud první pozice v seznamu odkazuje na hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::AddHead](#addhead).  
  
##  <a name="getheadposition"></a>CAtlList::GetHeadPosition  
 Volejte tuto metodu za účelem získání pozice první pozice v seznamu.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí POZICI hodnotu odpovídající element v první pozice v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je seznam prázdný, je vrácena hodnota NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]  
  
##  <a name="getnext"></a>CAtlList::GetNext  
 Volejte tuto metodu vrátit na další prvek ze seznamu.  
  
```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice, vrácené z předchozího volání `GetNext`, [CAtlList::GetHeadPosition](#getheadposition), nebo jiné `CAtlList` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je seznam **const**, `GetNext` vrátí kopii na další prvek seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetNext` vrátí odkaz na další prvek seznamu. To umožňuje metoda má být použit na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Čítač pozice `pos`, se aktualizuje a přejděte na další prvek v seznamu, nebo hodnota NULL, pokud nejsou žádné další prvky. V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::GetHeadPosition](#getheadposition).  
  
##  <a name="getprev"></a>CAtlList::GetPrev  
 Voláním této metody vrátit předchozí element ze seznamu.  
  
```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice, vrácené z předchozího volání `GetPrev`, [CAtlList::GetTailPosition](#gettailposition), nebo jiné `CAtlList` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je seznam **const**, `GetPrev` vrátí kopii element seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetPrev` vrátí odkaz na element seznamu. To umožňuje metoda má být použit na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Čítač pozice `pos`, se aktualizuje a přejděte na předchozí element v seznamu, nebo hodnota NULL, pokud nejsou žádné další prvky. V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::GetTailPosition](#gettailposition).  
  
##  <a name="gettail"></a>CAtlList::GetTail  
 Volejte tuto metodu za účelem vrátí prvek na konec seznamu.  
  
```
E& GetTail() throw();
const E& GetTail() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na nebo kopii, prvek na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je seznam **const**, `GetTail` vrátí kopii elementu na první pozice v seznamu. To umožňuje metoda má být použit pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetTail` vrátí odkaz na element v první pozice v seznamu. To umožňuje metoda má být použit na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
 V sestavení pro ladění chybu assertion dojde, pokud konec seznamu odkazuje na hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::AddTail](#addtail).  
  
##  <a name="gettailposition"></a>CAtlList::GetTailPosition  
 Volejte tuto metodu za účelem získání pozici konec seznamu.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí POZICI hodnotu odpovídající prvek na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je seznam prázdný, je vrácena hodnota NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]  
  
##  <a name="inargtype"></a>CAtlList::INARGTYPE  
 Typ použitý při element se předá jako vstupní argument.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertafter"></a>CAtlList::InsertAfter  
 Volejte tuto metodu za účelem vložení nového elementu do seznamu za konkrétní pozici.  
  
```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice, po jejímž uplynutí se vloží nového elementu.  
  
 `element`  
 Element, který má být vložen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice nového elementu.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění chybu assertion dojde, pokud v seznamu není platný, pokud se nezdaří úlohy insert, nebo pokud je proveden pokus o vložení prvku za tail.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]  
  
##  <a name="insertbefore"></a>CAtlList::InsertBefore  
 Volejte tuto metodu za účelem vložení nového elementu do seznamu před konkrétní pozici.  
  
```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Nového elementu se vloží do seznamu než tato hodnota pozice.  
  
 `element`  
 Element, který má být vložen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice nového elementu.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění chybu assertion dojde, pokud v seznamu není platný, pokud se nezdaří úlohy insert, nebo pokud je proveden pokus o vložení prvku před hlavičky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]  
  
##  <a name="isempty"></a>CAtlList::IsEmpty  
 Volejte tuto metodu za účelem určení, zda je seznam prázdný.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud seznam neobsahuje žádné objekty, jinak hodnota false.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]  
  
##  <a name="movetohead"></a>CAtlList::MoveToHead  
 Voláním této metody lze přesunout do první pozice v seznamu daného elementu.  
  
```
void MoveToHead(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice elementu, který chcete přesunout.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný element se přesune ze své aktuální pozici první pozice v seznamu. V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]  
  
##  <a name="movetotail"></a>CAtlList::MoveToTail  
 Voláním této metody lze přesunout na konec seznamu daného elementu.  
  
```
void MoveToTail(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice elementu, který chcete přesunout.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný element se přesune ze své aktuální pozici na konec seznamu. V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::MoveToHead](#movetohead).  
  
##  <a name="removeall"></a>CAtlList::RemoveAll  
 Voláním této metody lze odebrat všechny elementy ze seznamu.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere všechny elementy ze seznamu a uvolní přidělenou paměť. V sestavení pro ladí ATLASSERT, bude vyvolána pokud nebudou odstraněny všechny elementy nebo pokud byla poškozena struktura seznamu.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::IsEmpty](#isempty).  
  
##  <a name="removeat"></a>CAtlList::RemoveAt  
 Voláním této metody lze odebrat ze seznamu jediným elementem.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice elementu, který chcete odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Element odkazuje `pos` je odebrán, a uvolnit paměť. Se dá použít `RemoveAt` k odebrání head nebo konec seznamu.  
  
 V sestavení pro ladění dojde výraz je neplatný. Pokud v seznamu není platný nebo pokud odebrání elementu způsobí, že přístup k paměti, která není součástí struktury seznamu v seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]  
  
##  <a name="removehead"></a>CAtlList::RemoveHead  
 Volejte tuto metodu za účelem odebrání element v první pozice v seznamu.  
  
```
E RemoveHead();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí prvek na první pozice v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Head element se odstraní ze seznamu a uvolnit paměť. Vrátí se kopie elementu. V sestavení pro ladění dojde výraz je neplatný. Pokud je seznam prázdný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]  
  
##  <a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn  
 Voláním této metody lze odebrat element v první pozice v seznamu bez návrat hodnoty.  
  
```
void RemoveHeadNoReturn() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Head element se odstraní ze seznamu a uvolnit paměť. V sestavení pro ladění dojde výraz je neplatný. Pokud je seznam prázdný.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::IsEmpty](#isempty).  
  
##  <a name="removetail"></a>CAtlList::RemoveTail  
 Volejte tuto metodu za účelem odebrání prvek na konec seznamu.  
  
```
E RemoveTail();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí prvek na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Element poškozené databáze se odstraní ze seznamu a uvolnit paměť. Vrátí se kopie elementu. V sestavení pro ladění dojde výraz je neplatný. Pokud je seznam prázdný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]  
  
##  <a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn  
 Voláním této metody lze odebrat prvek na konec seznamu bez návrat hodnoty.  
  
```
void RemoveTailNoReturn() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Element poškozené databáze se odstraní ze seznamu a uvolnit paměť. V sestavení pro ladění dojde výraz je neplatný. Pokud je seznam prázdný.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlList::IsEmpty](#isempty).  
  
##  <a name="setat"></a>CAtlList::SetAt  
 Volejte tuto metodu a nastavit hodnotu prvku na dané pozici v seznamu.  
  
```
void SetAt(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice odpovídající elementu, který chcete změnit.  
  
 `element`  
 Nová hodnota elementu.  
  
### <a name="remarks"></a>Poznámky  
 Nahradí existující hodnotu `element`. V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]  
  
##  <a name="swapelements"></a>CAtlList::SwapElements  
 Volejte tuto metodu za účelem odkládacího souboru v seznamu elementů.  
  
```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pos1*  
 První POZICI hodnotu.  
  
 *pos2*  
 Druhá hodnota pozice.  
  
### <a name="remarks"></a>Poznámky  
 Zamění elementy na dvou místech zadán. V sestavení pro ladění bude chybu assertion dojít, pokud buď pozice hodnota je stejná na hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CList – třída](../../mfc/reference/clist-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
