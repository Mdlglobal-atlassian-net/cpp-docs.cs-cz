---
title: Třída CComEnumOnSTL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c380ba7b6c2c13f178a15263e1ff510f9f3c31c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363295"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL – třída
Tato třída definuje objekt enumerator COM na základě kolekce standardní knihovna C++.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>  
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
 T,
    Copy,
 CollType>,
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
 A [zkopírujte zásady](../../atl/atl-copy-policy-classes.md) třídy.  
  
 `CollType`  
 Kontejner – třída standardní knihovna C++.  
  
## <a name="remarks"></a>Poznámky  
 `CComEnumOnSTL` definuje objekt enumerator COM na základě kolekce standardní knihovna C++. Tato třída můžete použít samostatně nebo ve spojení s [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Obvyklé kroky pro použití této třídy jsou uvedeny níže. Další informace najdete v tématu [ATL – kolekce a výčty](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Tato třída použití s ICollectionOnSTLImpl:  
  
- `typedef` specializace této třídy.  
  
-   Použití `typedef` jako argument finální šablona v specializace `ICollectionOnSTLImpl`.  
  
 V tématu [ATL – kolekce a výčty](../../atl/atl-collections-and-enumerators.md) příklad.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>K použití této třídy nezávisle na ICollectionOnSTLImpl:  
  
- `typedef` specializace této třídy.  
  
-   Použití `typedef` jako argument šablony v specializace `CComObject`.  
  
-   Vytvoření instance `CComObject` specializace.  
  
-   Inicializovat objekt enumerator voláním [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Vrátí enumerátor rozhraní do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
## <a name="example"></a>Příklad  
 Kód ukazuje následující obrázek poskytuje obecné funkce pro zpracování, vytváření a inicializace objektu enumerátor:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Tato funkce šablony lze použít k implementaci `_NewEnum` vlastnost kolekce rozhraní, jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Tento kód vytvoří `typedef` pro `CComEnumOnSTL` která zveřejňuje vektor `CComVariant`s prostřednictvím **IEnumVariant** rozhraní. **CVariantCollection** třída jednoduše se specializuje **CreateSTLEnumerator** pro práci s enumerátor objekty tohoto typu.  
  
## <a name="see-also"></a>Viz také  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Ukázka ATLCollections: Představuje ICollectionOnSTLImpl, CComEnumOnSTL a vlastní kopie zásady třídy](../../visual-cpp-samples.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl – třída](../../atl/reference/ienumonstlimpl-class.md)
