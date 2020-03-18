---
title: /Zc:trigraphs (Náhrada trigraph)
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438651"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Náhrada trigraph)

Je-li zadán parametr **/Zc: trigraphs** , kompilátor nahradí sekvenci znaků trigraph pomocí odpovídajícího interpunkční znaku.

## <a name="syntax"></a>Syntaxe

> **/Zc: trigraphs**[ **-** ]

## <a name="remarks"></a>Poznámky

*Trigraph* se skládá ze dvou po sobě jdoucích otazníků ("??") následovaný jedinečným třetím znakem. Standard jazyka C podporuje trigraphs pro zdrojové soubory, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některé interpunkční znaky. Například když jsou povoleny trigraphs, kompilátor nahradí "?? = "trigraph pomocí znaku" # ". V jazyce C++ 14 jsou trigraphs podporovány jako v jazyce C. Standard C++ 17 odebere trigraphs z C++ jazyka. V C++ kódu možnost kompilátoru **/Zc: trigraphs** umožňuje substituci trigraph sekvencí odpovídajícím znakem interpunkce. **/Zc: trigraphs-** zakáže trigraph substituce.

Možnost **/Zc: trigraphs** je ve výchozím nastavení vypnutá a možnost není ovlivněna, pokud je zadána možnost [/Permissive-](permissive-standards-conformance.md) .

Seznam C/C++ trigraphs a příklad, který ukazuje, jak používat trigraphs, naleznete v tématu [trigraphs](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **příkazového řádku** **jazyka C/C++**  > .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala parametr **/Zc: trigraphs** nebo **/Zc: trigraphs-** a pak klikněte na **tlačítko OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](zc-conformance.md)<br/>
[Spřežky tří znaků](../../c-language/trigraphs.md)<br/>
