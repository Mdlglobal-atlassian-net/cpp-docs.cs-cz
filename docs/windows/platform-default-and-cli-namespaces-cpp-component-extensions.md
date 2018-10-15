---
title: Platform, default a cli obory názvů (C + +/ CLI a C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a70fb5317f42e98ccddb21fe66e328e1cc6f7643
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328022"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>Platform, default a cli obory názvů (C + +/ CLI a C + +/ CX)

Obor názvů kvalifikuje názvy prvků jazyka, aby názvy nebyly v konfliktu s jinak identickými názvy jinde ve zdrojovém kódu. Například kolize názvů může zabránit kompilátor rozpozná [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md). Obory názvů používá kompilátor, ale ve zkompilovaném sestavení nejsou zachovány.

## <a name="all-runtimes"></a>Všechny moduly runtime

Při vytváření projektu sady Visual Studio poskytuje výchozí obor názvů pro váš projekt. Můžete ručně přejmenovat obor názvů, i když v jazyce C + +/ CX název souboru winmd musí odpovídat názvu kořenového oboru názvů.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Další informace najdete v tématu [viditelnost typů a oborů názvů (C + +/ CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```cpp
using namespace cli;
```

### <a name="remarks"></a>Poznámky

C + +/ CLI podporuje **rozhraní příkazového řádku** oboru názvů. Při kompilaci s `/clr`, **pomocí** implikován příkaz v oddílu syntaxe.

Spadají následující funkce jazyka **rozhraní příkazového řádku** obor názvů:

- [Pole](../windows/arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, že je možné použít symbol v **rozhraní příkazového řádku** oboru názvů jako uživatelsky definovaný symbol v kódu.  Nicméně, jakmile to uděláte, budete muset explicitně nebo implicitně kvalifikovat odkazy na **rozhraní příkazového řádku** prvek jazyka se stejným názvem.

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

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](../windows/component-extensions-for-runtime-platforms.md)