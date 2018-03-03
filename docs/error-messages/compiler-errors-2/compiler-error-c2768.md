---
title: "C2768 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 42f4c23f36669ae2dd3284d8902f6ba017617201
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2768"></a>C2768 chyby kompilátoru
'function': Neplatné použití explicitní šablony argumenty  
  
 Kompilátor nemohl určete, jestli definici funkce měla být explicitní specializace šablony funkcí, nebo pokud byl v definici funkce měla být pro novou funkci.  
  
 Tato chyba byla zavedena v Visual Studio .NET 2003 jako součást vylepšení shoda kompilátoru.  
  
 Následující ukázka generuje C2768:  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```