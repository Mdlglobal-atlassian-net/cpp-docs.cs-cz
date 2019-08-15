---
title: Obory názvů Platform, default a CLIC++(/CLI C++a/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: db6c73d6c52bf97aea5d0fbeeeebdeef87f692cc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509764"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Obory názvů Platform, default a CLIC++(/CLI C++a/CX)

Obor názvů kvalifikuje názvy prvků jazyka, aby názvy nebyly v konfliktu s jinak identickými názvy jinde ve zdrojovém kódu. Kolize názvů může například zabránit kompilátoru v rozpoznání [kontextově závislých klíčových slov](context-sensitive-keywords-cpp-component-extensions.md). Obory názvů používá kompilátor, ale ve zkompilovaném sestavení nejsou zachovány.

## <a name="all-runtimes"></a>Všechny moduly runtime

Visual Studio poskytuje výchozí obor názvů pro váš projekt při vytváření projektu. Obor názvů můžete přejmenovat ručně, i když v C++/CX název souboru. winmd se musí shodovat s názvem kořenového oboru názvů.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Další informace naleznete v tématu [obory názvů a viditelnostC++typů (/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```cpp
using namespace cli;
```

### <a name="remarks"></a>Poznámky

C++/CLI podporuje obor názvů **CLI** . Při kompilaci s `/clr`příkazem je odvozen příkaz **using** v oddílu syntax.

Následující jazykové funkce jsou v oboru názvů **CLI** :

- [Pole](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, že je možné použít symbol v oboru názvů **CLI** jako uživatelsky definovaný symbol ve vašem kódu.  Nicméně až to uděláte, budete muset explicitně nebo implicitně kvalifikovat odkazy na element jazyka **CLI** se stejným názvem.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)