---
title: '/ Zc: trigraphs (náhrada trigraph) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e465b62944b360d6fdb09da1230f3353658437b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Náhrada trigraph)

Když **/Zc: trigraphs** není zadaný, kompilátor nahradí znak posloupnost trigraph pomocí odpovídající interpunkční znaménko.

## <a name="syntax"></a>Syntaxe

> **/ Zc: trigraphs**[**-**]  

## <a name="remarks"></a>Poznámky

A *trigraph* se skládá ze dvou po sobě jdoucích otazníky ("??") následuje jedinečný třetí znak. Jazyk C standardní podporuje trigraph pro zdrojové soubory, které používají znaková sada, která neobsahuje vhodné grafické reprezentace pro některé znaky interpunkce. Například pokud jsou povolené trigraph, kompilátor nahradí "?? = "trigraph pomocí znaku '#'. Prostřednictvím C ++ 14 jsou podporovány trigraph jako C. C ++ 17 standardní odebere trigraph z jazyka C++. V kódu C++ **/Zc: trigraphs** – možnost kompilátoru umožňuje náhrada trigraph pořadí podle odpovídající interpunkční znaménko. **/Zc:trigraphs-** zakáže trigraph nahrazení.

**/Zc: trigraphs** možnost je ve výchozím nastavení vypnuta a tato možnost není při vliv [/ projektovou-](permissive-standards-conformance.md) je zadána možnost.

Seznam trigraph C/C++ a příklad, který ukazuje způsob použití trigraph najdete v tématu [trigraph](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc: trigraphs** nebo **/Zc:trigraphs-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[Spřežky tří znaků](../../c-language/trigraphs.md)<br/>
