---
title: ref new, gcnew (C++/CLI a C++/CX)
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
ms.openlocfilehash: f7269a62d7899df4eb89f6dd9487310c0fda0b4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181808"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew (C++/CLI a C++/CX)

Klíčové slovo **ref new** přidělí instanci typu, která je uvolněna z paměti, když je objekt nepřístupný a který vrátí popisovač ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) přidělenému objektu.

## <a name="all-runtimes"></a>Všechny moduly runtime

Paměť pro instanci typu, která je přidělena **odkazem ref new** , je automaticky oddělované.

**Nová operace ref** vyvolá `OutOfMemoryException`, pokud není schopna přidělit paměť.

Další informace o tom, jak je přidělena paměť pro nativní C++ typy a které jsou přiděleny, naleznete v tématu [operátory New a DELETE](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Použijte **odkaz New** pro přidělení paměti pro objekty prostředí Windows Runtime, jejichž životnost se má automaticky spravovat. Objekt je automaticky uvolněn, pokud je jeho počet odkazů vrácen na nulu, ke kterému dojde po uplynutí poslední kopie odkazu mimo rozsah. Další informace naleznete v tématu [ref Classes and Structs](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Paměť pro spravovaný typ (typ odkazu nebo hodnoty) je přidělena pomocí **gcnew**a navrácena pomocí uvolňování paměti.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad používá **gcnew** k přidělení objektu zprávy.

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

Následující příklad používá **gcnew** k vytvoření zabaleného typu hodnoty pro použití jako typ odkazu.

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

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
