---
title: Vyřazování typů a členů (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 661445c8a365451d94f938cfe262623866b0fa5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618631"
---
# <a name="deprecating-types-and-members-ccx"></a>Vyřazování typů a členů (C + +/ CX)

V jazyce C + +/ CX, vyřazení prostředí Windows Runtime typů a členů pro producenty a spotřebiteli pomocí [zastaralé](/uwp/api/windows.foundation.metadata.deprecatedattribute) je atribut podporovaný. Využití rozhraní API, ke kterému tento atribut používá, dostanete zprávu upozornění kompilace, která označuje, že rozhraní API je zastaralé a také doporučuje alternativní rozhraní API pro použití. Ve vlastní veřejné typy a metody můžete použít tento atribut a zadejte vlastní zprávu.

> [!CAUTION]
> [Zastaralé](/uwp/api/windows.foundation.metadata.deprecatedattribute) atribut lze použít pouze s typy Windows Runtime. Standardní C++ tříd a členů, použijte [__declspec(deprecated)](../cpp/deprecated-cpp.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak přestat používat vaše vlastní veřejné rozhraní API – například v součásti prostředí Windows Runtime. Druhý operátor typu [Windows: Foundation:: Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) Určuje, jestli je rozhraní API je zastaralé nebo odebrán. Aktuálně pouze DeprecationType::Deprecated hodnota nepodporuje. Třetí parametr v atributu určuje, [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) pro kterou platí atribut.

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>Podporované cíle

Následující tabulka uvádí konstrukce, na které může být použit atribut zastaralé:

||
|-|
|Ovládací prvek XAML|
|delegát|
|event|
|pole|
|enum|
|struct |
|– metoda|
|třída|
|rozhraní|
|property|
|pole – struktura|
|konstruktorem s parametry|

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)