---
title: / DEPENDENTLOADFLAG (příznaky závislé zatížení výchozí sadu)
description: Možnost /DEPENDENTLOADFLAG nastaví výchozí příznaky pro knihovny DLL načtené pomocí možnosti LoadLibrary
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dependentloadflag
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a171f3c2edbbbf614a986ff78dd2405e734a1d1
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753722"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (příznaky závislé zatížení výchozí sadu)

Nastaví příznaky zatížení výchozí použít, když `LoadLibrary` slouží k načtení knihovny DLL.

## <a name="syntax"></a>Syntaxe

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Arguments

|||
|-|-|
*loadflags*|Volitelné 16bitové celočíselnou hodnotu "C" stylu v decimal, osmičková s úvodní nuly nebo hexadecimální s úvodní `0x`, který určuje příznaky závislé zatížení tak, aby uplatňovat pro všechny [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) volání. Výchozí hodnota je 0.

## <a name="remarks"></a>Poznámky

Tato možnost je nového ve Visual Studio 2017 a platí jenom pro aplikace běžící na Windows 10 RS1 a novějších verzích. Tato možnost je ignorována jinými operačními systémy, které aplikace spustit.

Na podporovaných operačních systémech, tato možnost je změna volání `LoadLibrary("dependent.dll")` na ekvivalent `LoadLibraryEx("dependent.dll", 0, loadflags)`. Volání [funkce LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091) jsou poškozena. Tato možnost se nevztahuje rekurzivně knihovny DLL načtené aplikace.

Tento příznak slouží k zabránit DLL výsadbě útoky. Například pokud aplikace používá `LoadLibrary` načíst závislé knihovnu DLL, může útočník plánu knihovny DLL se stejným názvem v vyhledávací cesta používaná systémem `LoadLibrary`, například aktuálním adresáři, který může ověřit před adresáře systému Pokud nouzový režim hledání knihoven DLL zakázané. Nouzový režim hledání knihoven DLL umístí aktuální adresář uživatele později v pořadí hledání a je povolená ve výchozím nastavení ve Windows XP SP2 a novější verze. Další informace najdete v tématu [pořadí hledání knihovny DLL](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

Pokud zadáte možnost propojení `/DEPENDENTLOADFLAG:0xA00` (hodnota kombinované příznaky `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), pak i v případě, že je v počítači uživatele zakázána Nouzový režim hledání knihovny DLL, je omezený na chráněných adresářů, které jsou pro útočníka obtížnější cesta hledání knihoven DLL změníte. Informace o příznaky, které jsou k dispozici a jejich symbolický a číselné hodnoty, najdete v článku *dwFlags* popis parametru v [funkce LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Chcete-li nastavit možnosti linkeru DEPENDENTLOADFLAG ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost v **další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](setting-linker-options.md)
- [Možnosti linkeru](linker-options.md)
- [Postup propojení implicitně s knihovny DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Rozhodování o způsobu vytváření použít](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [Funkce LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)
- [Pořadí hledání knihoven DLL](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)
