---
title: VýčtyC++(/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: be11d8d8f38a92fbe4be00eed53dd5226bab0b59
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821750"
---
# <a name="enums-ccx"></a>VýčtyC++(/CX)

C++/CX podporuje klíčové slovo `public enum class`, které se podobá standardnímu C++ `scoped  enum`. Použijete-li enumerátor deklarovaný pomocí klíčového slova `public enum class`, je nutné použít identifikátor výčtu k určení oboru každé hodnoty enumerátoru.

### <a name="remarks"></a>Poznámky

`public enum class`, který nemá specifikátor přístupu, jako je například `public`, se považuje za standardní C++ [vymezený výčet](../cpp/enumerations-cpp.md).

Deklarace `public enum class` nebo `public enum struct` může mít podkladový typ jakéhokoli integrálního typu, i když prostředí Windows Runtime sám o sobě vyžaduje, aby typ byl typu Int32 nebo UInt32 pro výčet příznaků. Následující syntaxe popisuje části `public enum class` nebo `public enum struct`.

Tento příklad ukazuje, jak definovat veřejnou třídu výčtu:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

Tento další příklad ukazuje, jak ji spotřebovat:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Příklady

Další příklady ukazují, jak deklarovat výčet,

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

Další příklad ukazuje, jak přetypovat na číselné ekvivalenty a provést porovnání. Všimněte si, že použití `One` enumerátoru je vymezeno identifikátorem výčtu `Enum1` a `First` výčtu je oborem `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
