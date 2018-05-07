---
title: C3293 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3293
dev_langs:
- C++
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b195a91825b0f20445b29e330f67810329584db7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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