---
title: VýčtyC++(/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 3bdcff03872dcfe83f0be5752cec4f567fbc6b72
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740215"
---
# <a name="enums-ccx"></a>VýčtyC++(/CX)

C++/CX podporuje `public enum class` klíčové slovo, které se analagous na standard C++ `scoped  enum`. Použijete-li enumerátor deklarovaný `public enum class` pomocí klíčového slova, je nutné použít identifikátor výčtu k určení oboru každé hodnoty enumerátoru.

### <a name="remarks"></a>Poznámky

Objekt `public enum class` , který nemá specifikátor přístupu, `public`jako je, je považován za standardní C++ [vymezený výčet](../cpp/enumerations-cpp.md).

Deklarace `public enum class` nebo`public enum struct` může mít nadřízený typ libovolného integrálního typu, i když prostředí Windows Runtime sám vyžaduje, aby typ byl typu Int32 nebo UInt32 pro výčet příznaků. Následující syntaxe popisuje části `public enum class` nebo. `public enum struct`

Tento příklad ukazuje, jak definovat veřejnou třídu výčtu:

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

Tento další příklad ukazuje, jak ji spotřebovat:

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>Příklady

Další příklady ukazují, jak deklarovat výčet,

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

Další příklad ukazuje, jak přetypovat na číselné ekvivalenty a provést porovnání. Všimněte si, že použití čítače `One` výčtu je vymezeno `Enum1` identifikátorem výčtu a enumerátor `First` je vymezen podle `Enum2`.

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
