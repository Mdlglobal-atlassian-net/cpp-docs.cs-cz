---
title: Event::Event konstruktor (knihovna šablon C++ prostředí Windows Runtime) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs:
- C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c2683d2e1875e7d68d27f7bde515b7a4ca70da0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649725"
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event Konstruktor (Knihovna šablon C++ prostředí Windows Runtime)
Inicializuje novou instanci třídy **události** třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Zpracování události. Ve výchozím nastavení *h* je inicializován na **nullptr**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Event – třída (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-class-windows-runtime-cpp-template-library.md)