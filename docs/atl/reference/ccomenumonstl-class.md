---
title: Ccomenumonstl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ca7b7d38c204d7dd8402b9d610a5800dcef6ced9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883226"
---
# <a name="ccomenumonstl-class"></a>Ccomenumonstl – třída
Tato třída definuje objekt enumerátoru modelu COM na základě kolekce standardní knihovny C++.  
  
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
 *základ*  
 Enumerátor modelu COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) rozhraní.  
  
 *piid*  
 Ukazatel na Identifikátor rozhraní rozhraní enumerátor.  
  
 *T*  
 Typ položky, které jsou vystavené rozhraní enumerátor.  
  
 *kopírování*  
 A [kopírovat zásady](../../atl/atl-copy-policy-classes.md) třídy.  
  
 *CollType*  
 Třída kontejneru standardní knihovny C++.  
  
## <a name="remarks"></a>Poznámky  
 `CComEnumOnSTL` definuje objekt enumerátoru modelu COM na základě kolekce standardní knihovny C++. Tato třída je možné samostatně nebo ve spojení s [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Typické postupy použití této třídy jsou popsány níže. Další informace najdete v tématu [ATL – kolekce a enumerátory](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Použití této třídy s ICollectionOnSTLImpl:  
  
- **Definice TypeDef** specializace této třídy.  
  
-   Použití **typedef** jako konečným argumentem šablony ve specializaci `ICollectionOnSTLImpl`.  
  
 Zobrazit [ATL – kolekce a enumerátory](../../atl/atl-collections-and-enumerators.md) příklad.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Použití této třídy bez ohledu na jejich ICollectionOnSTLImpl:  
  
- **Definice TypeDef** specializace této třídy.  
  
-   Použití **typedef** jako argument šablony ve specializaci `CComObject`.  
  
-   Vytvoření instance `CComObject` specializace.  
  
-   Inicializovat objekt enumerator voláním [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Vrátí enumerátor rozhraní do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [Ienumonstlimpl –](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
## <a name="example"></a>Příklad  
 Kód níže obsahuje obecnou funkci pro zpracování, vytváření a inicializace objekt enumerátoru:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Tuto funkci je možné implementovat `_NewEnum` vlastnost kolekce rozhraní, jak je znázorněno níže:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Tento kód vytvoří **typedef** pro `CComEnumOnSTL` , která zveřejní vektor `CComVariant`s prostřednictvím `IEnumVariant` rozhraní. `CVariantCollection` Třídy jednoduše specializuje `CreateSTLEnumerator` pro práci s objekty tohoto typu výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Ienumonstlimpl –](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections: Ukázce ICollectionOnSTLImpl a CComEnumOnSTL, vlastních tříd zásad kopírování](../../visual-cpp-samples.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl – třída](../../atl/reference/ienumonstlimpl-class.md)
