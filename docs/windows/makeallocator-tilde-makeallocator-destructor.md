---
title: 'MakeAllocator:: ~ MakeAllocator – destruktor | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- ~MakeAllocator, destructor
ms.assetid: f1299c5f-cc6b-4d4e-85d4-aee1be0e2b0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 09450b7883467640cc7176334ea18c07f43a098b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010870"
---
# <a name="makeallocatormakeallocator-destructor"></a>MakeAllocator::~MakeAllocator – destruktor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
~MakeAllocator();  
```  
  
## <a name="remarks"></a>Poznámky  
 Zruší inicializaci aktuální instance **MakeAllocator** třídy.  
  
 V případě potřeby se tento destruktor odstraní také základní přidělené paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Makeallocator – třída](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)