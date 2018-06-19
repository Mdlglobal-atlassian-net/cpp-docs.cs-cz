---
title: Třída CStringList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringList
- AFXCOLL/CStringList
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
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a88fc73b27323327bce477fa2cdaca747ed21c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375145"
---
# <a name="cstringlist-class"></a>CStringList – třída
Podporuje seznamy `CString` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStringList : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CStringList` jsou podobné funkce člena třídy [CObList](../../mfc/reference/coblist-class.md). Z důvodu této podobnosti, můžete použít `CObList` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CObject` ukazatel jako návratová hodnota, nahraďte `CString` (není `CString` ukazatel). Po zobrazení `CObject` ukazatel jako parametr funkce nahraďte `LPCTSTR`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 například překládá do  
  
 `CString& CStringList::GetHead() const;`  
  
 and  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 přeloží na  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Vytvoří prázdný seznam.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Přidá do hlavičky seznamu (díky nové head) elementu (nebo všechny elementy v jiném seznamu).|  
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Přidá na konec seznamu (díky nové tail) elementu (nebo všechny elementy v jiném seznamu).|  
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Načte pozici elementu určená hodnotou ukazatele.|  
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Načte pozici elementu určeného index počítaný od nuly.|  
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Získá element na dané pozici.|  
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Vrátí počet prvků v tomto seznamu.|  
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Vrátí element head seznamu (nemůže být prázdný).|  
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Vrátí pozici element head seznamu.|  
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Získá další prvek pro iterace.|  
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Získá předchozí prvek pro iterace.|  
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Vrátí počet prvků v tomto seznamu.|  
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Vrátí element tail seznamu (nemůže být prázdný).|  
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Vrátí pozici tail element seznamu.|  
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Vloží nového elementu za dané pozici.|  
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Vloží nového elementu před dané pozici.|  
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Testy pro prázdný seznam podmínku (žádné elementy).|  
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Odebere všechny elementy z tohoto seznamu.|  
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Odebere element z tohoto seznamu, určeného umístění.|  
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Odebere element z hlavičky v seznamu.|  
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Odebere element z konec seznamu.|  
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Nastaví element na dané pozici.|  
  
## <a name="remarks"></a>Poznámky  
 Všechny porovnání se provádí hodnotu, což znamená, že místo adresy řetězce jsou porovnávány znaky v řetězci.  
  
 `CStringList` zahrnuje `IMPLEMENT_SERIAL` makro pro podporu serializace a vypsání jejích elementů. Pokud seznam `CString` objekty ukládána do archivu, a to buď operátor přetížené vložení nebo s `Serialize` členské funkce se každý `CString` element serializován naopak.  
  
 Pokud potřebujete výpis individuální `CString` elementy, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Další informace o používání `CStringList`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



