---
title: Event::Operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2aaea1c1c0a036b7c6ba26a9f5df94a72e9ea582
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641792"
---
# <a name="eventoperator-operator"></a>Event::operator= – operátor
Přiřadí zadaný **události** odkaz na aktuální **události** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odkaz rvalue na **události** instance.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální **události** instance.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Event – třída (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-class-windows-runtime-cpp-template-library.md)