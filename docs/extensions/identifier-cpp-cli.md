---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 80aade53bf1d1c9aa30c4b8c8fe59c2247fe3cfb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034515"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

Umožňuje použít klíčová slova jazyka C++ jako identifikátory.

## <a name="all-platforms"></a>Všechny platformy

### <a name="syntax"></a>Syntaxe

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Poznámky

Použití **__identifier** – klíčové slovo pro identifikátory, které nejsou klíčových slov je povolené, ale důrazně nedoporučuje jak stylu.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

### <a name="examples"></a>Příklady

**Příklad**

V následujícím příkladu třída s názvem **šablony** se vytvoří v jazyce C# a distribuuje jako knihovnu DLL. V C++vyhodnocovací program, který používá **šablony** třídy, **__identifier** – klíčové slovo ukrývá fakt, který **šablony** je standard C++ – klíčové slovo.

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

**__Identifier** – klíčové slovo je platná `/clr` – možnost kompilátoru.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

V následujícím příkladu třída s názvem **šablony** se vytvoří v jazyce C# a distribuuje jako knihovnu DLL. V C++vyhodnocovací program, který používá **šablony** třídy, **__identifier** – klíčové slovo ukrývá fakt, který **šablony** je standard C++ – klíčové slovo.

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)<br/>
[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)