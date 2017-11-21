---
title: "C2505 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2505
dev_langs: C++
helpviewer_keywords: C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e703a5f36a5edd5febbcfaf4b75394bbbb28ee4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2505"></a>C2505 chyby kompilátoru
'symbol': '__declspec(modifer)' lze použít pouze deklarace nebo definice globální objekty nebo členy statických dat  
  
 A `__declspec` modifikátor, který je navržený pro lze použít pouze v globálním oboru byla použita ve funkci.  
  
 Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [proces](../../cpp/process.md).  
  
 Následující ukázka generuje C2505:  
  
```  
// C2505.cpp  
// compile with: /clr  
  
// OK  
__declspec(process) int ii;  
__declspec(appdomain) int jj;  
  
int main() {  
   __declspec(process) int i;   // C2505  
   __declspec(appdomain) int j;   // C2505  
}  
```