---
title: typeof přechází na T::typeid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0ae9f772a68735555748e6edbeb6196f1a73d2c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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