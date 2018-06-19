---
title: '-Zc: auto (odvození typu proměnné) | Microsoft Docs'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caa64f64b75145c850c6f6393570dc3f9ba0b0d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379572"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (odvození typu proměnné)

**/Zc: Auto [-]** – možnost kompilátoru říká kompilátoru, jak používat [auto – klíčové slovo](../../cpp/auto-keyword.md) deklarovat proměnné. Pokud zadáte výchozí možnost **/Zc: Auto**, kompilátor deduces typ deklarované proměnné z jeho inicializace výrazu. Pokud zadáte **/Zc:auto-**, kompilátor přiděluje proměnnou automatické třídy úložiště.

## <a name="syntax"></a>Syntaxe

> **/Zc:auto**[**-**]  

## <a name="remarks"></a>Poznámky

C++ standard definuje původní a revidované význam pro `auto` – klíčové slovo. Před [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], klíčové slovo deklaruje proměnné ve třídě automatické úložiště; to znamená, proměnné s místní životnost. Počínaje [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)], klíčové slovo deduces typ proměnné z výrazu deklaraci inicializace. Použít **/Zc: Auto [-]** – možnost kompilátoru říct kompilátor používal původní nebo revidovaný význam `auto` – klíčové slovo. **/Zc: Auto** možnost ve výchozím nastavení zapnutý. [/ Projektovou-](permissive-standards-conformance.md) možnost nezmění výchozí nastavení **/Zc: Auto**.

Kompilátor vydá odpovídající diagnostiky zprávu v případě použití `auto` – klíčové slovo v rozporu se aktuální **/Zc: Auto** – možnost kompilátoru. Další informace najdete v tématu [auto – klíčové slovo](../../cpp/auto-keyword.md). Další informace o problémech shoda s Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Zc: Auto** nebo **/Zc:auto-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[Auto – klíčové slovo](../../cpp/auto-keyword.md)
