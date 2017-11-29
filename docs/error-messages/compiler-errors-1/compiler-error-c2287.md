---
title: "C2287 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2287
dev_langs: C++
helpviewer_keywords: C2287
ms.assetid: 64556299-4e1f-4437-88b7-2464fc0b95bb
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed8537c7da77da7e5401448e8a6d579cfb4ebe07
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2287"></a>C2287 chyby kompilátoru
'class': reprezentace dědičnosti: 'representation1' je obecné menší než požadované representation2  
  
 Třída je deklarovaný s znázornění jednodušší než vyžaduje.  
  
 Následující ukázka generuje C2287:  
  
```  
// C2287.cpp  
// compile with: /vmg /c  
class __single_inheritance X;  
class __single_inheritance Y;  
  
struct A { };  
struct B { };  
struct X : A, B { };  // C2287  X uses multiple inheritance  
struct Y : A { };  // OK  
```