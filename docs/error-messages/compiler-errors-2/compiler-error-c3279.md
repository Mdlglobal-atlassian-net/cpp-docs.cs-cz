---
title: C3279 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a86f3dd637f84901559c4be8443a81425347237
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3279"></a>C3279 chyby kompilátoru
částečné a explicitní specializací také jako explicitní instancí možnosti šablony třídy deklarované v oboru názvů rozhraní příkazového řádku nejsou povoleny.  
  
 `cli` Obor názvů je definován společností Microsoft a obsahuje pseudo šablony. Visual C++ compiler neumožňuje definovaný uživatelem, částečné a explicitní specializací a explicitní instancí možnosti šablony třídy v tomto oboru názvů.  
  
 Následující ukázka generuje C3279:  
  
```  
// C3279.cpp  
// compile with: /clr  
namespace cli {  
   template <> ref class array<int> {};   // C3279  
   template <typename T> ref class array<T, 2> {};   // C3279  
}  
```