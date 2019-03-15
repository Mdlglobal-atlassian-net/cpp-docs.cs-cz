---
title: /DYNAMICBASE (Použít modul pro náhodné určení rozložení adresního prostoru)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: a3495de3ec72bcac78cdee2f5f3265864e7a2932
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807751"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Použít modul pro náhodné určení rozložení adresního prostoru)

Určuje, jestli se má generovat spustitelnou bitovou kopii, která lze náhodně změnit základ v okamžiku načtení pomocí funkce adresu místo rozložení náhodné (technologie ASLR) z Windows, která byla poprvé dostupná ve Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Poznámky

**Možnost/DynamicBase** možnost změní záhlaví *spustitelné bitové kopie*, soubor .dll nebo .exe, označuje, zda by měl být náhodně změnit základ v okamžiku načtení aplikace a umožňuje virtuální adresa náhodné přidělování, který má vliv na umístění virtuální paměti haldy, zásobníků a další přidělení operačního systému. **Možnost/DynamicBase** možnost se vztahuje na 32bitové i 64bitové obrazy. Technologie ASLR je podporován v systémech Windows Vista a novějších operačních systémech. Tato možnost je ignorována ve starších operačních systémech.

Ve výchozím nastavení **možnost/DynamicBase** je povolená. Chcete-li tuto možnost zakázat, použijte **kopii**. **Možnost/DynamicBase** možnost je vyžadována pro [/highentropyva](highentropyva-support-64-bit-aslr.md) možnost mají nějaký efekt.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **Upřesnit** stránku vlastností.

1. Upravit **Randomizovaného základní adresa** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Viz také:

- [Odkaz na MSVC linkeru](linking.md)
- [Možnosti Linkeru MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Obrana zabezpečení ISV softwaru Windows](https://msdn.microsoft.com/library/bb430720.aspx)