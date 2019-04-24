---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: f7db4320cf901412e3a9e3de682d0cfbcc9f23bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223011"
---
# <a name="finally"></a>finally

Kromě `try` a `catch` klauzule, podporuje pro zpracování výjimek CLR `finally` klauzuli. Sémantika jsou stejné jako `__finally` blokovat v strukturovaných výjimek (SEH) zpracování. A `__finally` můžete postupovat podle bloku `try` nebo `catch` bloku.

## <a name="remarks"></a>Poznámky

Účelem `finally` bloku je vyčistit všechny prostředky zbývající po došlo k výjimce. Všimněte si, `finally` bloku je vždy spuštěn, i v případě, že byla vyvolána žádná výjimka. `catch` Blok se spustí pouze, pokud je spravované výjimky vyvolána v rámci přidruženého `try` bloku.

`finally` je kontextové klíčové slovo; Zobrazit [Context-Sensitive Keywords](../extensions/context-sensitive-keywords-cpp-component-extensions.md) Další informace.

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

[Zpracování výjimek](../extensions/exception-handling-cpp-component-extensions.md)
