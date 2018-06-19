---
title: C2768 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee0fd3fa213639e70199cfe5653ee2034bc39b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233380"
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