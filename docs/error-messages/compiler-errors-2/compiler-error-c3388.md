---
title: "C3388 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3388
dev_langs: C++
helpviewer_keywords: C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4362617295ccbce8f71aeff3e5258f85835fa9bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3388"></a>C3388 chyby kompilátoru
'type': není povolena jako omezení, za předpokladu, že 'ref class'. Chcete-li pokračovat, analýza  
  
 Omezení byl zadán pro obecný typ, ale omezení nebyl zadán správně. V tématu [omezení obecných parametrů typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3388.  
  
```  
// C3388.cpp  
// compile with: /clr /c  
interface class AA {};  
  
generic <class T>  
where T : interface class   // C3388  
ref class C {};  
  
// OK  
generic <class T>  
where T : AA  
ref class D {};  
```