---
title: "Literal (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- literal
- literal_cpp
dev_langs:
- C++
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f858e94bf916c2d441cee607739bb9e08da09b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="literal-c-component-extensions"></a>literal (rozšíření komponent C++)
Proměnné (– datový člen) označen jako `literal` v **/CLR** kompilace je nativní ekvivalentem `static const` proměnné.  
  
## <a name="all-platforms"></a>Všechny platformy  
 **Poznámky**  
  
 (Používají se žádné poznámky pro tuto funkci jazyka, které platí pro všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 (Existují žádné poznámky pro tuto funkci jazyka, která se týkají jenom prostředí Windows Runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
  
## <a name="remarks"></a>Poznámky  
 Datový člen označen jako `literal` musí být inicializován, pokud deklarovaný a hodnota musí být konstantní integrální, výčet nebo typ řetězec. Převod z typu inicializace výrazu typu statický const člen dat nesmí vyžadovat převod definovaný uživatelem.  
  
 Není dostatek paměti přidělené pole literálu za běhu; Kompilátor pouze vloží jeho hodnota metadat pro třídu.  
  
 Proměnné označené `static const` nebudete mít k dispozici v metadata pro jiné kompilátory.  
  
 Další informace najdete v tématu [statické](../cpp/storage-classes-cpp.md) a [const](../cpp/const-cpp.md).  
  
 `literal`je kontextová – klíčové slovo. V tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, že `literal` proměnná znamená `static`.  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje vlivu literálu v metadatech:  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 Všimněte si rozdíl v metadatech pro `sc` a `lit`: `modopt` – direktiva se použije pro `sc`, znamená ji můžete ignorovat jinými kompilátory.  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad a vytvořené v C#, odkazuje na metadata vytvořili v předchozím příkladu a zobrazuje vlivu `literal` a `static const` proměnné:  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)