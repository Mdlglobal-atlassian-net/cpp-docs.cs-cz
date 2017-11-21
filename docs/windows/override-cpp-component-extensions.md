---
title: "přepsání (C++ Component Extensions) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c16b79d50ad0494956ee27f0928daabfefdacaed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="override--c-component-extensions"></a>override (rozšíření komponent C++)
Klíčové slovo `override` závislé na kontextu značí, že člen typu přepisuje základní třídu nebo člen základního rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 `override` – Klíčové slovo je platný při kompilaci pro nativní cíle (výchozí – možnost kompilátoru), prostředí Windows Runtime cíle (**/ZW** – možnost kompilátoru), nebo common language runtime cílů (**/CLR** kompilátoru možnost).  
  
 Další informace o specifikátorů override najdete v tématu [override – specifikátor](../cpp/override-specifier.md) a [specifikátory Override a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Další informace o kontextově závislá klíčová slova, najdete v části [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu znázorňuje, že klíčové slovo `override` lze použít také v nativních kompilacích.  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Příklad**  
  
 Následující příklad kódu znázorňuje, že klíčové slovo `override` lze použít v kompilacích prostředí Windows Runtime.  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Požadavky**  
  
 – Možnost kompilátoru: **/ZW**  
  
 **Příklad**  
  
 Následující příklad kódu znázorňuje, že klíčové slovo `override` lze použít v kompilacích modulu CLR (Common Language Runtime).  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Požadavky**  
  
 – Možnost kompilátoru:   **/CLR**  
  
## <a name="see-also"></a>Viz také  
 [override – specifikátor](../cpp/override-specifier.md)   
 [Override – specifikátory](../windows/override-specifiers-cpp-component-extensions.md)