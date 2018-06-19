---
title: C3062 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da507511cb5f091d5d9432bbfeb36951e3f43c6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250563"
---
# <a name="compiler-error-c3062"></a>C3062 chyby kompilátoru
'výčtu': enumerátor vyžaduje hodnotu, protože základní typ je "typ"  
  
 Můžete zadat základní typ pro výčet. Některé typy ale vyžadují, abyste hodnoty přiřadit každý enumerátor.  
  
 Další informace o výčty najdete v tématu [výčet tříd](../../windows/enum-class-cpp-component-extensions.md).  
  
 Následující ukázka generuje C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```