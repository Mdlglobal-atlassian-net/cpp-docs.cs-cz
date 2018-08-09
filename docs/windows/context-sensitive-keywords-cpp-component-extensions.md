---
title: Kontextově závislá klíčová slova (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal_CPP
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e362ec513cb7cb14f5fd3abb8a028c6e0eab616b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644226"
---
# <a name="context-sensitive-keywords--c-component-extensions"></a>Kontextově závislá klíčová slova (rozšíření komponent C++)
*Kontextově závislá klíčová slova* jsou prvky jazyka, které jsou rozpoznány pouze v určitém kontextu. Mimo určitý kontext může být kontextové klíčové slovo symbolem definovaným uživatelem.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
### <a name="remarks"></a>Poznámky
  
 Následuje seznam kontextových klíčových slov:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [delegate](../windows/delegate-cpp-component-extensions.md)  
  
-   [event](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each, in](../dotnet/for-each-in.md)  
  
-   [InitOnly.](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`   
  
-   [literál](../windows/literal-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [property](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where` (součást [obecných typů](../windows/generics-cpp-component-extensions.md))  
  
 Pro účely čitelnosti můžete omezit použití kontextových klíčových slov jako uživatelem definované symboly.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
### <a name="remarks"></a>Poznámky  
  
 (Neexistují žádné poznámky specifické pro platformu pro tuto funkci.)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
### <a name="remarks"></a>Poznámky  
  
 (Neexistují žádné poznámky specifické pro platformu pro tuto funkci.)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`  
  
### <a name="examples"></a>Příklady  
  
 Následující příklad kódu ukazuje, že ve vhodném kontextu **vlastnost** kontextové klíčové slovo je možné definovat vlastnost a proměnnou.  
  
```cpp  
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
  
```Output  
100  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)