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
ms.openlocfilehash: 59354062dded7792dca1cd84683bba64f6a64aa0
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571422"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new – operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>Parametry  
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