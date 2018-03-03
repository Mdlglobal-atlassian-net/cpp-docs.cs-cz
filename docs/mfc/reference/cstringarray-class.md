---
title: "Třída CStringArray | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
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
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2e9bc2a8f88ce79b6d4c31a4754ad660ecfcbe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cstringarray-class"></a>CStringArray – třída
Podporuje pole [CString](../../atl-mfc-shared/using-cstring.md) objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStringArray : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CStringArray` jsou podobné funkce člena třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti, můžete použít `CObArray` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CObject` ukazatel jako návratová hodnota, nahraďte [CString](../../atl-mfc-shared/using-cstring.md) objektu (není [CString](../../atl-mfc-shared/using-cstring.md) ukazatel). Po zobrazení `CObject` ukazatel jako parametr funkce, nahraďte `LPCTSTR`.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 například překládá do  
  
 `CString CStringArray::GetAt( int <nIndex> ) const;`  
  
 and  
  
 `void SetAt( int <nIndex>, CObject* <newElement> )`  
  
 přeloží na  
  
 `void SetAt( int <nIndex>, LPCTSTR <newElement> )`  
  
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
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může být **NULL**.|  
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
 `CStringArray`zahrnuje `IMPLEMENT_SERIAL` makro pro podporu serializace a vypsání jejích elementů. Pokud pole `CString` objekty ukládána do archivu, a to buď operátor přetížené vložení nebo s `Serialize` – členská funkce, každý prvek serializován naopak.  
  
> [!NOTE]
>  Před použitím pole, použijte `SetSize` k zahájení jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidávání elementů do pole způsobí, že se často znovu přidělit a zkopírovat. Časté opakované přidělení a kopírování jsou neefektivní a může fragmentovat paměti.  
  
 Pokud potřebujete výpis řetězec jednotlivých prvků v poli, musíte nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Když `CString` pole je odstraněna, nebo při jeho prvky jsou odebrány, je uvolnit paměť řetězec podle potřeby.  
  
 Další informace o používání `CStringArray`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



