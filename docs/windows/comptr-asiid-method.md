---
title: Comptr::asiid – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32f75c838ea178b1313ab0bf9f005ff2a4c5d75b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652559"
---
# <a name="comptrasiid-method"></a>ComPtr::AsIID – metoda
Vrátí **ComPtr** objekt, který představuje rozhraní, které identifikují pomocí ID zadané rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IUnknown>* p  
) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Identifikátor rozhraní.  
  
 *p*  
 Pokud objekt má rozhraní, jejichž ID se rovná *riid*, dvakrát nepřímé ukazatel na rozhraní určené typem *riid* parametr; jinak vrátí hodnotu, ukazatel na `IUnknown`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)