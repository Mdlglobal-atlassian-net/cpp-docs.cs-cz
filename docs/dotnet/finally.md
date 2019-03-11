---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: cb2bbdb36a102c7ef8974a9ac210473f2306f5d6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746770"
---
# <a name="finally"></a>finally

Kromě `try` a `catch` klauzule, podporuje pro zpracování výjimek CLR `finally` klauzuli. Sémantika jsou stejné jako `__finally` blokovat v strukturovaných výjimek (SEH) zpracování. A `__finally` můžete postupovat podle bloku `try` nebo `catch` bloku.

## <a name="remarks"></a>Poznámky

Účelem `finally` bloku je vyčistit všechny prostředky zbývající po došlo k výjimce. Všimněte si, `finally` bloku je vždy spuštěn, i v případě, že byla vyvolána žádná výjimka. `catch` Blok se spustí pouze, pokud je spravované výjimky vyvolána v rámci přidruženého `try` bloku.

`finally` je kontextové klíčové slovo; Zobrazit [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace.

## <a name="example"></a>Příklad

Následující příklad ukazuje jednoduchý `finally` blok:

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

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)
