---
title: __identifier (c + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a96363fcfbc753e727c6cbb6a5efbbb5606b6c40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
Umožňuje použití klíčová slova jazyka Visual C++ jako identifikátory.  
  
## <a name="all-platforms"></a>Všechny platformy  
**Syntaxe**  
  
```  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
**Poznámky**  
  
Použití `__identifier` – klíčové slovo pro identifikátory, které nejsou klíčová slova je povolené, ale důrazně nedoporučuje jako řádu stylu.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 V následujícím příkladu třída s názvem `template` je vytvořené v C# a distribuovaných jako knihovny DLL. V aplikaci Visual C++, která používá `template` třídy, `__identifier` – klíčové slovo ukrývá fakt, na který `template` je standardní C++ – klíčové slovo.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 `__identifier` – Klíčové slovo je platný s **/CLR** – možnost kompilátoru.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 V následujícím příkladu třída s názvem `template` je vytvořené v C# a distribuovaných jako knihovny DLL. V aplikaci Visual C++, která používá `template` třídy, `__identifier` – klíčové slovo ukrývá fakt, na který `template` je standardní C++ – klíčové slovo.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)   
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)