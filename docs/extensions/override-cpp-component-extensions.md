---
title: override (C++vyhodnocovací a C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 8dc7a0a0e6cf759d956fd701d033bd773e572af3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254478"
---
# <a name="override--ccli-and-ccx"></a>override (C++vyhodnocovací a C++/CX)

**Přepsat** kontextové klíčové slovo určuje, že člen typu přepisuje základní třídu nebo člen základního rozhraní.

## <a name="remarks"></a>Poznámky

**Přepsat** – klíčové slovo je platné při kompilaci nativních cílů (výchozí možnost kompilátoru), cílů Windows Runtime (`/ZW` – možnost kompilátoru), nebo cílů modulu CLR (`/clr` – možnost kompilátoru).

Další informace o specifikátorech přepisu naleznete v tématu [specifikátor override](../cpp/override-specifier.md) a [specifikátory přepisu a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Další informace o kontextových klíčových slov najdete v tématu [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, že **přepsat** lze také v nativních kompilacích.

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **přepsat** lze použít v kompilacích prostředí Windows Runtime.

```cpp
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **přepsat** můžete použít v kompilacích modulu runtime common language.

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také:

[override – specifikátor](../cpp/override-specifier.md)<br/>
[override – specifikátory](override-specifiers-cpp-component-extensions.md)