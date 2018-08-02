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
ms.openlocfilehash: 1a9460664ed58cf39f7b295e1406649ad1d66ca9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467414"
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress – metoda
Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 *progressHandler*  
 Adresy, ke kterému je nastavena obslužná rutina události průběh.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)