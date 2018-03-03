---
title: "Třída CComEnum | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 792c5ff95858936d38d9a87350dd3ca405c5ec66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomenum-class"></a>CComEnum – třída
Tato třída definuje objekt enumerator COM na základě pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>  
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
 T,
    Copy>,
 public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Enumerátor COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) rozhraní.  
  
 `piid`  
 Ukazatel na hodnotu Identifikátoru rozhraní enumerátor.  
  
 `T`  
 Typ položky, které jsou vystavené rozhraní enumerátor.  
  
 `Copy`  
 Homogenní [zkopírujte zásady třída](../../atl/atl-copy-policy-classes.md).  
  
 `ThreadModel`  
 Model vláken třídy. Tento parametr výchozí globální objektový model vláken použít ve vašem projektu.  
  
## <a name="remarks"></a>Poznámky  
 `CComEnum`definuje objekt enumerator COM na základě pole. Tato třída je obdobou [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) které implementuje enumerátor podle kontejner standardní knihovna C++. Obvyklé kroky pro použití této třídy jsou uvedeny níže. Další informace najdete v tématu [ATL – kolekce a výčty](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class"></a>K použití této třídy:  
  
- `typedef`specializace této třídy.  
  
-   Použití `typedef` jako argument šablony v specializace `CComObject`.  
  
-   Vytvoření instance `CComObject` specializace.  
  
-   Inicializovat objekt enumerator voláním [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).  
  
-   Vrátí enumerátor rozhraní do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
## <a name="example"></a>Příklad  
 Kód ukazuje následující obrázek poskytuje opakovaně použitelné funkce pro vytváření a inicializace objektu enumerátor.  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 Tato funkce šablony lze použít k implementaci `_NewEnum` vlastnost kolekce rozhraní, jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 Tento kód vytvoří `typedef` pro `CComEnum` která zveřejňuje vektor **VARIANT**s prostřednictvím **IEnumVariant** rozhraní. **CVariantArrayCollection** třída jednoduše se specializuje **CreateEnumerator** pro práci s enumerátor objekty tohoto typu a předává potřebné argumenty.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [CComEnumImpl – třída](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)
