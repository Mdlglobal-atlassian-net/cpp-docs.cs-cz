---
title: Isbaseofstrict – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db8f315c0589ceb7cd9411873152fe644985818e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Základní typ.  
  
 `Derived`  
 Odvozený typ.  
  
## <a name="remarks"></a>Poznámky  
 Ověřuje, zda je jeden typ základní jiného.  
  
 První šablona testuje, jestli je typ odvozený od základní typ, který může poskytne **true** nebo **false**. Druhá šablona testuje, jestli je typ odvozený od sebe, která vždy dává **false**.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[IsBaseOfStrict::value – konstanta](../windows/isbaseofstrict-value-constant.md)|Určuje, zda jeden typ základní jiného.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)