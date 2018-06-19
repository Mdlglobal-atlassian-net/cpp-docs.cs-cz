---
title: C3839 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbb5541e07d168df36bae83f81b7b8a8a7273665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269511"
---
# <a name="compiler-error-c3839"></a>C3839 chyby kompilátoru
nelze změnit zarovnání ve spravovaných WinRT typu nebo  
  
 Zarovnání proměnných v spravované nebo prostředí Windows Runtime typy řídí CLR nebo prostředí Windows Runtime a nemůže být upraven s [zarovnat](../../cpp/align-cpp.md).  
  
 Následující ukázka generuje C3839:  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
```