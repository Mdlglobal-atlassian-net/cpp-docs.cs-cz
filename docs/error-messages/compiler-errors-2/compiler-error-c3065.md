---
title: "C3065 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3065
dev_langs: C++
helpviewer_keywords: C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 059493df3a2c805e829bb50311b2fadebbbc575b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3065"></a>C3065 chyby kompilátoru
deklarace vlastnosti v oboru bez třídy není povoleno.  
  
 [Vlastnost](../../cpp/property-cpp.md) __declspec – modifikátor byl použit mimo třídu.  Vlastnost lze deklarovat pouze uvnitř třídy.  
  
 Následující ukázka generuje C3065:  
  
```  
// C3065.cpp  
// compile with: /c  
__declspec(property(get=get_i)) int i;   // C3065  
  
class x {  
public:  
   __declspec(property(get=get_i)) int i;   // OK  
};  
```