---
title: "Kontextově závislá klíčová slova (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: internal_CPP
dev_langs: C++
helpviewer_keywords: context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68ff63d5b596d575f26ec0f56a3ac7a568c8471e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="context-sensitive-keywords--c-component-extensions"></a>Kontextově závislá klíčová slova (rozšíření komponent C++)
*Kontextově závislá klíčová slova* jsou jazykové elementy, které jsou rozpoznány jenom v konkrétní kontexty. Mimo kontext určité kontextové klíčové slovo lze symbol definovaný uživatelem.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Poznámky**  
  
 Následuje seznam kontextově závislá klíčová slova:  
  
-   [abstraktní](../windows/abstract-cpp-component-extensions.md)  
  
-   [Delegát](../windows/delegate-cpp-component-extensions.md)  
  
-   [události](../windows/event-cpp-component-extensions.md)  
  
-   [Nakonec](../dotnet/finally.md)  
  
-   [pro každou v](../dotnet/for-each-in.md)  
  
-   [InitOnly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`   
  
-   [literál](../windows/literal-cpp-component-extensions.md)  
  
-   [přepsání](../windows/override-cpp-component-extensions.md)  
  
-   [Vlastnost](../windows/property-cpp-component-extensions.md)  
  
-   [zapečetěná](../windows/sealed-cpp-component-extensions.md)  
  
-   `where`(součástí [obecné typy](../windows/generics-cpp-component-extensions.md))  
  
 Pro účely čitelnost můžete omezit používání kontextově závislá klíčová slova jako uživatelem definované symboly.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 (Používají se žádné poznámky specifických pro platformy pro tuto funkci.)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 (Používají se žádné poznámky specifických pro platformy pro tuto funkci.)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že v odpovídající kontext `property` kontextová – klíčové slovo lze použít k definování vlastností a proměnné.  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **Výstup**  
  
```Output  
100  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)