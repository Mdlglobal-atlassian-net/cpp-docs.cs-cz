---
title: Třída CPtrArray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrArray
- AFXCOLL/CPtrArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: c23b87a3-bf84-49d6-a66b-61e999d0938a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a8749e54cc42a6ae98748e8a5906cf5a5009d51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cptrarray-class"></a>CPtrArray – třída
Podporuje pole neplatné ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPtrArray : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CPtrArray` jsou podobné funkce člena třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti, můžete použít `CObArray` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CObject` ukazatel jako parametr funkce nebo vrací hodnotu, nahraďte ukazatel na `void`.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 například překládá do  
  
 `void* CPtrArray::GetAt( int <nIndex> ) const;`  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; zvětšování pole v případě potřeby.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli; zvětšování pole v případě potřeby.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje jiného pole k poli; zvětšování pole v případě potřeby.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasné odkaz na element ukazatele v rámci pole.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní všechny nevyužitou paměť nad aktuální horní mez.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet elementů v toto pole.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být `NULL`.|  
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet elementů v toto pole.|  
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|  
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží zadaný index elementu (nebo všechny elementy v jiném poli).|  
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda pole prázdné.|  
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny elementy z tohoto pole.|  
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere element na konkrétním indexu.|  
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daného indexu; pole není povoleno zvětšovat.|  
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daného indexu; zvětšování pole v případě potřeby.|  
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků mají být obsažena v toto pole.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CObArray::operator]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá element v zadaném indexu.|  
  
## <a name="remarks"></a>Poznámky  
 `CPtrArray` zahrnuje `IMPLEMENT_DYNAMIC` makro pro podporu přístupu běhového typu a k vypsání `CDumpContext` objektu. Pokud potřebujete výpis jednotlivé ukazatele prvků pole, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
> [!NOTE]
>  Před použitím pole, použijte `SetSize` k zahájení jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidávání elementů do pole způsobí, že se často znovu přidělit a zkopírovat. Časté opakované přidělení a kopírování jsou neefektivní a může fragmentovat paměti.  
  
 Ukazatel pole nelze serializovat.  
  
 Při odstranění ukazatel pole nebo pokud jeho elementy jsou odebrány, odeberou se jenom ukazatele není entity, které se odkazují.  
  
 Další informace o používání `CPtrArray`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CObArray – třída](../../mfc/reference/cobarray-class.md)
