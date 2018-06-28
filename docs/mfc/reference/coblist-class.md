---
title: Třída cObList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d66c26fb94fa0f4e1863a6a6a9663de4239611db
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039126"
---
# <a name="coblist-class"></a>CObList – třída
fSupports seřazené seznamy nejedinečný `CObject` ukazatele přístupné postupně nebo ukazatel hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CObList : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObList::CObList](#coblist)|Vytvoří prázdný seznam pro `CObject` ukazatele.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CObList::AddHead](#addhead)|Přidá do hlavičky seznamu (díky nové head) elementu (nebo všechny elementy v jiném seznamu).|  
|[CObList::AddTail](#addtail)|Přidá na konec seznamu (díky nové tail) elementu (nebo všechny elementy v jiném seznamu).|  
|[CObList::Find](#find)|Načte pozici elementu určená hodnotou ukazatele.|  
|[CObList::FindIndex](#findindex)|Načte pozici elementu určeného index počítaný od nuly.|  
|[CObList::GetAt](#getat)|Získá element na dané pozici.|  
|[CObList::GetCount](#getcount)|Vrátí počet prvků v tomto seznamu.|  
|[CObList::GetHead](#gethead)|Vrátí element head seznamu (nemůže být prázdný).|  
|[CObList::GetHeadPosition](#getheadposition)|Vrátí pozici element head seznamu.|  
|[CObList::GetNext](#getnext)|Získá další prvek pro iterace.|  
|[CObList::GetPrev](#getprev)|Získá předchozí prvek pro iterace.|  
|[CObList::GetSize](#getsize)|Vrátí počet prvků v tomto seznamu.|  
|[CObList::GetTail](#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|  
|[CObList::GetTailPosition](#gettailposition)|Vrátí pozici tail element seznamu.|  
|[CObList::InsertAfter](#insertafter)|Vloží nového elementu za dané pozici.|  
|[CObList::InsertBefore](#insertbefore)|Vloží nového elementu před dané pozici.|  
|[CObList::IsEmpty](#isempty)|Testy pro prázdný seznam podmínku (žádné elementy).|  
|[CObList::RemoveAll](#removeall)|Odebere všechny elementy z tohoto seznamu.|  
|[CObList::RemoveAt](#removeat)|Odebere element z tohoto seznamu, určeného umístění.|  
|[CObList::RemoveHead](#removehead)|Odebere element z hlavičky v seznamu.|  
|[CObList::RemoveTail](#removetail)|Odebere element z konec seznamu.|  
|[CObList::SetAt](#setat)|Nastaví element na dané pozici.|  
  
## <a name="remarks"></a>Poznámky  
 `CObList` Zobrazí se chovají jako dvakrát propojené seznamy.  
  
 Proměnné typu **pozice** je klíč pro seznamu. Můžete použít **pozice** proměnné jako iterovat procházení seznam postupně i jako záložku pro uložení na místě. Pozice není stejný jako index, ale.  
  
 Element vložení je velmi rychle v seznamu head, od nějž a v známá **pozice**. Sekvenční vyhledávání je nezbytné pro vyhledávání element na hodnotu nebo index. Toto hledání může být pomalé, pokud je seznam dlouho.  
  
 `CObList` zahrnuje implement_serial – makro pro podporu serializace a vypsání jejích elementů. Pokud seznam `CObject` ukazatele je uložen do archivu, a to buď operátor přetížené vložení nebo s `Serialize` členské funkce se každý `CObject` element serializován naopak.  
  
 Pokud potřebujete výpis individuální `CObject` prvky v seznamu, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Když `CObList` je odstraněn objekt, nebo pokud jeho elementy odeberou se jenom `CObject` ukazatele jsou odebrány, nikoliv objekty odkazují.  
  
 Může být vaše vlastní třídy z `CObList`. Novou třídu seznamu navržený tak, aby podržením ukazatele objekty, které jsou odvozené z `CObject`, přidává nové členy dat a nové členské funkce. Všimněte si, že v rozevíracím seznamu není výhradně typ bezpečné, protože umožňuje vložení všech `CObject` ukazatel.  
  
> [!NOTE]
>  Je nutné použít [implement_serial –](run-time-object-model-services.md#implement_serial) makro k implementaci vaší odvozené třídy, pokud chcete serializovat seznamu.  
  
 Další informace o používání `CObList`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
##  <a name="addhead"></a>  CObList::AddHead  
 Přidá nového elementu nebo seznam prvků head tohoto seznamu.  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *newElement*  
 `CObject` Ukazatele, který se má přidat do tohoto seznamu.  
  
 *pNewList*  
 Ukazatel na jiný `CObList` seznamu. Prvky v *pNewList* bude přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první verze **pozice** hodnota nově vloženou elementu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::AddHead`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE AddHead (void\***  `newElement` **);**<br /><br /> **void AddHead (CPtrList\***  `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE AddHead (const CString &** `newElement` **);**<br /><br /> **POZICE AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList\***  `pNewList` **);**|  
  
### <a name="remarks"></a>Poznámky  
 V seznamu nesmí být prázdné před provedením operace.  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `AddHead example: A CObList with 2 elements`  
  
 `a CAge at $44A8 40`  
  
 `a CAge at $442A 21`  
  
##  <a name="addtail"></a>  CObList::AddTail  
 Přidá nového elementu nebo seznam prvků na konec tohoto seznamu.  
  
```  
POSITION AddTail(CObject* newElement);  
void AddTail(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *newElement*  
 `CObject` Ukazatele, který se má přidat do tohoto seznamu.  
  
 *pNewList*  
 Ukazatel na jiný `CObList` seznamu. Prvky v *pNewList* bude přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první verze **pozice** hodnota nově vloženou elementu.  
  
### <a name="remarks"></a>Poznámky  
 V seznamu nesmí být prázdné před provedením operace.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::AddTail`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Addtail – pozice (void\***  `newElement` **);**<br /><br /> **addtail – void (CPtrList\***  `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Addtail – pozice (const CString &** `newElement` **);**<br /><br /> **Addtail – pozice (LPCTSTR** `newElement` **);**<br /><br /> **addtail – void (CStringList\***  `pNewList` **);**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `AddTail example: A CObList with 2 elements`  
  
 `a CAge at $444A 21`  
  
 `a CAge at $4526 40`  
  
##  <a name="coblist"></a>  CObList::CObList  
 Vytvoří prázdnou `CObject` ukazatel seznamu.  
  
```  
CObList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Členitost přidělení paměti pro rozšíření seznamu.  
  
### <a name="remarks"></a>Poznámky  
 S růstem seznamu jednotek se přidělí paměť *nBlockSize* položky. V případě selhání přidělení paměti `CMemoryException` je vyvolána výjimka.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::CObList`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Příklad  
  Níže je seznam `CObject`-odvozené třídy `CAge` používá ve všech příkladech kolekce:  
  
 [!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 Dole je příklad `CObList` konstruktor využití:  
  
 [!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>  CObList::Find  
 Vyhledá v seznamu postupně k vyhledání prvního `CObject` ukazatel odpovídající zadané `CObject` ukazatel.  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *searchValue*  
 Ukazatel objektu, která se má najít v tomto seznamu.  
  
 *startAfter*  
 Počáteční pozice pro vyhledávání.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud objekt nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že porovnání hodnot ukazatele, nikoli jejich obsah objektů.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::Find`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Najde POZICI (void\***  `searchValue` **, pozice** `startAfter` **= NULL) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Najde POZICI (LPCTSTR** `searchValue` **, pozice** `startAfter` **= NULL) const;**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>  CObList::FindIndex  
 Používá hodnotu *nIndex* jako index do seznamu.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Index založený na nule elementu seznamu nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud *nIndex* je příliš velký. (Rozhraní generuje kontrolní výrazy, pokud *nIndex* je záporná.)  
  
### <a name="remarks"></a>Poznámky  
 Spuštěním kontroly sekvenční z hlavičky v seznamu na *n*element TD.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::FindIndex`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**FindIndex pozice (INT_PTR** `nIndex` **) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**FindIndex pozice (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>  CObList::GetAt  
 Proměnné typu **pozice** je klíč pro seznamu.  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Pozice*  
 A **pozice** hodnoty vrácené předchozí `GetHeadPosition` nebo `Find` volání funkce člen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).  
  
### <a name="remarks"></a>Poznámky  
 Není stejný jako index a nemůže pracovat **pozice** hodnotu sami. `GetAt` načte `CObject` ukazatel přidružené k dané pozici.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& GetAt (pozice** *pozice* **) const;**<br /><br /> **void\*& GetAt (pozice** *pozice* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const CString & GetAt (pozice** *pozice* **) const;**<br /><br /> **CString & GetAt (pozice** *pozice* **);**|  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [FindIndex](#findindex).  
  
##  <a name="getcount"></a>  CObList::GetCount  
 Získá počet elementů v tomto seznamu.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselnou hodnotu obsahující počet elementu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetCount`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount (const;)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount (const;)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>  CObList::GetHead  
 Získá `CObject` ukazatele, který reprezentuje element head tohoto seznamu.  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud v seznamu je přístupné přes ukazatel na **const CObList**, pak `GetHead` vrátí `CObject` ukazatel. To umožňuje funkce, která se použije pouze na pravé straně příkazu přiřazení a tedy chrání před změnou seznamu.  
  
 Pokud v seznamu přistupuje přímo nebo prostřednictvím ukazatele na `CObList`, pak `GetHead` vrátí odkaz na `CObject` ukazatel. To umožňuje funkce, která se použije na obou stranách příkazu přiřazení a proto umožňuje do seznamu položek má být změněn.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `GetHead`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetHead`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetHead const; void\*& GetHead ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const CString & GetHead () const; CString & GetHead ();**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 Následující příklad ukazuje použití `GetHead` na levé straně příkazu přiřazení.  
  
 [!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>  CObList::GetHeadPosition  
 Získá pozici element head tohoto seznamu.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud je seznam prázdný.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetHeadPosition`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE GetHeadPosition (const;)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE GetHeadPosition (const;)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>  CObList::GetNext  
 Získá seznam element identifikovaný *rPosition*, pak nastaví *rPosition* k `POSITION` hodnotu další položky v seznamu.  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rPosition*  
 Odkaz na `POSITION` hodnoty vrácené předchozí `GetNext`, `GetHeadPosition`, nebo jiné členské funkce volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetNext` ve smyčce dopředného iterace Pokud vytvořit počáteční pozice pomocí volání `GetHeadPosition` nebo `Find`.  
  
 Musíte zajistit, aby vaše `POSITION` hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud načtené elementem je poslední v seznamu, pak nová hodnota *rPosition* je nastaven na `NULL`.  
  
 Je možné odebrat element během iterace. Podívejte se na příklad pro [RemoveAt](#removeat).  
  
> [!NOTE]
>  Od verze knihovny MFC 8.0 se změnila const verze této metody vrátit `const CObject*` místo `const CObject*&`.  Tato změna byla provedená tím kompilátor do shoda s standardní C++.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetNext`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `a CAge at $479C 40`  
  
 `a CAge at $46C0 21`  
  
##  <a name="getprev"></a>  CObList::GetPrev  
 Získá seznam element identifikovaný *rPosition*, pak nastaví *rPosition* k `POSITION` hodnotu předchozí položky v seznamu.  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rPosition*  
 Odkaz na `POSITION` hodnoty vrácené předchozí `GetPrev` nebo jiné členské funkce volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `GetPrev` ve smyčce zpětné iterace Pokud vytvořit počáteční pozice pomocí volání `GetTailPosition` nebo `Find`.  
  
 Musíte zajistit, aby vaše `POSITION` hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Pokud je načtený element první v seznamu, pak nová hodnota `rPosition` je nastaven na `NULL`.  
  
> [!NOTE]
>  Od verze knihovny MFC 8.0 se změnila const verze této metody vrátit `const CObject*` místo `const CObject*&`.  Tato změna byla provedená tím kompilátor do shoda s standardní C++.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetPrev`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `a CAge at $421C 21`  
  
 `a CAge at $421C 40`  
  
##  <a name="getsize"></a>  CObList::GetSize  
 Vrátí počet prvků seznamu.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení počet elementů v seznamu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetSize`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; (INT_PTR getsize –)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; (INT_PTR getsize –)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>  CObList::GetTail  
 Získá `CObject` ukazatele, který reprezentuje element tail tohoto seznamu.  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Naleznete v popisu návratovou hodnotu pro [GetHead](#gethead).  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `GetTail`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetTail`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetTail const; void\*& GetTail ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const CString & GetTail () const; CString & GetTail ();**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>  CObList::GetTailPosition  
 Získá umístění prvku tail tohoto seznamu; **NULL** Pokud je seznam prázdný.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud je seznam prázdný.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::GetTailPosition`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE GetTailPosition (const;)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE GetTailPosition (const;)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>  CObList::InsertAfter  
 Přidá element do tohoto seznamu za elementem na zadané pozici.  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Pozice*  
 A **pozice** hodnoty vrácené předchozí `GetNext`, `GetPrev`, nebo `Find` volání funkce člen.  
  
 `newElement`  
 Ukazatel objektu, který má být přidán do tohoto seznamu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::InsertAfter`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE InsertAfter (pozice** *pozice* **, void\***  `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE InsertAfter (pozice** *pozice* **, const CString &** `newElement` **);**<br /><br /> **POZICE InsertAfter (pozice** *pozice* **, LPCTSTR** `newElement` **);**|  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která je stejná jako *pozice* parametr.  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>  CObList::InsertBefore  
 Přidá element do tohoto seznamu před element na zadané pozici.  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Pozice*  
 A **pozice** hodnoty vrácené předchozí `GetNext`, `GetPrev`, nebo `Find` volání funkce člen.  
  
 *newElement*  
 Ukazatel objektu, který má být přidán do tohoto seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci nebo načtení objektu ukazatel; **NULL** Pokud je seznam prázdný.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::InsertBefore`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POZICE InsertBefore (pozice** *pozice* **, void\***  `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POZICE InsertBefore (pozice** *pozice* **, const CString &** `newElement` **);**<br /><br /> **POZICE InsertBefore (pozice** *pozice* **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `InsertBefore example: A CObList with 3 elements`  
  
 `a CAge at $4AE2 40`  
  
 `a CAge at $4B02 65`  
  
 `a CAge at $49E6 21`  
  
##  <a name="isempty"></a>  CObList::IsEmpty  
 Určuje, zda tento seznam neobsahuje žádné elementy.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je tento seznam prázdný; jinak 0.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::IsEmpty`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty (const;)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty (const;)**|  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [RemoveAll](#removeall).  
  
##  <a name="removeall"></a>  CObList::RemoveAll  
 Odebere všechny elementy z tohoto seznamu a uvolní přidruženého `CObList` paměti.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Seznam je prázdný, nevygeneruje se žádná chyba.  
  
 Když odeberete elementy z `CObList`, odeberte objekt ukazatele ze seznamu. Je vaší povinností odstranit objekty sami.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveAll`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void (RemoveAll);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void (RemoveAll);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]  
  
##  <a name="removeat"></a>  CObList::RemoveAt  
 Odebere zadaný element z tohoto seznamu.  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>Parametry  
 *Pozice*  
 Pozice elementu, který chcete odebrat ze seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Když odeberete element z `CObList`, odeberte objekt ukazatele ze seznamu. Je vaší povinností odstranit objekty sami.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (pozice** *pozice* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (pozice** *pozice* **);**|  
  
### <a name="example"></a>Příklad  
  Dávejte pozor při odebírání element během iterace seznamu. Následující příklad ukazuje postup odebrání, který zaručuje platná **pozice** hodnota [GetNext](#getnext).  
  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>  CObList::RemoveHead  
 Odebere element z hlavičky v seznamu a vrátí ukazatel na ni.  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `CObject` Ukazatel dříve na první pozice v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `RemoveHead`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveHead`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>  CObList::RemoveTail  
 Odebere element z konec seznamu a vrátí ukazatel na ni.  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt, který byl na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Ujistěte se, že v seznamu není prázdná před voláním `RemoveTail`. Pokud je seznam prázdný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí. Použití [IsEmpty](#isempty) ověřit, jestli seznam obsahuje elementy.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::RemoveTail`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail ();**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]  
  
##  <a name="setat"></a>  CObList::SetAt  
 Nastaví element na dané pozici.  
  
```  
void SetAt(
    POSITION pos,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 **Pozice** elementu nastavit.  
  
 *newElement*  
 `CObject` Ukazatel má být zapsán do seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Proměnné typu **pozice** je klíč pro seznamu. Není stejný jako index a nemůže pracovat **pozice** hodnotu sami. `SetAt` zapíše `CObject` ukazatel na zadané pozici v seznamu.  
  
 Musíte zajistit, aby vaše **pozice** hodnota představuje platnou místo v seznamu. Pokud je neplatný, ladění verzi knihovny Microsoft Foundation Class se vyhodnotí.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObList::SetAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (pozice** `pos` **, const CString &** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (pozice** `pos` **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](#coblist) seznam `CAge` třídy.  
  
 [!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CStringList – třída](../../mfc/reference/cstringlist-class.md)   
 [CPtrList – třída](../../mfc/reference/cptrlist-class.md)
