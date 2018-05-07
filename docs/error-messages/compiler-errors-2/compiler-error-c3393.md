---
title: C3393 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3393
dev_langs:
- C++
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db8e60df6c6f8f1d19b55d78b527cca2755f4ca4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3393"></a>C3393 chyby kompilátoru
Chyba syntaxe v klauzuli omezení: "identifikátor" není typu  
  
 Identifikátor předaný omezení, které musí být typu, nebyl typu.  Další informace najdete v tématu [omezení obecných parametrů typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3393:  
  
```  
// C3393.cpp  
// compile with: /clr /c  
void MyInterface() {}  
interface class MyInterface2 {};  
  
generic<typename T>  
where T : MyInterface   // C3393  
// try the following line instead  
// where T : MyInterface2  
ref class R {};  
```