---
title: Swap – funkce (knihovna šablon C++ prostředí Windows Runtime) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
dev_langs:
- C++
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63c28a18723ad1dc39669ee5a367c870451c9943
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651756"
---
# <a name="swap-function-windows-runtime-c-template-library"></a>Prohození – funkce (knihovna šablon C++ prostředí Windows Runtime)
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW inline void Swap(  
   _Inout_ T& left,  
   _Inout_ T& right  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *doleva*  
 První argument.  
  
 *doprava*  
 Druhý argument.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vymění hodnoty dvou zadaných argumentů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)