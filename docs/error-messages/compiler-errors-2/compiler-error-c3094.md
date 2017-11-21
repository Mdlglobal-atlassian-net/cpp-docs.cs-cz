---
title: "C3094 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3094
dev_langs: C++
helpviewer_keywords: C3094
ms.assetid: 10da9b7c-e72d-4013-9925-c83e1bb142db
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: de1d697a3dad13981815dcd9990043da374a4747
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3094"></a>C3094 chyby kompilátoru
'atribut': anonymní využití není povoleno  
  
 Atribut nebyl správně obor.  Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3094.  
  
```  
// C3094.cpp  
// compile with: /clr /c  
using namespace System;  
[AttributeUsage(AttributeTargets::Class)]  
public ref class AAttribute : Attribute {};  
  
[A];   // C3094  
  
// OK  
[A]  
ref class x{};  
```