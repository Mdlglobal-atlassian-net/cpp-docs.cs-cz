---
title: "RoInitializeWrapper – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs: C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f6330c78a6bbac5f14e94c253f05515e3d29575
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída
Inicializuje prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Poznámky  
 RoInitializeWrapper je pro vaše pohodlí, která inicializuje prostředí Windows Runtime a vrátí HRESULT určující, zda operace byla úspěšná.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper – konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializuje novou instanci třídy RoInitializeWrapper.|  
|[RoInitializeWrapper::~RoInitializeWrapper – destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Zničí aktuální instance třídy RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() – operátor](../windows/roinitializewrapper-hresult-parens-operator.md)|Načte HRESULT vyprodukované RoInitializeWrapper konstruktor.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)