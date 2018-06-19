---
title: C2601 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2601
dev_langs:
- C++
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49598223c3f68271065cc6212da19767020c51e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230822"
---
# <a name="compiler-error-c2601"></a>C2601 chyby kompilátoru
'function': definice místní funkcí jsou neplatné  
  
 Definice funkce v rámci funkce pokusu kódu.  
  
 Nebo může být navíc levá složená závorka vašeho zdrojového kódu před umístění C2601 chyby.  
  
 Následující ukázka generuje C2601:  
  
```  
// C2601.cpp  
int main() {  
   int i = 0;  
  
   void funcname(int j) {   // C2601  
      j++;  
   }  
}  
```