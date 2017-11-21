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
ms.openlocfilehash: 8b94db5e54089fa91c3b79c185df8b366de07c38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Roinitializewrapper::roinitializewrapper – konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializuje novou instanci třídy RoInitializeWrapper.|  
|[RoInitializeWrapper:: ~ roinitializewrapper – destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Zničí aktuální instance třídy RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Roinitializewrapper:: HRESULT() – operátor](../windows/roinitializewrapper-hresult-parens-operator.md)|Načte HRESULT vyprodukované RoInitializeWrapper konstruktor.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: wrappers – Namespace](../windows/microsoft-wrl-wrappers-namespace.md)