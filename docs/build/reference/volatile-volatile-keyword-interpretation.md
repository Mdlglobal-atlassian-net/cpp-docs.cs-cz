---
title: -volatile (interpretace klíčového slova volatile) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccd36c5edaaab8577e5f278b25b51ce69e0633f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378194"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (Interpretace klíčového slova volatile)

Určuje, jak [volatile](../../cpp/volatile-cpp.md) – klíčové slovo se budou interpretovat.

## <a name="syntax"></a>Syntaxe

> **/ volatile:**{**iso**|**ms**}  

## <a name="arguments"></a>Arguments

**/volatile:ISO**  
Vybere striktní `volatile` sémantiku podle jazyka C++ standardem ISO. Získání a verze sémantiku se nezaručuje, že na volatile přístupů. Pokud kompilátor cílem ARM, je to výchozí interpretaci `volatile`.

**/volatile:MS**  
Vybere Microsoft rozšířené `volatile` sémantikou, které přidat paměti řazení záruky mimo jazyk C++ standardem ISO. Získání a verze sémantiku zaručeně na volatile přístupů. Tato možnost však vynutí kompilátoru generovat překážek paměti hardwaru, které může přidat významné režijní náklady na ARM a dalších slabé architektury řazení paměti. Pokud kompilátor cílem všechny platformy kromě ARM, je to výchozí interpretaci `volatile`.

## <a name="remarks"></a>Poznámky

Důrazně doporučujeme použít **/volatile:iso** spolu s explicitní synchronizace primitiv a vnitřní funkce kompilátoru, když pracujete s pamětí, který je sdílen mezi vláken. Další informace najdete v tématu [volatile](../../cpp/volatile-cpp.md).

Pokud port existující kód nebo změňte tuto možnost uprostřed projektu, může být užitečné umožnit upozornění [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) k identifikaci kódu umístění, které jsou ovlivněné rozdíl ve smyslu sémantiky.

Neexistuje žádné `#pragma` ekvivalentní k řízení tuto možnost.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Chcete-li nastavit / volatile – možnost kompilátoru v sadě Visual Studio

1. Otevřete **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte **/volatile:iso** nebo **/volatile:ms** a potom zvolte **OK** nebo **použít** uložte provedené změny.

## <a name="see-also"></a>Viz také

[volatile](../../cpp/volatile-cpp.md)  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
