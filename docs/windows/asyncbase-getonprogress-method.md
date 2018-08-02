---
title: Asyncbase::getonprogress – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs:
- C++
helpviewer_keywords:
- GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e88509a77c58266c56290b84adfd1e7c143da2ef
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465077"
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress – metoda
Adresa obslužné rutiny události aktuální průběh zkopíruje do zadané proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 *progressHandler*  
 Umístění, kde je uložen adresu obslužné rutiny události aktuální průběh.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)