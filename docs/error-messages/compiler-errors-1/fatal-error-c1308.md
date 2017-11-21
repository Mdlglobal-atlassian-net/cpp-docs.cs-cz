---
title: "Závažná chyba C1308 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1308
dev_langs: C++
helpviewer_keywords: C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9958ccb3daa537f8789d7485822fd623da8c703
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1308"></a>Závažná chyba C1308
propojení sestavení není podporováno  
  
 Je povolený .netmodule jako vstup linkeru, ale není sestavení. Tuto chybu lze generovat, když je proveden pokus o odkaz sestavení zkompilovaného s `/clr:safe`.  
  
 Další informace najdete v tématu [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).  
  
 Následující ukázka generuje C1308:  
  
```  
// C1308.cpp  
// compile with: /clr:safe /LD  
public ref class MyClass {  
public:  
   int i;  
};  
```  
  
 A pak  
  
```  
// C1308b.cpp  
// compile with: /clr /link C1308b.obj C1308.dll  
// C1308 expected  
#using "C1308.dll"  
int main() {  
   MyClass ^ my = gcnew MyClass();  
}  
```