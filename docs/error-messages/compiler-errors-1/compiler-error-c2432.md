---
title: "C2432 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2432
dev_langs: C++
helpviewer_keywords: C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d89d894738978359fa0cedb9a9da6c4f9781c135
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2432"></a>C2432 chyby kompilátoru
Neplatný odkaz na 16bitové data v "identifikátor"  
  
 Registrace 16 bitů se používá jako index nebo základní registrace. Kompilátor nepodporuje odkazy na data 16 bitů. zaregistruje 16bitové nelze použít jako index nebo základní registrů při kompilaci pro 32bitový kód.  
  
 Následující ukázka generuje C2432:  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```