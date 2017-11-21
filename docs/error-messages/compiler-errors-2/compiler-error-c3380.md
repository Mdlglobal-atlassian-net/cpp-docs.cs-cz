---
title: "C3380 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3380
dev_langs: C++
helpviewer_keywords: C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b06f57795cea7dda7b3ba2797f7c57026a9acf60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3380"></a>C3380 chyby kompilátoru
'class': Neplatné sestavení přístup specifikátor - pouze 'veřejné' nebo 'privátní, jsou povolené.  
  
 Při použití spravovaných třídě nebo struktuře, [veřejné](../../cpp/public-cpp.md) a [privátní](../../cpp/private-cpp.md) klíčová slova označuje, zda se třída zveřejní prostřednictvím metadata sestavení. Pouze `public` nebo `private` můžete použít pro třídu v programu kompilovat s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 `ref` a `value` klíčová slova, pokud se používá s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), znamenat, že třída je spravované (viz [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md)).  
  
 Následující ukázka generuje C3380:  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  
