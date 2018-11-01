---
title: '/ Zc: externconstexpr (povolení proměnných extern constexpr)'
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: a9efa2fa191cbdda99e057ac9329d79bc598743c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510692"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/ Zc: externconstexpr (povolení proměnných extern constexpr)

**/Zc: externconstexpr** – možnost kompilátoru instruuje kompilátor, aby se řídí standardu jazyka C++ a povolit vnější propojení pro `constexpr` proměnné. Ve výchozím nastavení, budou vždy poskytuje Visual Studio `constexpr` proměnné vnitřní propojení, i když zadáte `extern` – klíčové slovo.

## <a name="syntax"></a>Syntaxe

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Poznámky

**/Zc: externconstexpr** – možnost kompilátoru způsobí, že kompilátor použije vnější propojení k proměnné deklarované s použitím `extern constexpr`. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:externConstexpr-** není zadána, Visual Studio použije vnitřní propojení k `constexpr` i pokud proměnné `extern` – klíčové slovo se používá. **/Zc: externconstexpr** možnost je k dispozici od verze Visual Studio 2017 Update 15.6. a je vypnuto ve výchozím nastavení. [/ Permissive-](permissive-standards-conformance.md) možnost nepovolíte **/Zc: externconstexpr**.

Pokud soubor hlavičky obsahuje proměnné deklarované `extern constexpr`, musí být označen [__declspec(selectany)](../../cpp/selectany.md) aby bylo možné sloučit duplicitní deklarace do jediné instance v odkazovaný binární soubor. Jinak se může zobrazit chyby linkeru, například LNK2005 pro porušení jednu definici pravidla.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Přidat **/Zc: externconstexpr** nebo **/Zc:externConstexpr-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[Auto – klíčové slovo](../../cpp/auto-keyword.md)