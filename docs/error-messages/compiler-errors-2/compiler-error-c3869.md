---
title: C3869 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3869
dev_langs:
- C++
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcb19652f6b9006783cea4cee687156a0c1fb4b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267509"
---
# <a name="compiler-error-c3869"></a>C3869 chyby kompilátoru
gcnew omezení chybí seznamu prázdný parametr '().  
  
 `gcnew` Byl zadán speciální omezení bez seznamu prázdný parametr. V tématu [omezení obecných parametrů typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3869.  
  
```  
// C3869.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : gcnew   // C3869  
// try the following line instead  
// where T : gcnew()  
ref class List {};  
```