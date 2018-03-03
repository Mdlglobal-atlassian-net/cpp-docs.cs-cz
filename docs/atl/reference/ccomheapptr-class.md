---
title: "Třída CComHeapPtr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8619c050ecc356e1445991b625da00c04f462848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomheapptr-class"></a>CComHeapPtr – třída
Chytré ukazatele třída pro správu haldy ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu k uložení v haldě.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Konstruktor|  
  
## <a name="remarks"></a>Poznámky  
 `CComHeapPtr`odvozená z `CHeapPtr`, ale používá [CComAllocator](../../atl/reference/ccomallocator-class.md) přidělit paměť pomocí rutiny COM. V tématu [CHeapPtr](../../atl/reference/cheapptr-class.md) a [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) pro dostupné metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr  
 Konstruktor  
  
```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Existující objekt `CComHeapPtr`.  
  
### <a name="remarks"></a>Poznámky  
 Ukazatel haldy lze vytvořit volitelně pomocí stávající `CComHeapPtr` objektu. Pokud ano, nové `CComHeapPtr` objekt odpovědnost za správu nový ukazatel a prostředky.  
  
## <a name="see-also"></a>Viz také  
 [CHeapPtr – třída](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrBase – třída](../../atl/reference/cheapptrbase-class.md)   
 [CComAllocator – třída](../../atl/reference/ccomallocator-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
