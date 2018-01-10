---
title: "typeof přechází na T::typeid | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 09ec4aef4c8bc68f8a808193b30d86b8519ba881
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="typeof-goes-to-ttypeid"></a>typeof přechází na T::typeid
`typeof` Operátor používá se v spravovaných rozšíření pro C++ byl nahrazen pomocí `typeid` – klíčové slovo v jazyce Visual C++.  
  
 Ve spravovaných rozšíření `__typeof()` operátor vrátí přidruženého `Type*` objektu při předání názvu spravovaného typu. Příklad:  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 V nové syntaxe `__typeof` nahradila další formu `typeid` , který vrací `Type^` Pokud je zadán parametr spravovaného typu.  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## <a name="see-also"></a>Viz také  
 [Obecné jazykové změny (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)