---
title: Comptr::Attach – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78b5039268bd122ade815ed6040a1df546e0f293
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641327"
---
# <a name="comptrattach-method"></a>ComPtr::Attach – metoda
Přidruží to **ComPtr** s typem rozhraní určeném aktuálním parametru typu šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Ostatní*  
 Typ rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)