---
title: "Postupy: přístup ke znakům v datech třídy System::String | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 888370cac57025418bc70b322703d8569a4be3d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Postupy: Přístup ke znakům v datech třídy System::String
Dostanete znaků <xref:System.String> objekt pro vysoce výkonné volání nespravovaných funkcí, které přijímají `wchar_t*` řetězce. Metoda poskytuje vnitřní ukazatel na první znak <xref:System.String> objektu. Ukazatel this můžete manipulovat přímo nebo připnuté a předaný funkci očekává běžný `wchar_t` řetězec.  
  
## <a name="example"></a>Příklad  
 `PtrToStringChars`Vrátí <xref:System.Char>, což je vnitřní ukazatel (také označované jako `byref`). Jako takový je předmětem uvolňování paměti. Nemusíte tento ukazatel připnout, pokud se chystáte předat nativní funkce.  
  
 Vezměte v úvahu následující kód.  Připnutí není nutné, protože `ppchar` je vnitřní ukazatel, a pokud se uvolňování přesune odkazuje na řetězec, bude také aktualizovat `ppchar`. Bez [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md), bude kód pracovat a nebude mít potenciální výkon, což je způsobeno připnutím.  
  
 Pokud předáte `ppchar` nativní funkci, pak musí být připnutý ukazatel; uvolňování nebude možné aktualizovat všechny ukazatele na rámec nespravované zásobníku.  
  
```  
// PtrToStringChars.cpp  
// compile with: /clr  
#include<vcclr.h>  
using namespace System;  
  
int main() {  
   String ^ mystring = "abcdefg";  
  
   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );  
  
   for ( ; *ppchar != L'\0'; ++ppchar )  
      Console::Write(*ppchar);  
}  
```  
  
```Output  
abcdefg  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, kde je potřeba připnutí.  
  
```  
// PtrToStringChars_2.cpp  
// compile with: /clr  
#include <string.h>  
#include <vcclr.h>  
// using namespace System;  
  
size_t getlen(System::String ^ s) {  
   // Since this is an outside string, we want to be secure.  
   // To be secure, we need a maximum size.  
   size_t maxsize = 256;  
   // make sure it doesn't move during the unmanaged call  
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);  
   return wcsnlen(pinchars, maxsize);  
};  
  
int main() {  
   System::Console::WriteLine(getlen("testing"));  
}  
```  
  
```Output  
7  
```  
  
## <a name="example"></a>Příklad  
 Vnitřní ukazatel má všechny vlastnosti nativní ukazatel C++. Například můžete použít provede propojená datová struktura, a to vložení a odstranění pomocí pouze jeden ukazatel:  
  
```  
// PtrToStringChars_3.cpp  
// compile with: /clr /LD  
using namespace System;  
ref struct ListNode {  
   Int32 elem;   
   ListNode ^ Next;  
};  
  
void deleteNode( ListNode ^ list, Int32 e ) {   
   interior_ptr<ListNode ^> ptrToNext = &list;  
   while (*ptrToNext != nullptr) {  
      if ( (*ptrToNext) -> elem == e )  
         *ptrToNext = (*ptrToNext) -> Next;   // delete node  
      else  
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)