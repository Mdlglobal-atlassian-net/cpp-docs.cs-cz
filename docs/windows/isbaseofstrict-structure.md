---
title: Isbaseofstrict – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: d4690c15adac7be66ca916b1fc0f769e6c50190c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017895"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict – struktura
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
### <a name="parameters"></a>Parametry  
 *základ*  
 Základní typ.  
  
 *Odvozené*  
 Odvozeného typu.  
  
## <a name="remarks"></a>Poznámky  
 Ověřuje, zda je jeden typ základ jiného.  
  
 První šablona testuje, jestli typ je odvozen od základního typu, který může přinést **true** nebo **false**. Druhá šablona testuje, jestli je typ odvozený od sebe sama, který vždy dává **false**.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[IsBaseOfStrict::value – konstanta](../windows/isbaseofstrict-value-constant.md)|Označuje, zda je jeden typ základ jiného.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)