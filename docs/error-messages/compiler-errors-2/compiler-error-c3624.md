---
title: C3624 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3624
dev_langs:
- C++
helpviewer_keywords:
- C3624
ms.assetid: eaac6a4f-eb11-4e4d-ab12-124ba995c5cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea8ece897ecae5b1d4b0f8f844c4ced50e9da1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257537"
---
# <a name="compiler-error-c3624"></a>C3624 chyby kompilátoru
'type': Tento typ vyžaduje odkaz na sestavení 'assembly.  
  
 Nebyl zadán sestavení (referenční dokumentace) potřebné ke kompilaci kódu; předat sestavení do [#using](../../preprocessor/hash-using-directive-cpp.md) – direktiva.  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3624:  
  
```  
// C3624.cpp  
// compile with: /clr /c  
#using <System.Windows.Forms.dll>  
  
// Uncomment the following 2 lines to resolve.  
// #using <System.dll>  
// #using <System.Drawing.dll>  
  
using namespace System;  
  
public ref class MyForm : public Windows::Forms::Form {};   // C3624  
```  
