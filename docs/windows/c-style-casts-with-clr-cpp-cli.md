---
title: "Vrhá stylu jazyka C s - clr (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a47dddb9950378d2b76e30893560dc0c364d7cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-style-casts-with-clr-ccli"></a>Přetypování ve stylu jazyka pomocí možnosti /clr (C++/CLI)
Následující téma se vztahuje pouze na modul Common Language Runtime.  
  
 Při použití s typy CLR, pokusí se kompilátor mapovat stylu jazyka C přetypovat na jednu z položky CAST uvedené níže, v uvedeném pořadí:  
  
1.  const_cast –  
  
2.  safe_cast  
  
3.  safe_cast plus const_cast –  
  
4.  static_cast –  
  
5.  static_cast plus const_cast –  
  
 Pokud žádná z výše uvedené položky CAST není platný, a pokud typ výrazu a typ cíle jsou typy CLR odkazů, mapuje přetypování ve stylu C runtime kontrola (castclass MSIL instrukce). Jinak přetypování ve stylu jazyka C považovány za neplatné a vydá k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Přetypování ve stylu jazyka C se nedoporučuje. Při kompilaci s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), použijte [safe_cast](../windows/safe-cast-cpp-component-extensions.md).  
  
 Následující příklad ukazuje přetypování ve stylu C, která se mapuje `const_cast`.  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 Následující příklad ukazuje přetypování ve stylu C, která se mapuje `safe_cast`.  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 Následující příklad ukazuje přetypování ve stylu C, která se mapuje `safe_cast` plus `const_cast`.  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 Následující příklad ukazuje přetypování ve stylu C, která se mapuje `static_cast`.  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 Následující příklad ukazuje přetypování ve stylu C, která se mapuje `static_cast` plus `const_cast`.  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 Následující příklad ukazuje přetypování ve stylu C který se mapuje na spuštění kontroly.  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 Následující příklad ukazuje neplatný C-styl přetypování, což způsobí, že kompilátor vystavit k chybě.  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)