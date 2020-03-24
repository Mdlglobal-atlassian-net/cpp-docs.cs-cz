---
title: přepsat (C++/CLI a C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 32c825539efe670528eab7416afefe07d4cb1b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172097"
---
# <a name="override--ccli-and-ccx"></a>přepsat (C++/CLI a C++/CX)

Klíčové slovo **override** -závislé na kontextu označuje, že člen typu Přepisuje základní třídu nebo člen základního rozhraní.

## <a name="remarks"></a>Poznámky

Klíčové slovo **override** je platné při kompilaci pro nativní cíle (výchozí možnost kompilátoru), prostředí Windows Runtime cíle (`/ZW` možnost kompilátoru) nebo cílů společného jazykového modulu Runtime (`/clr` možnost kompilátoru).

Další informace o specifikátorech přepisu naleznete v tématu [specifikátor přepisu](../cpp/override-specifier.md) a [specifikátory přepisu a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Další informace o kontextově závislých klíčových slovech najdete v tématu [klíčová slova závislá na kontextu](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, že **přepsání** lze také použít v nativních kompilacích.

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

Následující příklad kódu ukazuje, že **přepsání** lze použít v prostředí Windows runtimech kompilacích.

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

Možnost kompilátoru: `/ZW`

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že **přepsání** lze použít v kompilacích modulu CLR (Common Language Runtime).

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

Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také

[override – specifikátor](../cpp/override-specifier.md)<br/>
[override – specifikátory](override-specifiers-cpp-component-extensions.md)
