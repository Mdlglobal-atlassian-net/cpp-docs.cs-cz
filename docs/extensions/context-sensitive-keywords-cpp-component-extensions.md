---
title: Kontextově závislá klíčováC++slova ( C++/CLI a/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: 53fcaf13eb56ae14841861bffd1a29376304b8d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182172"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>Kontextově závislá klíčováC++slova ( C++/CLI a/CX)

*Kontextově závislá klíčová slova* jsou prvky jazyka, které jsou rozpoznány pouze v konkrétních kontextech. Mimo konkrétní kontext může být kontextové klíčové slovo uživatelsky definovaný symbol.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="remarks"></a>Poznámky

Následuje seznam klíčových slov, která jsou závislá na kontextu:

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [literal](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [property](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where` (část [obecných typů](generics-cpp-component-extensions.md))

Pro účely čitelnosti můžete chtít omezit použití klíčových slov, která jsou závislá na kontextu, jako uživatelsky definované symboly.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

(Pro tuto funkci nejsou k dispozici žádné poznámky specifické pro platformu.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

(Pro tuto funkci nejsou k dispozici žádné poznámky specifické pro platformu.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, že v příslušném kontextu lze pomocí klíčového slova s kontextovou **vlastností** definovat vlastnost a proměnnou.

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
