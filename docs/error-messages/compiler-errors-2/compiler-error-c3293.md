---
title: "C3293 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3293
dev_langs: C++
helpviewer_keywords: C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ccf6bd08b1ca540fcdf46d18631e0ab11c7fe4f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3293"></a>C3293 chyby kompilátoru
"objekt": "default" používat pro přístup k výchozí vlastnost (indexer) pro třídu "typ"  
  
 Indexované vlastnosti se nesprávně získat přístup.  V tématu [postupy: použití vlastnosti v jazyce C + +/ CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) Další informace.  

 **Visual Studio 2017 a novější**: V sadě Visual Studio 2015 a starší, kompilátor v některých případech misidentified výchozí vlastnost jako výchozí indexer. Bylo možné tento problém obejít, na základě identifikátoru "Výchozí" pro přístup k vlastnosti. Alternativní řešení, samotné se stala problematické po výchozí zavedl jako klíčové slovo v C ++ 11. Proto je ve Visual Studio 2017 byly opraveny chyby, které vyžaduje alternativní řešení a kompilátor nyní vyvolá chybu, pokud "Výchozí" se používá pro přístup k výchozí vlastnost pro třídu.
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3293 v sadě Visual Studio 2015 a starší.  
  
```  
// C3293.cpp  
// compile with: /clr /c  
using namespace System;  
ref class IndexerClass {  
public:  
   // default indexer  
   property int default[int] {  
      int get(int index) { return 0; }  
      void set(int index, int value) {}  
   }  
};  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier
  
   String ^s = "Hello";  
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier  
   Console::WriteLine(wc2);  
}  
```