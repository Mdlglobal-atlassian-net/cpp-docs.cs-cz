---
title: / CETCOMPAT (kompatibilní s implementační technologie struktury toku řízení)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 1a01dd45667f64dbcbe11acaf1180835bd0d6e31
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809844"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/ CETCOMPAT (kompatibilní s implementační technologie struktury toku řízení)

Určuje, jestli se má označit jako kompatibilní s tok řízení výkonu technologie (CET) spustitelnou bitovou kopii.

## <a name="syntax"></a>Syntaxe

> **/ CETCOMPAT**\[**: NO**]

## <a name="arguments"></a>Arguments

**NE**<br/>
Určuje, že spustitelný soubor by neměl být označen jako kompatibilní s CET.

## <a name="remarks"></a>Poznámky

Technologie vynucení toku řízení (CET) je funkce procesoru počítače, který nabízí možnosti, které braňte se proti určité druhy malwarových útoků. Další informace najdete v tématu [Intel tok řízení vynucení Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

**/CETCOMPAT** – možnost linkeru přikazuje linkeru, aby označit jako kompatibilní s CET binárního souboru. **/CETCOMPAT:No** označí jako není kompatibilní s CET binárního souboru. Pokud obě možnosti jsou zadané na příkazovém řádku, použije se poslední z nich zadat. Tento přepínač je teď jenom pro architekturu x86 a x64.

**/CETCOMPAT** možnost je k dispozici od verze sady nástrojů Visual Studio. 2019 ve verzi Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Nastavení parametru linkeru /CETCOMPAT v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte **/CETCOMPAT** nebo **/CETCOMPAT:NO** a klikněte na tlačítko **OK** nebo **použít**uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také:

[Možnosti linkeru](linker-options.md)
