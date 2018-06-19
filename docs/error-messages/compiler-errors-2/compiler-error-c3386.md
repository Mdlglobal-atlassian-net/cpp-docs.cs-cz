---
title: C3386 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3386
dev_langs:
- C++
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d378c92fbeff4e8738450e2e49c42c00bd46a6c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258072"
---
# <a name="compiler-error-c3386"></a>C3386 chyby kompilátoru
'type': __declspec(dllexport) /\__declspec(dllimport) nelze použít pro spravované nebo WinRTtype  
  
 `dllimport` a [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modifikátory nejsou platná na spravované nebo prostředí Windows Runtime typu.  
  
 Následující ukázka generuje C3386 a ukazuje, jak to opravit:  
  
```  
// C3386.cpp  
// compile with: /clr /c  
ref class __declspec(dllimport) X1 {   // C3386  
// try the following line instead  
// ref class X1 {  
};  
```