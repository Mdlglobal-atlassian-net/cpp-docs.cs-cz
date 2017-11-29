---
title: "C3397 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3397
dev_langs: C++
helpviewer_keywords: C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 778e57e1071764b63a6293907403bd53a2989372
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3397"></a>C3397 chyby kompilátoru
Inicializace agregace není povolen ve výchozí argumenty  
  
 Pole byla deklarována nesprávně.  V tématu [pole](../../windows/arrays-cpp-component-extensions.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3397.  
  
```  
// C3397.cpp  
// compile with: /clr  
// /clr /c  
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397  
void Func2(array<int> ^p = gcnew array<int> (3));   // OK  
  
int main() {  
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK  
}  
```