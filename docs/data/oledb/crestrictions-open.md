---
title: CRestrictions::Open | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8039d55312687cc28be27f2ed7726b9bda1b44aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097429"
---
# <a name="crestrictionsopen"></a>CRestrictions::Open
Vrátí výsledek nastavena podle uživatelem zadané omezení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [v] Určuje existující relaci objekt používaný pro připojení ke zdroji dat.  
  
 *lpszParam*  
 [v] Určuje omezení na sadu řádků schématu.  
  
 `bBind`  
 [v] Určuje, jestli se automaticky vytvořit vazbu mapu sloupce. Výchozí hodnota je **true**, což způsobí, že mapu sloupce vázat automaticky. Nastavení `bBind` k **false** brání automatické vazby mapu sloupce tak, aby můžete ručně vytvořit vazbu. (Ruční vazba je zajímají hlavně o uživatelům OLAP).  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Můžete zadat maximálně sedm omezení pro sadu řádků schématu.  
  
 V tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) informace o definované omezení na jednotlivých řádků schématu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)