---
title: 'Přepínače/Zc: (Povolit aktualizované __cplusplus – makro)'
ms.date: 05/30/2018
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 89545f541f32374a47dce7f87958e61873c1b47c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315713"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>Přepínače/Zc: (Povolit aktualizované __cplusplus – makro)

**Přepínače/Zc:** umožňuje – možnost kompilátoru  **\_ \_cplusplus** preprocesor makro hlášení aktualizovanou hodnotu pro poslední C++ normy jazykové podpory. Ve výchozím nastavení, Visual Studio vždy vrátí hodnotu "199711L"  **\_ \_cplusplus** makro preprocesoru.

## <a name="syntax"></a>Syntaxe

> **/Zc:__cplusplus**[**-**]

## <a name="remarks"></a>Poznámky

**\_\_Cplusplus** preprocesor makro se běžně používá k podpoře sestavy pro konkrétní verzi standard jazyka C++. Vzhledem k tomu velké množství existujícího kódu se zdá, že budou záviset na hodnotě toto makro odpovídající "199711L", kompilátor nezmění hodnotu makra, pokud je výslovně vyjádřit výslovný souhlas s použitím **přepínače/Zc:** – možnost kompilátoru. **Přepínače/Zc:** možnost je k dispozici od verze Visual Studio 2017 verze 15.7. proto je vypnuto ve výchozím nastavení. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:__cplusplus-** je zadán, vrátí hodnotu "199711 L" Visual Studio pro  **\_ \_cplusplus** Makro preprocesoru. [/ Permissive-](permissive-standards-conformance.md) možnost nepovolíte **přepínače/Zc:**.

Když **přepínače/Zc:** možnost povolená, hlášená hodnota ve  **\_ \_cplusplus** – makro závisí na [/std](std-specify-language-standard-version.md) přepínač verze nastavení. Tato tabulka uvádí možné hodnoty pro makra:

|/Zc:__cplusplus switch|/std:c++ přepínače|__cplusplus hodnota|
|-|-|-|
Zc:__cplusplus|/ std: c ++ 14 (výchozí)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/ std: c ++ nejnovější|201704L
Zc:__cplusplus- (disabled)|Libovolná hodnota|199711L
Nezadáno|Libovolná hodnota|199711L

Kompilátor nepodporuje přepínače standardy pro C ++ 98, C ++ 03 nebo C ++ 11.

Pro citlivější zjišťování změn do sady nástrojů kompilátoru, použijte [_MSC_VER](../../preprocessor/predefined-macros.md) předdefinované makro. Hodnota této předdefinované makro se zvýší, pro každou aktualizaci sady nástrojů v sadě Visual Studio 2017 a novějších verzích. [_MSVC_LANG](../../preprocessor/predefined-macros.md) předdefinované makro hlásí, zda standardní verze **přepínače/Zc:** možnost povolený nebo zakázaný. Když **přepínače/Zc:** je povoleno, `__cplusplus == _MSVC_LANG`.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **přepínače/Zc:** nebo **/Zc:__cplusplus-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také:

- [/Zc (shoda)](zc-conformance.md)
- [/ STD (určení standardní jazykové verze)](std-specify-language-standard-version.md)
- [Předdefinovaná makra](../../preprocessor/predefined-macros.md)
