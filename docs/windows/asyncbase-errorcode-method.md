---
title: Asyncbase::ErrorCode – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a5f4ccbe1789914f5a7c378f5cb847aaa1c49bb8
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644700"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode – metoda
Získá kód chyby pro aktuální asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Chyba*  
 Umístění, kde tato operace ukládá aktuální kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato operace je bezpečná pro vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)