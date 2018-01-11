---
title: "C3099 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3099
dev_langs: C++
helpviewer_keywords: C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a644a27c834efcd3c3857241927a6e618f600d0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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