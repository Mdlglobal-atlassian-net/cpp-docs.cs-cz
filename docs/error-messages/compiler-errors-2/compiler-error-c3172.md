---
title: "C3172 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3390c0f1f566e28bc6a000b2ff570c781c93bc98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3172"></a>C3172 chyby kompilátoru
'module_name': v projektu nelze zadat jiný idl_module – atributy  
  
 [idl_module –](../../windows/idl-module.md) atributy se stejným názvem ale odlišným `dllname` nebo `version` parametry nebyly nalezeny v dva soubory v kompilaci. Pouze jeden jedinečný `idl_module` jeden kompilace lze zadat atribut.  
  
 Identické `idl_module` atributy lze zadat v více než jednoho souboru se zdrojovým kódem.  
  
 Například pokud následující `idl_module` nebyly nalezeny atributy:  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 A pak  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 Kompilátor by vygeneroval C3172 (Všimněte si hodnot jinou verzi).