---
title: DontUseNewUseMake::operator new – operátor | Dokumentace Microsoftu
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
ms.openlocfilehash: b849c7578b29a3d4595a9ecd07c4339dc751e9dd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652946"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new – operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *__unnamed0*  
 Nepojmenovaný parametr, který určuje počet bajtů paměti k přidělení.  
  
 *umístění*  
 Typ, který má být přiděleny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Poskytuje způsob, jak předat další argumenty, pokud přetížíte operátor **nové**.  
  
## <a name="remarks"></a>Poznámky  
 Přetížení operátoru **nové** a brání použití v `RuntimeClass`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Dontusenewusemake – třída](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)