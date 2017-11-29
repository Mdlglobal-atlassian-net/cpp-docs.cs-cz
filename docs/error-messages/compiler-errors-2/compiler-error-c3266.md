---
title: "C3266 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3266
dev_langs: C++
helpviewer_keywords: C3266
ms.assetid: 7375c099-acb7-42f6-898d-57cfefa010b8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bda696e0dd48d4decdec1a9a52ae2a4fdbb7c826
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3266"></a>C3266 chyby kompilátoru
'class': konstruktoru třídy musí mít seznam parametrů, void.  
  
Třída konstruktorů ve třídě pomocí programování/CLR nepřijímají parametry.  
  
Následující ukázka generuje C3266:  
  
```  
// C3266.cpp  
// compile with: /clr  
  
ref class X {  
   static X(int i) { // C3266  
   // try the following line instead  
   // static X() {  
   }  
};  
  
int main() {  
}  
```  