---
title: "C2811 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2811
dev_langs: C++
helpviewer_keywords: C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5a8f38fecb6b139a8e36007affc1a394bd81254
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2811"></a>C2811 chyby kompilátoru
'type1': nemůže Zdědit z 'type2' ref třída může dědit pouze z ref třídy nebo rozhraní – třída  
  
 Jste se pokusili použít nespravované třídu jako základní třída pro třídu spravované.  
  
 Následující ukázka generuje C2811:  
  
```  
// C2811.cpp  
// compile with: /clr /c  
struct S{};  
ref struct T {};  
ref class C : public S {};   // C2811  
ref class D : public T {};   // OK  
```