---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988342"
---
# <a name="finally"></a>finally

Kromě klauzulí `try` a `catch` podporuje zpracování výjimek CLR klauzuli `finally`. Sémantika je shodná s `__finally` blok ve strukturovaném zpracování výjimek (SEH). Blok `__finally` může následovat po bloku `try` nebo `catch`.

## <a name="remarks"></a>Poznámky

Účelem bloku `finally` je vyčištění všech prostředků zbývajících po výskytu výjimky. Všimněte si, že je vždy spuštěn blok `finally`, i když nebyla vyvolána žádná výjimka. `catch` blok je spuštěn pouze v případě, že je vyvolána spravovaná výjimka v rámci přidruženého bloku `try`.

`finally` je kontextově závislé klíčové slovo; Další informace najdete v tématu [Kontextově závislá klíčová slova](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje jednoduchý blok `finally`:

```cpp
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
