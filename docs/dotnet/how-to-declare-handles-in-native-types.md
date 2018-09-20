---
title: 'Postupy: deklarace obslužných rutin v nativních typech | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
f1_keywords:
- gcroot
dev_langs:
- C++
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fbf2934c2d7a1192e55ee9b454f91e7e8cc7037f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431265"
---
# <a name="how-to-declare-handles-in-native-types"></a>Postupy: Deklarace obslužných rutin v nativních typech

Nelze deklarovat typ popisovače v nativním typu. Vcclr.h poskytuje obálku zajišťující bezpečnost typů šablonu `gcroot` k odkazování na objekt CLR z haldy jazyka C++. Tato šablona vám umožní vložit virtuální popisovač v nativním typu a s zacházet, jako by šlo základní typ. Ve většině případů můžete použít `gcroot` objektu jako vložený typ, bez jakékoli přetypování. Nicméně s [u každé v](../dotnet/for-each-in.md), budete muset použít `static_cast` načíst základní referenční informace pro spravované.

`gcroot` Šablony je implementováno pomocí zařízení hodnotová třída System::Runtime, který poskytuje "popisovače" na haldě uvolňování. Všimněte si, že popisovače samy o sobě nejsou vynuceno uvolnění paměti a jsou uvolněny už při použití v destruktoru `gcroot` třídy (Tento destruktor nelze volat ručně). Pokud vytvoříte instanci `gcroot` objektu na nativní haldě, je nutné volat odstranit na tento prostředek.

Modul runtime bude udržovat spojení mezi popisovač a objekt CLR, který odkazuje. Přesun pomocí haldy uvolňování objektu CLR popisovač vrátí novou adresu objektu. Není potřeba připnout předtím, než je přiřazen k proměnné `gcroot` šablony.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit `gcroot` objekt v nativní zásobníku.

```
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

Tento příklad ukazuje, jak vytvořit `gcroot` objektu na nativní haldě.

```
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

Tento příklad ukazuje způsob použití `gcroot` k udržení odkazů na typy hodnot (ne odkazové typy) v nativním typu pomocí `gcroot` na zabalený typ.

```
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

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)