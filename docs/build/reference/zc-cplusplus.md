---
title: /Zc:__cplusplus (Povolit aktualizované __cplusplus – makro)
ms.custom: ''
ms.date: 05/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:__cplusplus
dev_langs:
- C++
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a796794c0086b09c15ee88442e0fea4d1b114d98
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705794"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (Povolit aktualizované __cplusplus – makro)

**/Zc:__cplusplus** umožňuje – možnost kompilátoru  **\_ \_cplusplus** makro preprocesoru nahlásit aktualizovanou hodnotu pro poslední podpory standardy jazyka C++. Ve výchozím nastavení, Visual Studio vždy vrátí hodnotu "199711L" pro  **\_ \_cplusplus** makro preprocesoru.

## <a name="syntax"></a>Syntaxe

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>Poznámky

**\_ \_Cplusplus** makro preprocesoru se často používá ke sestavy podporu pro konkrétní verzi C++ standard. Protože velké množství existující kód se zdá, závisí na hodnotu této makra odpovídající "199711L", kompilátor nezmění hodnota makra, pokud je výslovně výslovný souhlas s použitím **/Zc:__cplusplus** – možnost kompilátoru. **/Zc:__cplusplus** možnost je k dispozici od Visual Studio 2017 verze 15.7 a ve výchozím nastavení. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:__cplusplus-** je zadán, Visual Studio vrátí hodnotu "199711 L" pro  **\_ \_cplusplus** Makro preprocesoru. [/ Projektovou-](permissive-standards-conformance.md) možnost neumožňuje **/Zc:__cplusplus**.

Při **/Zc:__cplusplus** možnost povolena, hodnota hlášené  **\_ \_cplusplus** makro závisí na [/std](std-specify-language-standard-version.md) verze přepínače nastavení. Tato tabulka obsahuje možné hodnoty pro makro:

|/Zc:__cplusplus přepínače|/std:c++ přepínače|__cplusplus – hodnota|
|-|-|-|
Zc:__cplusplus|/ std: c ++ 14 (výchozí)|201402L
Zc:__cplusplus|/ std: c ++ 17|201703L
Zc:__cplusplus|/ std: c ++ nejnovější|201704L
Zc:__cplusplus-(zakázáno)|Libovolná hodnota|199711L
Není zadaná.|Libovolná hodnota|199711L

Kompilátor C ++ 98, C ++ 03 nebo C ++ 11 standardy přepínače nepodporuje.

Citlivější detekce změn do sady nástrojů kompilátoru použít [_msc_ver –](../../preprocessor/predefined-macros.md) předdefinované makro. Hodnota této integrované makro se zvýší, pro každou aktualizaci sady nástrojů v Visual Studio 2017 a novějších verzích. [_MSVC_LANG](../../preprocessor/predefined-macros.md) předdefinované makro hlásí standardní verzi, jestli **/Zc:__cplusplus** možnost povolená nebo zakázaná. Když **/Zc:__cplusplus** je povoleno, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Zc:__cplusplus** nebo **/Zc:__cplusplus-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také:

- [/Zc (shoda)](zc-conformance.md)
- [/STD (zadejte jazyk standardní verze)](std-specify-language-standard-version.md)
- [Předdefinovaná makra](../../preprocessor/predefined-macros.md)
