---
title: override (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6071cef3d5669fda86975bb0f27a2b9b87eeb011
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407267"
---
# <a name="override--c-component-extensions"></a>override (rozšíření komponent C++)

**Přepsat** kontextové klíčové slovo určuje, že člen typu přepisuje základní třídu nebo člen základního rozhraní.

## <a name="remarks"></a>Poznámky

**Přepsat** – klíčové slovo je platné při kompilaci nativních cílů (výchozí možnost kompilátoru), cílů Windows Runtime (`/ZW` – možnost kompilátoru), nebo cílů modulu CLR (`/clr` – možnost kompilátoru).

Další informace o specifikátorech přepisu naleznete v tématu [specifikátor override](../cpp/override-specifier.md) a [specifikátory přepisu a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Další informace o kontextových klíčových slov najdete v tématu [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md).

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

## <a name="see-also"></a>Viz také

[override – specifikátor](../cpp/override-specifier.md)<br/>
[Override – specifikátory](../windows/override-specifiers-cpp-component-extensions.md)