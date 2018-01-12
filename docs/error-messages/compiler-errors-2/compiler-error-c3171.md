---
title: "C3171 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3171
dev_langs: C++
helpviewer_keywords: C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed053e37dfbf5f3c85cf1f8ec44912eca3148315
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3171"></a>C3171 chyby kompilátoru
'module': nelze zadat jiný modul atributy v projektu  
  
 [modul](../../windows/module-cpp.md) v dva soubory v kompilaci byly nalezeny atributy s jiným parametrem seznamy. Pouze jeden jedinečný `module` jeden kompilace lze zadat atribut.  
  
 Identické `module` atributy lze zadat v více než jednoho souboru se zdrojovým kódem.  
  
 Například pokud následující `module` nebyly nalezeny atributy:  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 A pak  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 Kompilátor by vygeneroval C3171 (Všimněte si hodnot jinou verzi).