---
title: "C2766 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2766
dev_langs: C++
helpviewer_keywords: C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a74f3808f566c4977d2cffccc0030770e7ae0577
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2766"></a>C2766 chyby kompilátoru
explicitní specializace; 'specializace' již byla definována.  
  
 Duplicitní explicitní specializací nejsou povoleny. Další informace najdete v tématu [explicitní specializace šablon funkcí](../../cpp/explicit-specialization-of-function-templates.md).  
  
 Následující ukázka generuje C2766:  
  
```  
// C2766.cpp  
// compile with: /c  
template<class T>   
struct A {};  
  
template<>   
struct A<int> {};  
  
template<>   
struct A<int> {};   // C2766  
// try the following line instead  
// struct A<char> {};  
```