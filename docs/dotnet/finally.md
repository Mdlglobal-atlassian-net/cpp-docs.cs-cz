---
title: Nakonec | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55e2b77fbbcc607d802c4ea9e54d7ef56d473bd5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="finally"></a>finally
Kromě `try` a `catch` klauzule, podporuje zpracování výjimky CLR `finally` klauzule. Sémantika jsou stejné jako `__finally` blokovat v strukturovaného zpracování (SEH) výjimek. A `__finally` můžete postupovat podle bloku `try` nebo `catch` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Účelem `finally` bloku je vyčistit všechny prostředky zbývající po se vyskytla výjimka. Všimněte si, že `finally` bloku je vždy provést, i v případě, že byla vyvolána žádná výjimka. `catch` Bloku je spustit pouze pokud je vyvolána výjimka spravované v rámci přidruženého `try` bloku.  
  
 `finally`je kontextové klíčové slovo; v tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý `finally` bloku:  
  
```  
// keyword__finally.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyException: public System::Exception{};  
  
void ThrowMyException() {  
   throw gcnew MyException;  
}  
  
int main() {  
   try {  
      ThrowMyException();  
   }  
   catch ( MyException^ e ) {  
      Console::WriteLine(  "in catch" );  
      Console::WriteLine( e->GetType() );  
   }  
   finally {  
      Console::WriteLine(  "in finally" );  
   }  
}  
```  
  
```Output  
in catch  
MyException  
in finally  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)