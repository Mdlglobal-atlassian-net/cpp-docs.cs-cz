---
title: /Zc:externConstexpr (Povolit extern constexpr proměnné) | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:externConstexpr
dev_langs:
- C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cbce8366fdd7be62c8d71f838b298d77849dcdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr (Povolit extern constexpr proměnné)

**/Zc:externConstexpr** – možnost kompilátoru říká kompilátoru odpovídat C++ standard a povolit externí propojení pro `constexpr` proměnné. Ve výchozím nastavení, budou vždy poskytuje sadě Visual Studio `constexpr` proměnné vnitřní propojení, i když zadáte `extern` – klíčové slovo.

## <a name="syntax"></a>Syntaxe

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Poznámky

**/Zc:externConstexpr** – možnost kompilátoru způsobí, že kompilátor použít externí propojení proměnných deklarovaných pomocí `extern constexpr`. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:externConstexpr-** není zadaný, Visual Studio použije vnitřní propojení na `constexpr` i když proměnné `extern` – klíčové slovo se používá. **/Zc:externConstexpr** možnost je k dispozici od 15,6 operací aktualizace 2017 Visual Studio. a ve výchozím nastavení. [/ Projektovou-](permissive-standards-conformance.md) možnost neumožňuje **/Zc:externConstexpr**.

Pokud soubor hlaviček obsahuje proměnná definovaná `extern constexpr`, musí být označen [__declspec(selectany)](../../cpp/selectany.md) Chcete-li sloučit duplicitní deklarace do jediné instance v propojených binárního souboru. V opačném případě se mohou zobrazit chyby linkeru, například LNK2005 pro porušení jedna definice pravidla.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Zc:externConstexpr** nebo **/Zc:externConstexpr-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)  
[Auto – klíčové slovo](../../cpp/auto-keyword.md)