---
title: 'Postupy: Deklarace obslužných rutin v nativních typech'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988245"
---
# <a name="how-to-declare-handles-in-native-types"></a>Postupy: Deklarace obslužných rutin v nativních typech

Typ popisovače nelze deklarovat v nativním typu. Vcclr. h poskytuje `gcroot` šablony obálky s bezpečným typem pro odkazování na objekt CLR z C++ haldy. Tato šablona umožňuje vložit virtuální popisovač do nativního typu a nakládat s ním, jako by se jednalo o nadřízený typ. Ve většině případů můžete použít objekt `gcroot` jako vložený typ bez jakéhokoli přetypování. U [každého v](../dotnet/for-each-in.md)je však nutné použít `static_cast` k načtení základního spravovaného odkazu.

Šablona `gcroot` je implementována pomocí zařízení třídy Value System:: Runtime:: InteropServices:: GCHandle, která poskytuje "Handles" do haldy uvolňování paměti. Všimněte si, že samotné popisovače nejsou sbírány do paměti a jsou uvolněny, pokud je již nepoužívá destruktor ve třídě `gcroot` (Tento destruktor nelze volat ručně). Pokud vytváříte instanci `gcroot` objektu na nativní haldě, je nutné volat metodu DELETE pro daný prostředek.

Modul runtime bude udržovat přidružení mezi popisovačem a objektem CLR, na který odkazuje. Když objekt CLR přesune s haldou uvolňování paměti, popisovač vrátí novou adresu objektu. Proměnnou není nutné připnout předtím, než je přiřazena k šabloně `gcroot`.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit objekt `gcroot` v nativním zásobníku.

```cpp
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit objekt `gcroot` v nativní haldě.

```cpp
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít `gcroot` pro blokování odkazů na typy hodnot (ne odkazových typů) v nativním typu pomocí `gcroot` na zabalený typ.

```cpp
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
