---
title: Ftmbase::disconnectobject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0bb6b6be87736d55eabc6b487101ec68fc16e378
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646137"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject – metoda
Nuceně uvolní všechny externí připojení k objektu. Server objektu zavolá objektu implementace této metody před vypíná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHODIMP DisconnectObject(  
   __in DWORD dwReserved  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwReserved*  
 Vyhrazeno pro budoucí použití; musí být nula.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)