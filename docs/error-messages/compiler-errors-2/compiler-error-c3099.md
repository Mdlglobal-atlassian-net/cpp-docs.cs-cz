---
title: C3099 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3099
dev_langs:
- C++
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27059beb1cb587b9060da8c5cc5702ea966422f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249752"
---
# <a name="compiler-error-c3099"></a>C3099 chyby kompilátoru
'– klíčové slovo': použijte [System::AttributeUsageAttribute] pro spravované atributy; použití [Windows::Foundation::Metadata::AttributeUsageAttribute] WinRT atributů  
  
 Použití <xref:System.AttributeUsageAttribute> deklarovat **/CLR** atributy. Použití `Windows::Foundation::Metadata::AttributeUsageAttribute` deklarovat prostředí Windows Runtime atributy.  
  
 Další informace o atributech/CLR najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md). Podporovaných atributů v prostředí Windows Runtime, najdete v části [Windows.Foundation.Metadata obor názvů](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3099 a ukazuje, jak ji odstranit.  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```