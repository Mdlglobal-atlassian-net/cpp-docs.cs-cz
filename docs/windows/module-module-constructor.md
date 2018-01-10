---
title: "Module::module – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::Module
dev_langs: C++
helpviewer_keywords: Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24e74bf30f932fa8029c64d27ce55dd2a75a99aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="modulemodule-constructor"></a>Module::Module – konstruktor
Inicializuje novou instanci třídy modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Module();  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento konstruktor je chráněn a nelze volat pomocí `new` – klíčové slovo. Místo toho volat buď [Module::getmodule – metoda](../windows/module-getmodule-method.md) nebo [Module::Create – metoda](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)