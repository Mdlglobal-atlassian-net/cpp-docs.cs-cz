---
title: / CETCOMPAT (kompatibilní s CET stínový zásobník)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 0ed5d9d4f9f4f4dc5cd4fc19df4179e86e430187
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356012"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/ CETCOMPAT (kompatibilní s CET stínový zásobník)

Určuje, jestli se má označit jako kompatibilní se tok řízení technologie vynucení (CET) stínový zásobník spustitelnou bitovou kopii.

## <a name="syntax"></a>Syntaxe

> **/ CETCOMPAT**\[**: NO**]

## <a name="arguments"></a>Arguments

**NE**<br/>
Určuje, že spustitelný soubor by neměl být označen jako kompatibilní s CET stínový zásobník.

## <a name="remarks"></a>Poznámky

Tok řízení technologie vynucení (CET) stínový zásobník je funkce procesoru počítače, který poskytuje funkce pro ochranu před návratový orientované programování (mohli) založený na malwarových útoků. Další informace najdete v tématu [Intel tok řízení vynucení Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

**/CETCOMPAT** – možnost linkeru přikazuje linkeru, aby označit binárního souboru jako kompatibilního s CET stín zásobníku. **/CETCOMPAT:No** označí jako není kompatibilní s CET stínový zásobník binárního souboru. Pokud obě možnosti jsou zadané na příkazovém řádku, použije se poslední z nich zadat. Tento přepínač je teď jenom pro architekturu x86 a x64.

**/CETCOMPAT** možnost je k dispozici od verze sady nástrojů Visual Studio. 2019 ve verzi Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Nastavení parametru linkeru /CETCOMPAT v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte **/CETCOMPAT** nebo **/CETCOMPAT:NO** a klikněte na tlačítko **OK** nebo **použít**uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také:

[Možnosti linkeru](linker-options.md)
