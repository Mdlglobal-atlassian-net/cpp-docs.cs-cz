---
title: Nepoužívané typy a členy (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6cd880af7e206b4c7338e53615594ec2c65c59fc
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740503"
---
# <a name="deprecating-types-and-members-ccx"></a>Nepoužívané typy a členy (C++/CX)

V C++/CX je podporována vyřazení typů prostředí Windows Runtime a členů pro výrobce a uživatele pomocí [nepoužívaného](/uwp/api/windows.foundation.metadata.deprecatedattribute) atributu. Pokud využijete rozhraní API, na které byl tento atribut použit, zobrazí se zpráva s upozorněním při kompilaci, která indikuje, že rozhraní API je zastaralé a také doporučuje alternativní rozhraní API, které se má použít. Ve vlastních veřejných typech a metodách můžete použít tento atribut a dodat svoji vlastní zprávu.

> [!CAUTION]
> [Zastaralý](/uwp/api/windows.foundation.metadata.deprecatedattribute) atribut je použit pouze s typy prostředí Windows Runtime. U standardních C++ tříd a členů použijte [__declspec (zastaralé)](../cpp/deprecated-cpp.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vyřadit vlastní veřejná rozhraní API, například v součásti prostředí Windows Runtime. Druhý parametr typu [Windows: Foundation:: metadata::D eprecationtype](/uwp/api/windows.foundation.metadata.deprecationtype) určuje, jestli je rozhraní API zastaralé nebo odebrané. V současné době je podporovaná jenom hodnota DeprecationType::D eprecated. Třetí parametr v atributu určuje vlastnost [Windows:: Foundation:: metadata::P latform](/uwp/api/windows.foundation.metadata.platformattribute) , na kterou se atribut vztahuje.

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

V následující tabulce jsou uvedeny konstrukce, na které lze použít zastaralý atribut:

| |
|-|
|Ovládací prvek XAML|
|delegát|
|event|
|pole Enum|
|enum|
|struct|
|– metoda|
|třída|
|rozhraní|
|property|
|pole struktury|
|parametrizovaný konstruktor|

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
