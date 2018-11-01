---
title: /HIGHENTROPYVA (podpora 64bitové technologie ASLR)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: a8bd1b2231530c0f1632b244edaf36ee14ed65b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534794"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (podpora 64bitové technologie ASLR)

Určuje, zda spustitelné bitové kopie podporují náhodného generování rozložení prostoru adres 64-bit vysokou mírou entropie (technologie ASLR).

## <a name="syntax"></a>Syntaxe

> **/ HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>Poznámky

**/ HIGHENTROPYVA** změní záhlaví *spustitelné bitové kopie*, soubor .dll nebo .exe souboru, označuje, zda technologie ASLR můžete použít celou 64-bit adresní prostor. Pokud tato možnost je nastavena na spustitelný soubor a všechny moduly, na kterých závisí, operační systém, který podporuje 64bitové technologie ASLR základ segmentů spustitelné bitové kopie v okamžiku načtení pomocí náhodných adres v 64bitové virtuální adresní prostor. Tento rozsáhlý adresní prostor ztěžuje útočníkovi možnost uhádnout umístění konkrétní paměťové oblasti.

Ve výchozím nastavení **/highentropyva** povoleny pro 64bitové spustitelné bitové kopie. Tato možnost vyžaduje [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), je také povolená ve výchozím nastavení pro 64bitové obrazy. **/ HIGHENTROPYVA** neplatí pro 32bitové spustitelné bitové kopie, pokud linker ignoruje možnost. Chcete-li explicitně zakázat tuto možnost, použijte **/HIGHENTROPYVA:NO**.

Pro **/highentropyva** mají nějaký efekt v okamžiku načtení [možnost/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) také musí být povolené. **/ DYNAMICBASE** je ve výchozím nastavení povolené a je nutné k povolení technologie ASLR v systémech Windows Vista a novějších operačních systémech. Starší verze Windows ignorují tento příznak.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte `/HIGHENTROPYVA` nebo `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Obrana zabezpečení ISV softwaru Windows](https://msdn.microsoft.com/library/bb430720.aspx)
