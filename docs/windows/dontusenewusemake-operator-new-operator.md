---
title: DontUseNewUseMake::operator new – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9785ea27c79ff0a118ff3697a22804c520b265ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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