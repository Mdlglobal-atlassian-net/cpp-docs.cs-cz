---
title: "Třída CPtrList | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CPtrList
dev_langs: C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9a7d32e202c7184ecbf974dc095c223686d6dff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cptrlist-class"></a>CPtrList – třída
Podporuje seznamy neplatné ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CPtrList` jsou podobné funkce člena třídy [CObList](../../mfc/reference/coblist-class.md). Z důvodu této podobnosti, můžete použít `CObList` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CObject` ukazatel jako parametr funkce nebo vrací hodnotu, nahraďte ukazatel na `void`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 například překládá do  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>Poznámky  
 `CPtrList`zahrnuje `IMPLEMENT_DYNAMIC` makro pro podporu přístupu běhového typu a k vypsání `CDumpContext` objektu. Pokud potřebujete výpis seznamu elementů jednotlivé ukazatele, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Ukazatel zobrazí nelze serializovat.  
  
 Když `CPtrList` je odstraněn objekt, nebo při jeho prvky jsou odebrány, odeberou se jenom ukazatele není entity, které se odkazují.  
  
 Další informace o používání `CPtrList`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CObList – třída](../../mfc/reference/coblist-class.md)