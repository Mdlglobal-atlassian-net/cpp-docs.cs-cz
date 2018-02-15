---
title: CAccessorBase::GetHAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
dev_langs:
- C++
helpviewer_keywords:
- GetHAccessor method
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a078ddcbeffc96af35274746de8f052cc6c38810
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="caccessorbasegethaccessor"></a>CAccessorBase::GetHAccessor
Načte popisovač přistupujícího objektu zadaného přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      HACCESSOR GetHAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `nAccessor`  
 [v] Číslo nula posun přistupujícího objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Popisovač přistupujícího objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CAccessorBase – třída](../../data/oledb/caccessorbase-class.md)