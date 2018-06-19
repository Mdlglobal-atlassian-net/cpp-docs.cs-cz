---
title: Event::Operator = – operátor | Microsoft Docs
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
ms.openlocfilehash: d3da41ff7fd145889ec799bb2f8ebe99aed36934
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871120"
---
# <a name="eventoperator-operator"></a>Event::operator= – operátor
Přiřadí zadaný odkaz na aktuální instanci události událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Rvalue – odkaz na instanci události.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální instanci události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Event – třída (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-class-windows-runtime-cpp-template-library.md)