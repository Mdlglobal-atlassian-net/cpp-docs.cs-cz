---
title: CTypedPtrList – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afb32a662c538526c4fe26f6abf46e56a42de728
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList – třída
Typově bezpečný "obálky" poskytuje pro objekty třídy `CPtrList`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Základní třída třídy seznamu typu ukazatele; musí být třída seznamu ukazatele ( `CObList` nebo `CPtrList`).  
  
 `TYPE`  
 Typ elementů uložený v seznamu základní třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|Přidá do hlavičky seznamu (díky nové head) elementu (nebo všechny elementy v jiném seznamu).|  
|[CTypedPtrList::AddTail](#addtail)|Přidá na konec seznamu (díky nové tail) elementu (nebo všechny elementy v jiném seznamu).|  
|[CTypedPtrList::GetAt](#getat)|Získá element na dané pozici.|  
|[CTypedPtrList::GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|  
|[CTypedPtrList::GetNext](#getnext)|Získá další prvek pro iterace.|  
|[CTypedPtrList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|  
|[CTypedPtrList::GetTail](#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|  
|[CTypedPtrList::RemoveHead](#removehead)|Odebere element z hlavičky v seznamu.|  
|[CTypedPtrList::RemoveTail](#removetail)|Odebere element z konec seznamu.|  
|[CTypedPtrList::SetAt](#setat)|Nastaví element na dané pozici.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití `CTypedPtrList` místo `CObList` nebo `CPtrList`, kontrola typu zařízení C++ pomáhá eliminovat chyby způsobené typy neodpovídající ukazatelů.  
  
 Kromě toho `CTypedPtrList` obálku provádí většinu přetypování, která by byla zapotřebí, pokud jste použili `CObList` nebo `CPtrList`.  
  
 Protože všechny `CTypedPtrList` jsou vložené funkce, pomocí této šablony nemá vliv na výrazně velikost a rychlost kódu.  
  
 Seznamy odvozené od `CObList` lze serializovat, ale které pocházejí z `CPtrList` nelze.  
  
 Když `CTypedPtrList` je odstraněn objekt, nebo při jeho prvky jsou odebrány, odeberou se jenom ukazatele není entity, které se odkazují.  
  
 Další informace o používání `CTypedPtrList`, najdete v článcích [kolekce](../../mfc/collections.md) a [na základě šablon třídy](../../mfc/template-based-classes.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří instanci `CTypedPtrList`, přidá jeden objekt, serializuje seznamu na disk a poté se odstraní objekt:  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtempl.h  
  
##  <a name="addhead"></a>  CTypedPtrList::AddHead  
 Tato funkce člen volá `BASE_CLASS` **:: AddHead**.  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ elementů uložený v seznamu základní třídy.  
  
 `newElement`  
 Ukazatel objektu, který má být přidán do tohoto seznamu. A **NULL** je povolena hodnota.  
  
 `BASE_CLASS`  
 Základní třída třídy seznamu typu ukazatele; musí být třída seznamu ukazatele ( [CObList](../../mfc/reference/coblist-class.md) nebo [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Ukazatel na jiný [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objektu. Prvky v `pNewList` bude přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první verze **pozice** hodnota nově vloženou elementu.  
  
### <a name="remarks"></a>Poznámky  
 První verze přidá nového elementu před první pozice v seznamu. Druhá verze přidá jiného seznamu elementů před hlavičky.  
  
##  <a name="addtail"></a>  CTypedPtrList::AddTail  
 Tato funkce člen volá `BASE_CLASS` **:: addtail –**.  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ elementů uložený v seznamu základní třídy.  
  
 `newElement`  
 Ukazatel objektu, který má být přidán do tohoto seznamu. A **NULL** je povolena hodnota.  
  
 `BASE_CLASS`  
 Základní třída třídy seznamu typu ukazatele; musí být třída seznamu ukazatele ( [CObList](../../mfc/reference/coblist-class.md) nebo [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Ukazatel na jiný [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objektu. Prvky v `pNewList` bude přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první verze **pozice** hodnota nově vloženou elementu.  
  
### <a name="remarks"></a>Poznámky  
 První verze přidá nového elementu za konec seznamu. Druhá verze přidá jiného seznamu elementů za konec seznamu.  
  
##  <a name="getat"></a>  CTypedPtrList::GetAt  
 Proměnné typu **pozice** je klíč pro seznamu.  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů, které jsou uloženy v seznamu.  
  
 *Pozice*  
 A **pozice** hodnoty vrácené předchozí `GetHeadPosition` nebo **najít** volání funkce člen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v seznamu je přístupné přes ukazatel na **const CTypedPtrList**, pak `GetAt` vrací ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.  
  
 Pokud v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetAt` vrátí odkaz na ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Není stejný jako index a nemůže pracovat **pozice** hodnotu sami. `GetAt` načte `CObject` ukazatel přidružené k dané pozici.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Tato vložená funkce volá `BASE_CLASS` **:: GetAt**.  
  
##  <a name="gethead"></a>  CTypedPtrList::GetHead  
 Získá ukazatele, který reprezentuje element head tohoto seznamu.  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů, které jsou uloženy v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v seznamu je přístupné přes ukazatel na **const CTypedPtrList**, pak `GetHead` vrací ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.  
  
 Pokud v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetHead` vrátí odkaz na ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `GetHead`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, jestli seznam obsahuje elementy.  
  
##  <a name="getnext"></a>  CTypedPtrList::GetNext  
 Získá seznam element identifikovaný `rPosition`, potom nastaví `rPosition` k **pozice** hodnotu další položky v seznamu.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů obsažených v tomto seznamu.  
  
 `rPosition`  
 Odkaz na **pozice** hodnoty vrácené předchozí `GetNext`, `GetHeadPosition`, nebo jiné členské funkce volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v seznamu je přístupné přes ukazatel na **const CTypedPtrList**, pak `GetNext` vrací ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.  
  
 Pokud v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetNext` vrátí odkaz na ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetNext` ve smyčce dopředného iterace Pokud vytvořit počáteční pozice pomocí volání `GetHeadPosition` nebo [CPtrList::Find](../../mfc/reference/coblist-class.md#find).  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud načtené elementem je poslední v seznamu, pak nová hodnota `rPosition` je nastaven na **NULL**.  
  
 Je možné odebrat element během iterace. Podívejte se na příklad pro [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).  
  
##  <a name="getprev"></a>  CTypedPtrList::GetPrev  
 Získá seznam element identifikovaný `rPosition`, potom nastaví `rPosition` k **pozice** hodnotu předchozí položky v seznamu.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů obsažených v tomto seznamu.  
  
 `rPosition`  
 Odkaz na **pozice** hodnoty vrácené předchozí `GetPrev` nebo jiné členské funkce volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v seznamu je přístupné přes ukazatel na **const CTypedPtrList**, pak `GetPrev` vrací ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.  
  
 Pokud v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetPrev` vrátí odkaz na ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetPrev` ve smyčce zpětné iterace Pokud vytvořit počáteční pozice pomocí volání `GetTailPosition` nebo **najít**.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud je načtený element první v seznamu, pak nová hodnota `rPosition` je nastaven na **NULL**.  
  
##  <a name="gettail"></a>  CTypedPtrList::GetTail  
 Získá ukazatele, který reprezentuje element head tohoto seznamu.  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů, které jsou uloženy v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v seznamu je přístupné přes ukazatel na **const CTypedPtrList**, pak `GetTail` vrací ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.  
  
 Pokud v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CTypedPtrList`, pak `GetTail` vrátí odkaz na ukazatel s typem zadaným parametrem šablony *typu*. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `GetTail`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, jestli seznam obsahuje elementy.  
  
##  <a name="removehead"></a>  CTypedPtrList::RemoveHead  
 Odebere element z hlavičky v seznamu a vrátí ji.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů, které jsou uloženy v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel dříve na první pozice v seznamu. Je tento ukazatel s typem zadaným parametrem šablony *typu*.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `RemoveHead`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, jestli seznam obsahuje elementy.  
  
##  <a name="removetail"></a>  CTypedPtrList::RemoveTail  
 Odebere element z konec seznamu a vrátí ji.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů, které jsou uloženy v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel dříve na konec seznamu. Je tento ukazatel s typem zadaným parametrem šablony *typu*.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `RemoveTail`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, jestli seznam obsahuje elementy.  
  
##  <a name="setat"></a>  CTypedPtrList::SetAt  
 Tato funkce člen volá `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 **Pozice** elementu nastavit.  
  
 *TYP*  
 Typ elementů uložený v seznamu základní třídy.  
  
 `newElement`  
 Ukazatel objekt, který má být zapsán do seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Proměnné typu **pozice** je klíč pro seznamu. Není stejný jako index a nemůže pracovat **pozice** hodnotu sami. `SetAt` zapíše objekt ukazatel na zadané pozici v seznamu.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Podrobné poznámky, najdete v části [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPtrList – třída](../../mfc/reference/cptrlist-class.md)   
 [CObList – třída](../../mfc/reference/coblist-class.md)
