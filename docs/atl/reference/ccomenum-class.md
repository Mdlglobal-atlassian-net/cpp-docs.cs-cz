---
title: Ccomenum – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd8fe2120ad42d7df223d05a43591937ffcce6e2
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885386"
---
# <a name="ccomenum-class"></a>Ccomenum – třída
Tato třída definuje objekt enumerátoru modelu COM na základě pole.  
  
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
 *základ*  
 Enumerátor modelu COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) rozhraní.  
  
 *piid*  
 Ukazatel na Identifikátor rozhraní rozhraní enumerátor.  
  
 *T*  
 Typ položky, které jsou vystavené rozhraní enumerátor.  
  
 *kopírování*  
 Homogenní [třídy zásady kopírování](../../atl/atl-copy-policy-classes.md).  
  
 *ThreadModel*  
 Model vláken třídy. Tento parametr výchozí hodnota je globální objektový model vláken použitých v projektu.  
  
## <a name="remarks"></a>Poznámky  
 `CComEnum` definuje objekt enumerátoru modelu COM na základě pole. Tato třída je obdobou [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) který implementuje enumerátor podle kontejneru standardní knihovny C++. Typické postupy použití této třídy jsou popsány níže. Další informace najdete v tématu [ATL – kolekce a enumerátory](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class"></a>Chcete-li použít tuto třídu:  
  
- **Definice TypeDef** specializace této třídy.  
  
-   Použití **typedef** jako argument šablony ve specializaci `CComObject`.  
  
-   Vytvoření instance `CComObject` specializace.  
  
-   Inicializovat objekt enumerator voláním [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).  
  
-   Vrátí enumerátor rozhraní do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [Ccomenumimpl –](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
## <a name="example"></a>Příklad  
 Kód níže obsahuje opakovaně použitelné funkce pro vytváření a inicializaci objekt enumerátoru.  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 Tuto funkci je možné implementovat `_NewEnum` vlastnost kolekce rozhraní, jak je znázorněno níže:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 Tento kód vytvoří **typedef** pro `CComEnum` , která zveřejní vektor varianty prostřednictvím `IEnumVariant` rozhraní. `CVariantArrayCollection` Třídy jednoduše specializuje `CreateEnumerator` pro práci s enumerátor objekty tohoto typu a předá nezbytné argumenty.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Ccomenumimpl – třída](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)
