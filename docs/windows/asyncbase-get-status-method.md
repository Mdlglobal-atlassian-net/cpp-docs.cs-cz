---
title: Asyncbase::get_status – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1590d07a7b37e7dd3abf09377a03734299cb124c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460955"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status – metoda
Načte hodnotu označující stav asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 *Stav*  
 Umístění, kde má být uložen stav. Další informace najdete v tématu Windows::Foundation::AsyncStatus výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda implementuje `IAsyncInfo::get_Status`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)