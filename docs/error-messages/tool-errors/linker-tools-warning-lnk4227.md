---
title: "Upozornění linkerů Lnk4227 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4227
dev_langs: C++
helpviewer_keywords: LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6ab7c91a9e73a44b3403adb5cfaf77a11713a359
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4227"></a>Upozornění linkerů LNK4227  
  
> operace upozornění metadata (*HRESULT*): *warning_message*  
  
Linkeru zjistil metadata rozdíly při slučování:  
  
-   Jeden nebo více odkazovaných sestaveních s sestavení budou vytvářeny.  
  
-   Jeden nebo více soubory zdrojového kódu v kompilaci.  
  
Například může být způsobeno LNK4227 Pokud máte dva globální funkce se stejným názvem, ale informace o parametrech deklarovaný jinak (tedy deklarace nejsou konzistentní v souborech všech určených ke kompilaci). Použijte ildasm.exe/text/metadata *object_file* na každého souboru .obj zobrazíte, jak se typy liší.  
  
LNK4227 slouží také k hlášení problémů, které pocházejí z jiného nástroje. Vyhledávání zprávy upozornění pro další informace.  
  
K vyřešení upozornění je potřeba opravit problémy, které jsou metadata.  
  
## <a name="example"></a>Příklad  
  
LNK4227 se vygeneruje, když jinak než sestavení, které na ni odkazuje podepsaná odkazované sestavení.  
  
Následující ukázka generuje LNK4227:  
  
```cpp  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 A pak  
  
```cpp  
// LNK4227b.cpp  
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
// Try the following line instead  
// [assembly:AssemblyDelaySignAttribute(false)];  
  
ref class MyClass  
{  
};  
```  
  
## <a name="example"></a>Příklad  
  
LNK4227 lze také generovat při atributů sestavení jsou předávány čísla verze v má nesprávný formát.  ' *' Je specifická pro zápis `AssemblyVersionAttribute`.  Toto upozornění vyřešíte použít pouze čísla v atributech verze jiné než `AssemblyVersionAttribute`.  
  
Následující ukázka generuje LNK4227:  
  
```cpp  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```