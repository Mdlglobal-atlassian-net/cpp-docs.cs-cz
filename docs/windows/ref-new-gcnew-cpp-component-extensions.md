---
title: REF new, gcnew (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: dd78bcb7283cb08f4971192274686710fe22181f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641765"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>REF new, gcnew (C + +/ CLI a C + +/ CX)

**Ref nové** agregační – klíčové slovo přiděluje instance typu, který je uvolněna při objekt přestane být přístupný a, která vrací popisovač ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) na přiřazený objekt.

## <a name="all-runtimes"></a>Všechny moduly runtime

Paměť pro instanci typu, která je přidělena **ref nové** automaticky uvolní.

A **ref nové** vyvolá operaci `OutOfMemoryException` Pokud nelze přidělit paměť.

Další informace o fungování přidělené a přidělení paměti pro nativní typy jazyka C++, naleznete v tématu [nové a odstranit operátory](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Použití **ref nové** přidělení paměti pro objekty modulu Windows Runtime, jehož doba života, které chcete spravovat automaticky. Objekt je automaticky uvolní při jeho počet odkazů dosáhne nuly, které dojde po poslední Kopírovat odkaz má nepřejdou mimo rozsah. Další informace najdete v tématu [referenční třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Je přidělena paměť pro spravovaného typu (typ hodnotou nebo odkazem) **gcnew**a navrácena pomocí uvolňování paměti.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad používá **gcnew** přidělit objekt zprávy.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

Následující příklad používá **gcnew** vytvořit zabalený typ hodnoty pro použití jako typ odkazu.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](../windows/component-extensions-for-runtime-platforms.md)