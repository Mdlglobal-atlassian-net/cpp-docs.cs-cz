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
ms.openlocfilehash: 66d6232ed43f9c842ebbb0e22b57c509cf610afa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170056"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Použít modul pro náhodné určení rozložení adresního prostoru)

Určuje, jestli se má generovat spustitelná image, která se dá náhodně využít při načítání, pomocí funkce ASLR (Address Space layouting Layout) systému Windows, která byla poprvé dostupná v systému Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/DYNAMICBASE**[ **: No**]

## <a name="remarks"></a>Poznámky

Možnost **/DYNAMICBASE** upraví hlavičku *spustitelné bitové kopie*, soubor. dll nebo. exe, aby označovala, zda by měla být aplikace náhodně založena během načítání, a umožňuje náhodné vyřazení virtuálních adres, což ovlivňuje umístění virtuálních paměti hald, zásobníků a dalších přidělení operačního systému. Možnost **/DYNAMICBASE** se vztahuje na 32 bitové i 64 bitové kopie. ASLR je podporován v systému Windows Vista a novějších operačních systémech. Možnost ignoruje starší operační systémy.

Ve výchozím nastavení je povolená možnost **/DYNAMICBASE** . Pokud chcete tuto možnost zakázat, použijte **/DYNAMICBASE: No**. Možnost **/DYNAMICBASE** je vyžadována, pokud má možnost [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) efekt.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **konfigurační vlastnosti** > **linker** > **Upřesnit** stránku vlastností.

1. Upravte vlastnost **randomizovaná základní adresa** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Viz také

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Obrana zabezpečení softwaru Windows ISV](https://msdn.microsoft.com/library/bb430720.aspx)
