---
title: TemplateInstantiation – třída
description: Referenční C++ dokumentace třídy TemplateInstantiation sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2c94f8d3a4613e072c03f6dd4c846798d3d2122b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332969"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TemplateInstantiation` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) události.

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

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `TemplateInstantiation` následující členy:

### <a name="constructors"></a>Konstruktory

[TemplateInstantiation](#template-instantiation)

### <a name="functions"></a>Functions

[Druh](#kind)
[PrimaryTemplateSymbolKey](#primary-template-symbol-key)
[SpecializationSymbolKey](#specialization-symbol-key)

## <a name="kind"></a>Plnění

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>Návratová hodnota

Kód popisující typ vytvoření instance šablony, který byl proveden.

## <a name="primary-template-symbol-key"></a>PrimaryTemplateSymbolKey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>Návratová hodnota

Číselný identifikátor pro typ šablony, který byl specializovaný. Tento identifikátor je jedinečný v rámci front-endového průchodu kompilátoru.

## <a name="specialization-symbol-key"></a>SpecializationSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>Návratová hodnota

Číselný identifikátor typu specializace. Tento identifikátor je jedinečný v rámci front-endového průchodu kompilátoru.

## <a name="template-instantiation"></a>TemplateInstantiation

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) .

::: moniker-end
