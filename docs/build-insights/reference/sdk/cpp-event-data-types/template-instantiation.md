---
title: Třída TemplateInstantiation
description: C++ Build Insights SDK TemplateInstantiation odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ba8fd10efc6a536c9160f10b19e19e17bfaaad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324224"
---
# <a name="templateinstantiation-class"></a>Třída TemplateInstantiation

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TemplateInstantiation` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

## <a name="syntax"></a>Syntaxe

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `TemplateInstantiation` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[ŠablonaVytvoření](#template-instantiation)

### <a name="functions"></a>Functions

[Druh](#kind)
[PrimaryTemplateSymbolSymbolSpecializationSymbolKey](#primary-template-symbol-key)
[SpecializationSymbolKey](#specialization-symbol-key)

## <a name="kind"></a><a name="kind"></a>Druhu

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód popisující typ vytvoření instance šablony.

## <a name="primarytemplatesymbolkey"></a><a name="primary-template-symbol-key"></a>Primární klíč symbolů šablony

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>Návratová hodnota

Číselný identifikátor pro typ šablony, který byl specializovaný. Tento identifikátor je jedinečný v rámci front-endového průchodu kompilátoru.

## <a name="specializationsymbolkey"></a><a name="specialization-symbol-key"></a>SpecializaceSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>Návratová hodnota

Číselný identifikátor pro typ specializace. Tento identifikátor je jedinečný v rámci front-endového průchodu kompilátoru.

## <a name="templateinstantiation"></a><a name="template-instantiation"></a>ŠablonaVytvoření

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

::: moniker-end
