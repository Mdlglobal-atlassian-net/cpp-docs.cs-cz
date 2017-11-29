---
title: "C3838 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3838
dev_langs: C++
helpviewer_keywords: C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2384dcb853b28309eb893d2df6b5083ea14c1e5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3838"></a>C3838 chyby kompilátoru
Nelze explicitně dědí "typ"  
  
 Zadaný `type` nemůže fungovat jako základní třída v žádné třídě.  
  
## <a name="example"></a>Příklad
 Následující ukázka generuje C3838:  
  
```  
// C3838a.cpp  
// compile with: /clr /c  
public ref class B : public System::Enum {};   // C3838  
```  