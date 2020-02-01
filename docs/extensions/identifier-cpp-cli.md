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
ms.openlocfilehash: 395f1443f4eef16d9eea44c23a6e3288daf03d14
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912840"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Povoluje použití C++ klíčových slov jako identifikátorů.

## <a name="all-platforms"></a>Všechny platformy

### <a name="syntax"></a>Syntaxe

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Poznámky

Použití klíčového slova **__identifier** u identifikátorů, které nejsou klíčovými slovy, je povoleno, ale důrazně nedoporučujeme, aby se jednalo o styl.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

### <a name="examples"></a>Příklady

**Příklad**

V následujícím příkladu je třída s názvem **template** vytvořena v C# a distribuována jako knihovna DLL. V programu C++/CLI, který používá třídu **šablony** , klíčové slovo **__identifier** skrývá fakt, že **Šablona** je standardní C++ klíčové slovo.

```csharp
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

Klíčové slovo **__identifier** je platné s možností kompilátoru `/clr`.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

V následujícím příkladu je třída s názvem **template** vytvořena v C# a distribuována jako knihovna DLL. V programu C++/CLI, který používá třídu **šablony** , klíčové slovo **__identifier** skrývá fakt, že **Šablona** je standardní C++ klíčové slovo.

```csharp
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