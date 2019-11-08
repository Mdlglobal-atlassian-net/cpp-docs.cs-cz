---
title: C/C++ – referenční dokumentace preprocesoru
ms.date: 10/31/2019
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: ef93f2cb98a033eed539ffc25559937b274d8a21
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754079"
---
# <a name="cc-preprocessor-reference"></a>C/C++ – referenční dokumentace preprocesoru

*Referenční dokumentace CC++ /preprocesoru* vysvětluje preprocesor, jak je implementován v Microsoft C/.C++ Preprocesor provádí předběžné operace se soubory C a C++ před jejich předáním do kompilátoru. Můžete použít preprocesor pro podmíněné kompilování kódu, vkládání souborů, určení chybových zpráv při kompilaci a použití pravidel specifických pro konkrétní počítač pro oddíly kódu.

V aplikaci Visual Studio 2019 možnost kompilátoru [/Experimental: preprocesor](../build/reference/experimental-preprocessor.md) umožňuje novou implementaci preprocesoru. Nová implementace stále probíhá, a proto je považována za experimentální. Je žádoucí, aby byl nakonec vyhovující C99, C11 a C++ 20. Další informace najdete v tématu [MSVC experimentální preprocesor – přehled](preprocessor-experimental-overview.md).

## <a name="in-this-section"></a>V tomto oddílu

\ [preprocesoru](preprocessor.md)
Poskytuje přehled tradičních a nových experimentálních preprocesorů.

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)\
Popisuje direktivy, které se obvykle používají k snadné změně zdrojových programů a jejich snadné kompilaci v různých prostředích pro spuštění.

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)\
Popisuje čtyři operátory pro preprocesory, které jsou používány v kontextu direktivy `#define`.

[Předdefinovaná makra](../preprocessor/predefined-macros.md)\
Popisuje Předdefinovaná makra, která jsou určena ANSI C++a Microsoftem.

[Direktivy pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
Popisuje direktivy pragma, které nabízejí způsob, jakým každý kompilátor nabízí funkce specifické pro počítač a operační systém při zachování celkové kompatibility s jazyky C a C++ .

## <a name="related-sections"></a>Související oddíly

Referenční informace o jazyce\ [ C++ ](../cpp/cpp-language-reference.md)
Poskytuje referenční materiály pro implementaci C++ jazyka od Microsoftu.

\ [Referenční dokumentace jazyka C](../c-language/c-language-reference.md)
Poskytuje referenční materiály pro implementaci jazyka C od společnosti Microsoft.

[Referenční\C++ C/sestavení](../build/reference/c-cpp-building-reference.md)
Obsahuje odkazy na témata, která pojednávají o možnostech kompilátoru a linkeru.

[Projekty sady Visual Studio C++ –](../build/creating-and-managing-visual-cpp-projects.md)\
Popisuje uživatelské rozhraní v aplikaci Visual Studio, které umožňuje určit adresáře, ve kterých bude systém projektu vyhledávat soubory pro váš C++ projekt.
