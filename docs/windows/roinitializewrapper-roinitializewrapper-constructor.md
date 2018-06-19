---
title: Roinitializewrapper::roinitializewrapper – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 64f2af40c671760bb8d4e667c209598c46b24665
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889201"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper – konstruktor
Inicializuje novou instanci třídy RoInitializeWrapper.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 Jeden z výčtů RO_INIT_TYPE, které určuje podpora poskytovaná prostředí Windows Runtime.  
  
## <a name="remarks"></a>Poznámky  
 RoInitializeWrapper – třída volá Windows::Foundation::Initialize (*příznaky*).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HandleT – třída](../windows/handlet-class.md)