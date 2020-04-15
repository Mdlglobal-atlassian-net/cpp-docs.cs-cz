---
title: Třída TemplateInstantiationGroup
description: C++ Build Insights SDK TemplateInstantiationGroup odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 18dd48219c7c68ce152c381eb505fe37b19ec8dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324262"
---
# <a name="templateinstantiationgroup-class"></a>Třída TemplateInstantiationGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TemplateInstantiationGroup` se používá s [funkcemi MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k přizpůsobení skupin [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) událostí.

## <a name="syntax"></a>Syntaxe

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní třídy `TemplateInstantiationGroup` [EventGroup\<\> TemplateInstantiation](event-group.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parametry

*Skupiny*\
Skupina [událostí TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

::: moniker-end
