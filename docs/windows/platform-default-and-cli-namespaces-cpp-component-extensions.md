---
title: "Platform, default a rozhraní příkazového řádku obory názvů (C++ Component Extensions) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- lang
- cli
dev_langs: C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bde9c1d76c2c8196f7773a8af042acb2ef0d2d89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Obory názvů Platform, default a cli (rozšíření komponent C++)
Obor názvů kvalifikuje názvy prvků jazyka, aby názvy nebyly v konfliktu s jinak identickými názvy jinde ve zdrojovém kódu. Například kolize názvů může zabránit kompilátor rozpozná [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md). Obory názvů používá kompilátor, ale ve zkompilovaném sestavení nejsou zachovány.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 Při vytváření projektu poskytuje jazyk Visual C++ výchozí obor názvů pro váš projekt. Můžete ručně přejmenujte obor názvů, i když v prostředí Windows Runtime musí odpovídat názvu souboru .winmd název kořenového oboru názvů.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Další informace najdete v tématu [obory názvů a Typ viditelnosti (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Syntaxe**  
  
```  
using namespace cli;  
```  
  
 **Poznámky**  
  
 C + +/ CLI podporuje `cli` oboru názvů. Při kompilaci s **/CLR**, `using` je implicitní příkazu v části syntaxe.  
  
 V jsou následující funkce jazyka `cli` obor názvů:  
  
-   [Pole](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje, že je možné použít symbol v `cli` oboru názvů jako uživatelem definované symbol v kódu.  Nicméně Jakmile provedete, budete muset explicitně nebo implicitně kvalifikaci vaše odkazy na `cli` jazyk element se stejným názvem.  
  
```  
// cli_namespace.cpp  
// compile with: /clr  
using namespace cli;  
int main() {  
   array<int> ^ MyArray = gcnew array<int>(100);  
   int array = 0;  
  
   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062  
  
   // OK  
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);  
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)