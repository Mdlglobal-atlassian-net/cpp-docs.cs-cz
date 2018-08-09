---
title: Asyncbase::putonprogress – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs:
- C++
helpviewer_keywords:
- PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a99eee63496632b8f0918ee888e6a824424b757d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649887"
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress – metoda
Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
### <a name="parameters"></a>Parametry  
 *progressHandler*  
 Adresy, ke kterému je nastavena obslužná rutina události průběh.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)