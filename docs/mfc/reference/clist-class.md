---
title: "CList – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
dev_langs: C++
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed7cd5ca4a1c3ef08707efc722c8f6ee299295c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clist-class"></a>CList – třída
Podporuje seřazené seznamy nejedinečný objekty přístupné postupně nebo podle hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class TYPE, class ARG_TYPE = const TYPE&>  
class CList : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CList::CList](#clist)|Vytvoří prázdný uspořádaného seznamu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CList::AddHead](#addhead)|Přidá do hlavičky seznamu (díky nové head) elementu (nebo všechny elementy v jiném seznamu).|  
|[CList::AddTail](#addtail)|Přidá na konec seznamu (díky nové tail) elementu (nebo všechny elementy v jiném seznamu).|  
|[CList::Find](#find)|Načte pozici elementu určená hodnotou ukazatele.|  
|[CList::FindIndex](#findindex)|Načte pozici elementu určeného index počítaný od nuly.|  
|[CList::GetAt](#getat)|Získá element na dané pozici.|  
|[CList::GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|  
|[CList::GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|  
|[CList::GetHeadPosition](#getheadposition)|Vrátí pozici element head seznamu.|  
|[CList::GetNext](#getnext)|Získá další prvek pro iterace.|  
|[CList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|  
|[CList::GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|  
|[CList::GetTail](#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|  
|[CList::GetTailPosition](#gettailposition)|Vrátí pozici tail element seznamu.|  
|[CList::InsertAfter](#insertafter)|Vloží nového elementu za dané pozici.|  
|[CList::InsertBefore](#insertbefore)|Vloží nového elementu před dané pozici.|  
|[CList::IsEmpty](#isempty)|Testy pro prázdný seznam podmínku (žádné elementy).|  
|[CList::RemoveAll](#removeall)|Odebere všechny elementy z tohoto seznamu.|  
|[CList::RemoveAt](#removeat)|Odebere element z tohoto seznamu, určeného umístění.|  
|[CList::RemoveHead](#removehead)|Odebere element z hlavičky v seznamu.|  
|[CList::RemoveTail](#removetail)|Odebere element z konec seznamu.|  
|[CList::SetAt](#setat)|Nastaví element na dané pozici.|  
  
#### <a name="parameters"></a>Parametry  
 `TYPE`  
 Typ objektu, které jsou uloženy v seznamu.  
  
 `ARG` *_* `TYPE`  
 Typ slouží k odkazování objekty uložené v seznamu. Může být odkaz.  
  
## <a name="remarks"></a>Poznámky  
 `CList`Zobrazí se chovají jako dvakrát propojené seznamy.  
  
 Proměnné typu **pozice** je klíč pro seznamu. Můžete použít **pozice** proměnné jako iterovat procházení seznam postupně a jako záložku pro uložení na místě. Pozice není stejný jako index, ale.  
  
 Element vložení je velmi rychle v seznamu head, od nějž a v známá **pozice**. Sekvenční vyhledávání je nezbytné pro vyhledávání element na hodnotu nebo index. Toto hledání může být pomalé, pokud je seznam dlouho.  
  
 Pokud potřebujete výpis jednotlivé prvky v seznamu, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Určité funkce člena třídy volání globální pomocné funkce, které je nutné upravit pro většiny použití `CList` třídy. V tématu [pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md) v části "Makra a globální prvky".  
  
 Další informace o používání `CList`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtempl.h  
  
##  <a name="addhead"></a>CList::AddHead  
 Přidá nového elementu nebo seznam prvků head tohoto seznamu.  
  
```  
POSITION AddHead(ARG_TYPE newElement);  
void AddHead(CList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Určení typu prvku seznam (může být odkaz) parametr šablony.  
  
 `newElement`  
 Nového elementu.  
  
 `pNewList`  
 Ukazatel na jiný `CList` seznamu. Prvky v `pNewList` bude přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první verze **pozice** hodnota nově vloženou elementu.  
  
### <a name="remarks"></a>Poznámky  
 V seznamu nesmí být prázdné před provedením operace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]  
  
##  <a name="addtail"></a>CList::AddTail  
 Přidá nového elementu nebo seznam prvků na konec tohoto seznamu.  
  
```  
POSITION AddTail(ARG_TYPE newElement);  
void AddTail(CList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Určení typu prvku seznam (může být odkaz) parametr šablony.  
  
 `newElement`  
 Element, který má být přidán do tohoto seznamu.  
  
 `pNewList`  
 Ukazatel na jiný `CList` seznamu. Prvky v `pNewList` bude přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první verze **pozice** hodnota nově vloženou elementu.  
  
### <a name="remarks"></a>Poznámky  
 V seznamu nesmí být prázdné před provedením operace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]  
  
##  <a name="clist"></a>CList::CList  
 Vytvoří prázdný uspořádaného seznamu.  
  
```  
CList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Členitost přidělení paměti pro rozšíření seznamu.  
  
### <a name="remarks"></a>Poznámky  
 S růstem seznamu jednotek se přidělí paměť `nBlockSize` položky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]  
  
##  <a name="find"></a>CList::Find  
 Vyhledá v seznamu postupně najít první prvek odpovídající zadané `searchValue`.  
  
```  
POSITION Find(
    ARG_TYPE searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Určení typu prvku seznam (může být odkaz) parametr šablony.  
  
 `searchValue`  
 Hodnota, která se má najít v seznamu.  
  
 `startAfter`  
 Počáteční pozice pro vyhledávání. Pokud není zadaná žádná hodnota, hledání začíná head element.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud objekt nebyl nalezen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]  
  
##  <a name="findindex"></a>CList::FindIndex  
 Používá hodnotu `nIndex` jako index do seznamu.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index založený na nule elementu seznamu nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud `nIndex` je záporný nebo příliš velký.  
  
### <a name="remarks"></a>Poznámky  
 Spuštěním kontroly sekvenční z hlavičky v seznamu na  *n* element TD.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]  
  
##  <a name="getat"></a>CList::GetAt  
 Získá seznam element na dané pozici.  
  
```  
TYPE& GetAt(POSITION position);  
const TYPE& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ objektu v seznamu.  
  
 *pozice*  
 Pozice elementu, který chcete získat v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Naleznete v popisu návratovou hodnotu pro `GetHead`.  
  
### <a name="remarks"></a>Poznámky  
 `GetAt`Vrátí element (nebo odkaz na element) přidružené k dané pozici. Není stejný jako index a nemůže pracovat **pozice** hodnotu sami. Proměnné typu **pozice** je klíč pro seznamu.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CList::GetHeadPosition](#getheadposition).  
  
##  <a name="getcount"></a>CList::GetCount  
 Získá počet elementů v tomto seznamu.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselnou hodnotu obsahující počet elementu.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody bude generovat stejný výsledek jako [CList::GetSize](#getsize) metoda.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CList::RemoveHead](#removehead).  
  
##  <a name="gethead"></a>CList::GetHead  
 Získá head element (nebo odkaz na head element) v tomto seznamu.  
  
```  
const TYPE& GetHead() const;  
  
TYPE& GetHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ objektu v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je seznam **const**, `GetHead` vrátí kopii elementu na první pozice v seznamu. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetHead` vrátí odkaz na element v první pozice v seznamu. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `GetHead`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]  
  
##  <a name="getheadposition"></a>CList::GetHeadPosition  
 Získá pozici element head tohoto seznamu.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud je seznam prázdný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]  
  
##  <a name="getnext"></a>CList::GetNext  
 Získá seznam element identifikovaný `rPosition`, potom nastaví `rPosition` k **pozice** hodnotu další položky v seznamu.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
const TYPE& GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů v seznamu.  
  
 `rPosition`  
 Odkaz na **pozice** hodnoty vrácené předchozí `GetNext`, [GetHeadPosition](#getheadposition), nebo jiné členské funkce volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je seznam **const**, `GetNext` vrátí kopii element seznamu. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetNext` vrátí odkaz na element seznamu. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetNext` ve smyčce dopředného iterace Pokud vytvořit počáteční pozice pomocí volání `GetHeadPosition` nebo **najít**.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud načtené elementem je poslední v seznamu, pak nová hodnota `rPosition` je nastaven na **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]  
  
##  <a name="getprev"></a>CList::GetPrev  
 Získá seznam element identifikovaný `rPosition`, potom nastaví `rPosition` k **pozice** hodnotu předchozí položky v seznamu.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
const TYPE& GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů v seznamu.  
  
 `rPosition`  
 Odkaz na **pozice** hodnoty vrácené předchozí `GetPrev` nebo jiné členské funkce volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je seznam **const**, `GetPrev` vrátí kopii elementu na první pozice v seznamu. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a chrání před změnou seznamu.  
  
 Pokud je seznam není **const**, `GetPrev` vrátí odkaz na element seznamu. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetPrev` ve smyčce zpětné iterace Pokud vytvořit počáteční pozice pomocí volání `GetTailPosition` nebo **najít**.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud je načtený element první v seznamu, pak nová hodnota `rPosition` je nastaven na **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]  
  
##  <a name="getsize"></a>CList::GetSize  
 Vrátí počet prvků seznamu.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení počet elementů v seznamu.  Voláním této metody bude generovat stejný výsledek jako [CList::GetCount](#getcount) metoda.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]  
  
##  <a name="gettail"></a>CList::GetTail  
 Získá `CObject` ukazatele, který reprezentuje element tail tohoto seznamu.  
  
```  
TYPE& GetTail();  
const TYPE& GetTail() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Naleznete v popisu návratovou hodnotu pro [GetHead](../../mfc/reference/coblist-class.md#gethead).  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `GetTail`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](../../mfc/reference/coblist-class.md#isempty) ověřit, jestli seznam obsahuje elementy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]  
  
##  <a name="gettailposition"></a>CList::GetTailPosition  
 Získá umístění prvku tail tohoto seznamu; **NULL** Pokud je seznam prázdný.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud je seznam prázdný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]  
  
##  <a name="insertafter"></a>CList::InsertAfter  
 Přidá element do tohoto seznamu za elementem na zadané pozici.  
  
```  
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *pozice*  
 A **pozice** hodnoty vrácené předchozí `GetNext`, `GetPrev`, nebo **najít** volání funkce člen.  
  
 `ARG_TYPE`  
 Určení typu prvku seznamu parametr šablony.  
  
 `newElement`  
 Element, který má být přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo seznamu elementu načtení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]  
  
##  <a name="insertbefore"></a>CList::InsertBefore  
 Přidá element do tohoto seznamu před element na zadané pozici.  
  
```  
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *pozice*  
 A **pozice** hodnoty vrácené předchozí `GetNext`, `GetPrev`, nebo **najít** volání funkce člen.  
  
 `ARG_TYPE`  
 Určení typu prvku seznam (může být odkaz) parametr šablony.  
  
 `newElement`  
 Element, který má být přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo seznamu elementu načtení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *pozice* je **NULL**, element vloženo na první pozice v seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]  
  
##  <a name="isempty"></a>CList::IsEmpty  
 Určuje, zda tento seznam neobsahuje žádné elementy.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je tento seznam prázdný; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]  
  
##  <a name="removeall"></a>CList::RemoveAll  
 Odebere všechny elementy z tohoto seznamu a uvolní přidružené paměti.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Seznam je prázdný, nevygeneruje se žádná chyba.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]  
  
##  <a name="removeat"></a>CList::RemoveAt  
 Odebere zadaný element z tohoto seznamu.  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>Parametry  
 *pozice*  
 Pozice elementu, který chcete odebrat ze seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]  
  
##  <a name="removehead"></a>CList::RemoveHead  
 Odebere element z hlavičky v seznamu a vrátí ukazatel na ni.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element dříve v první pozice v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `RemoveHead`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]  
  
##  <a name="removetail"></a>CList::RemoveTail  
 Odebere element z konec seznamu a vrátí ukazatel na ni.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element, který byl na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `RemoveTail`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]  
  
##  <a name="setat"></a>CList::SetAt  
 Proměnné typu **pozice** je klíč pro seznamu.  
  
```  
void SetAt(POSITION pos, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 **Pozice** elementu nastavit.  
  
 `ARG_TYPE`  
 Určení typu prvku seznam (může být odkaz) parametr šablony.  
  
 `newElement`  
 Element, který chcete přidat do seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Není stejný jako index a nemůže pracovat **pozice** hodnotu sami. `SetAt`zapíše elementu na zadané pozici v seznamu.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMap – třída](../../mfc/reference/cmap-class.md)   
 [Carray – třída](../../mfc/reference/carray-class.md)
