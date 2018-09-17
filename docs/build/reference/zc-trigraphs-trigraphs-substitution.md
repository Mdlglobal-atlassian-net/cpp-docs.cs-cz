---
title: '/ Zc: trigraphs (náhrada trigraph) | Dokumentace Microsoftu'
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
ms.openlocfilehash: ce8c9d13fa062ddac0f31eac0e20fba1266c7a8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707730"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Náhrada trigraph)

Když **/Zc: trigraphs** není zadán, kompilátor nahradí znak sekvence trigrafu pomocí odpovídající znak interpunkce.

## <a name="syntax"></a>Syntaxe

> **/ Zc: trigraphs**[**-**]

## <a name="remarks"></a>Poznámky

A *trigraph* se skládá ze dvou po sobě jdoucími otazníky ("??") následovaný znakem třetí jedinečný. Standard jazyka C podporuje trigraphs pro zdrojové soubory, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některá interpunkční znaménka. Například pokud trigrafy jsou povolené, kompilátor nahradí "?? = "trigraph pomocí znak"#". Pomocí C ++ 14 jsou podporovány trigraphs stejně jako v jazyce C. Standardu C ++ 17 odebere trigraphs z jazyka C++. V kódu jazyka C++ **/Zc: trigraphs** – možnost kompilátoru umožňuje nahrazování sekvence trigrafů umožňuje díky na odpovídající znak interpunkce. **/Zc:trigraphs-** zakáže náhrada trigraph.

**/Zc: trigraphs** možnost je vypnuto ve výchozím nastavení, a tato možnost není při měla vliv [/ permissive-](permissive-standards-conformance.md) je zadána možnost.

Seznam trigraphs C/C++ a příklad, který ukazuje způsob použití trigraphs najdete v tématu [Trigraphs](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: trigraphs** nebo **/Zc:trigraphs-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[Spřežky tří znaků](../../c-language/trigraphs.md)<br/>
