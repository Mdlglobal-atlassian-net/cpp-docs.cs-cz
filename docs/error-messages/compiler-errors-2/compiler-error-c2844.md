---
title: "C2844 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2844
dev_langs: C++
helpviewer_keywords: C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 45e0a7eb7a8846d90cc8e0743f5484ba1b58208a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2844"></a>C2844 chyby kompilátoru
"člen": nesmí být členem skupiny rozhraní 'rozhraní.  
  
 [Třída rozhraní](../../windows/interface-class-cpp-component-extensions.md) nesmí obsahovat datový člen, pokud je také vlastnost.  
  
 Jakoukoli jinou hodnotu než vlastnost nebo člen funkce není povolena v rozhraní. Kromě toho nejsou povoleny konstruktory, destruktory a operátory.  
  
 Následující ukázka generuje C2844:  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
