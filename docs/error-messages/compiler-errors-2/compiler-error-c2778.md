---
title: "C2778 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2778
dev_langs: C++
helpviewer_keywords: C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ce6c780db1442ec254e9b7b9875c9050ef39ef8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2778"></a>C2778 chyby kompilátoru
nesprávně formátovaný GUID v __declspec(uuid())  
  
 Je zadaný nesprávný identifikátor GUID do [uuid](../../cpp/uuid-cpp.md) rozšířených atributů.  
  
 Identifikátor GUID musí být řetězec o délce šestnáctková číslice v následujícím formátu:  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid` Rozšířených atributů přijímá řetězce rozpoznáno [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589), s nebo bez závorek oddělovače.  
  
 Následující ukázka generuje C2778:  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```