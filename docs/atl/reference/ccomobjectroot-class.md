---
title: "Třída CComObjectRoot | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs: C++
helpviewer_keywords: CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2dc617eeb58594262ea272a0a4ef7da2865b73f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot – třída
Tato definice typu z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) je převést na šablonu na výchozí model serveru vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## <a name="remarks"></a>Poznámky  
 `CComObjectRoot`je `typedef` z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) převést na šablonu na výchozí model serveru vláken. Proto [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) bude odkazovat buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).  
  
 `CComObjectRootEx`zpracovává Správa počet odkaz objektu pro neagregovaná a agregované objekty. Pokud není agregovaný objektu a obsahuje ukazatele na vnější neznámý, pokud je agregovaný objektu drží odkaz počet objektů. Pro agregované objekty `CComObjectRootEx` metody lze použít k vyřešení selhání vnitřní objekt k vytvoření a k ochraně vnější objekt z odstranění, když jsou vydávány vnitřní rozhraní nebo vnitřní objekt se odstraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
## <a name="see-also"></a>Viz také  
 [Členy třídy CComObjectRootEx](http://msdn.microsoft.com/en-us/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)   
 [CComObject – třída](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
