---
title: Module::module – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b31e9f1e4536bc124bba359ece10217ef8b7f253
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875250"
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