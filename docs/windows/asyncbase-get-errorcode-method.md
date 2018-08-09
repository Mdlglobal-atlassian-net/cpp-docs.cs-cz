---
title: Asyncbase::get_errorcode – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc9ec0c0c68c2941991d0820265b9ee1499bf7cb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650830"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode – metoda
Získá kód chyby pro aktuální asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *Kód chyby*  
 Umístění, kde je uložen aktuální kód chyby.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL, pokud se zavře aktuální asynchronní operace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)