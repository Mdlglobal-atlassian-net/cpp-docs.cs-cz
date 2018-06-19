---
title: C2480 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 987cefa42b3f3f8d9588e446ca181c0b7cd48f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198583"
---
# <a name="compiler-error-c2480"></a>C2480 chyby kompilátoru
"identifikátor": 'přístup z více vláken' platí pouze pro datové položky statický rozsah  
  
 Nelze použít `thread` atribut se automatické proměnné, nestatické datový člen, parametr funkce nebo funkce deklarace nebo definice.  
  
 Použití `thread` atribut pro globální proměnné, členy statických dat a pouze místní statické proměnné.  
  
 Následující ukázka generuje C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```