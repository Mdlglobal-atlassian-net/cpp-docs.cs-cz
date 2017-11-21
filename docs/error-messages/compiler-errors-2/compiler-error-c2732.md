---
title: "C2732 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2732
dev_langs: C++
helpviewer_keywords: C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 38b364ac890118ce90164c3003a76e0d3c2e100d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2732"></a>C2732 chyby kompilátoru
Specifikace propojení v rozporu se starší specifikace 'function'.  
  
 Funkce je již deklarována s specifikátor různých propojení.  
  
 Tato chyba může být způsobena podle zahrnují soubory s specifikátory různých propojení.  
  
 Chcete-li tuto chybu opravit, změňte `extern` příkazy tak, aby souhlas vazby. Konkrétně není zalomen `#include` direktivy v `extern "C"` bloky.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2732:  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```