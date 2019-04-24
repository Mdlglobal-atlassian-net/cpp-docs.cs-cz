---
title: /volatile (Interpretace klíčového slova volatile)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: 02871622242930d7419fda16f4d106fccb2056f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316636"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (Interpretace klíčového slova volatile)

Určuje, jak [volatile](../../cpp/volatile-cpp.md) – klíčové slovo se budou interpretovat.

## <a name="syntax"></a>Syntaxe

> **/ volatile:**{**iso**|**ms**}

## <a name="arguments"></a>Arguments

**/volatile:ISO**<br/>
Vybere striktní `volatile` sémantiku podle jazyka C++ podle standardu ISO jazyka. Sémantika získání nebo vydání není zaručena pro nestálé přístupy. Pokud se kompilátor zaměřuje na ARM, toto je výchozí výklad `volatile`.

**/volatile:MS**<br/>
Vybere Microsoft rozšířené `volatile` sémantiku, která nad rámec standardu ISO C++ jazyk zaručuje řazení paměti. Sémantika získání nebo vydání je zaručena pro nestálé přístupy. Tato možnost však způsobí kompilátor generuje hardwarové překážky paměti, které mohou přidat významné zatížení na ARM a jiné slabého řazení paměti architektury. Pokud se kompilátor zaměřuje na libovolnou platformu s výjimkou ARM, toto je výchozí výklad `volatile`.

## <a name="remarks"></a>Poznámky

Důrazně doporučujeme používat **/volatile:iso** spolu s explicitní synchronizací primitiv a vnitřních typů kompilátoru při jednání s pamětí, která je sdílena mezi vlákny. Další informace najdete v tématu [volatile](../../cpp/volatile-cpp.md).

Pokud portujete existující kód nebo měníte tuto možnost během projektu, může být užitečné povolit upozornění [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) k identifikaci umístění kódu, která jsou ovlivněna rozdíly v sémantice.

Neexistuje žádná `#pragma` ekvivalentní pro ovládání této možnosti.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Chcete-li nastavit možnosti/volatilní – možnost kompilátoru v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte **/volatile:iso** nebo **/volatile:ms** a klikněte na tlačítko **OK** nebo **použít** uložte provedené změny.

## <a name="see-also"></a>Viz také:

[volatile](../../cpp/volatile-cpp.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
