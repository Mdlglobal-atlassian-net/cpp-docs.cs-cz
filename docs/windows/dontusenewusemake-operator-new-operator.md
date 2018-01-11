---
title: "DontUseNewUseMake::operator new – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs: C++
helpviewer_keywords: operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea5cfa85dcf2873dcb8fe287e251511e3e48dbb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new – operátor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `__unnamed0`  
 Nepojmenovaný parametr, který určuje počet bajtů paměti k přidělení.  
  
 `placement`  
 Typ, který má být přidělen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Poskytuje způsob, jak předat další argumenty, pokud přetížení operátoru `new`.  
  
## <a name="remarks"></a>Poznámky  
 Přetížení operátoru `new` a brání použití v RuntimeClass.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [DontUseNewUseMake – třída](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)