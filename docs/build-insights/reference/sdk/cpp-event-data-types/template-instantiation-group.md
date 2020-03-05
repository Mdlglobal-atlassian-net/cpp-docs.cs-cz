---
title: TemplateInstantiationGroup – třída
description: Referenční C++ dokumentace třídy TemplateInstantiationGroup sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 281088b4c6cbd39b2fb7677180a7966b490ec3ac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332990"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TemplateInstantiationGroup` se používá s funkcemi [MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ji pro spárování skupin [TEMPLATE_INSTANTIATIONch](../event-table.md#template-instantiation) událostí.

## <a name="syntax"></a>Syntaxe

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své třídy [event\<TemplateInstantiation\>](event-group.md) základní třídy obsahuje Třída `TemplateInstantiationGroup` následující členy:

### <a name="constructors"></a>Konstruktory

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parametry

\ *skupiny*
Skupina [TEMPLATE_INSTANTIATIONch](../event-table.md#template-instantiation) událostí.

::: moniker-end
