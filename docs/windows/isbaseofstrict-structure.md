---
title: "Isbaseofstrict – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs: C++
helpviewer_keywords: IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fd3d232094ed9a56db9cd0e14776ca0ec9eca8c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Isbaseofstrict::Value – konstanta](../windows/isbaseofstrict-value-constant.md)|Určuje, zda jeden typ základní jiného.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)