---
title: "C3450 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3450
dev_langs: C++
helpviewer_keywords: C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90aa45cc810f8a0d7f869484216a28ea80eaf602
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3450"></a>C3450 chyby kompilátoru
'type': není atribut; Nelze zadat [System::AttributeUsageAttribute] nebo [Windows::Foundation::Metadata::AttributeUsageAttribute]  
  
 Uživatelem definované spravované atributu musí dědit z <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>. Prostředí Windows Runtime atribut musí být definován v `Windows::Foundation::Metadata` oboru názvů.  
  
 Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3450 a ukazuje, jak ji odstranit.  
  
```  
// C3450.cpp  
// compile with: /clr  
// C3450 expected  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref struct AtClass {  
   AtClass(Type ^) {}  
};  
  
[attribute(AttributeTargets::All)]  
ref struct AtClass2 {  
   AtClass2() {}  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
// Delete the following line to resolve.  
ref class B {};  
// Uncomment the following line to resolve.  
// ref class B : Attribute {};  
```