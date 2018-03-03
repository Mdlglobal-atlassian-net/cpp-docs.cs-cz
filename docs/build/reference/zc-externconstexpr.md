---
title: "/Zc:externConstexpr (Povolit extern constexpr proměnné) | Microsoft Docs"
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:externConstexpr
dev_langs:
- C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84037e5e8a942d51175d97957d0c05bd6f4aa29d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr (Povolit extern constexpr proměnné)

**/Zc:externConstexpr** – možnost kompilátoru říká kompilátoru odpovídat C++ standard a povolit externí propojení pro `constexpr` proměnné. Ve výchozím nastavení, budou vždy poskytuje sadě Visual Studio `constexpr` proměnné vnitřní propojení, i když zadáte `extern` – klíčové slovo.

## <a name="syntax"></a>Syntaxe

> /Zc:externConstexpr [-]

## <a name="remarks"></a>Poznámky

**/Zc:externConstexpr** – možnost kompilátoru způsobí, že kompilátor použít externí propojení proměnných deklarovaných pomocí `extern constexpr`. **/Zc:externConstexpr** možnost je k dispozici od verze Visual Studio 2017 aktualizace 15,5. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:externConstexpr-** není zadaný, Visual Studio použije vnitřní propojení na `constexpr` i když proměnné `extern` – klíčové slovo se používá.

Pokud soubor hlaviček obsahuje proměnná definovaná `extern constexpr`, musí být označen [__declspec(selectany)](../../cpp/selectany.md) Chcete-li sloučit duplicitní deklarace do jediné instance v propojených binárního souboru. V opačném případě se mohou zobrazit chyby linkeru, například LNK2005 pro porušení jedna definice pravidla.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, rozbalte položku **C/C++** a potom zvolte **příkazového řádku**.

1. Přidat **/Zc:externConstexpr** nebo **/Zc:externConstexpr-** k **další možnosti:** podokně.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)  
[Auto – klíčové slovo](../../cpp/auto-keyword.md)