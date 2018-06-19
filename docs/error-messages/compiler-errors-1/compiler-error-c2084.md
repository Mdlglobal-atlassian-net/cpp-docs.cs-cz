---
title: C2084 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce1510dd6e78b8774d3cc433f583c16cdbb8d06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33173874"
---
# <a name="compiler-error-c2084"></a>C2084 chyby kompilátoru
Funkce '*funkce*se již text  
  
 Funkce již byl definován.  
  
 Ve verzích než Visual Studio 2002, Visual C++  
  
-   Kompilátor by více specializací šablony, které se přeložit na stejnou skutečný typ přijmout, i když další definice nikdy nebude k dispozici. Kompilátor nyní zjistí tyto několik definic.  
  
-   `__int32` a `int` byly zpracovány jako samostatné typy. Kompilátor teď zpracovává `__int32` jako synonymum pro `int`. To znamená, že kompilátor zjistí několik definic, funkce při přetížení na obou `__int32` a `int` a vrátí chybu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2084:  
  
```cpp  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
Chcete-li opravit tuto chybu, odeberte duplicitní definice:  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```