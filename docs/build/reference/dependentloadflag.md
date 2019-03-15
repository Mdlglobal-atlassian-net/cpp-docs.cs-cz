---
title: / DEPENDENTLOADFLAG (sada výchozích závislé zatížení příznaků)
description: Možnost /DEPENDENTLOADFLAG nastaví výchozí příznaky pro knihovny DLL načtené pomocí možnosti LoadLibrary
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 94998e06f23a7e70524221d3cb75166b5d3f2c44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815967"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (sada výchozích závislé zatížení příznaků)

Nastaví výchozí příznaky zatížení použít, pokud `LoadLibrary` slouží k načtení knihovny DLL.

## <a name="syntax"></a>Syntaxe

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Arguments

*loadflags*<br/>
Volitelná hodnota "C" stylu 16bitové celé číslo v desítkové, osmičkové s počáteční nulou nebo šestnáctkové s úvodní `0x`, který určuje příznaky závislé zatížení chcete použít pro všechny [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) volání. Výchozí hodnota je 0.

## <a name="remarks"></a>Poznámky

Tato možnost je nového v sadě Visual Studio 2017 a platí jenom pro aplikace běžící na Windows 10 RS1 a novějších verzích. Tato možnost je ignorována jinými operačními systémy, na kterých běží aplikace.

Na podporovaných operačních systémech, tato možnost nemá vliv změny volání `LoadLibrary("dependent.dll")` na ekvivalent `LoadLibraryEx("dependent.dll", 0, loadflags)`. Volání [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) to neovlivní. Tato možnost se nevztahuje rekurzivně na načtení aplikací pro knihovny DLL.

Tento příznak je možné zabránit DLL výsadbě útoky. Například, pokud aplikace používá `LoadLibrary` načíst závislá knihovna DLL, může útočník plánu knihovnu DLL se stejným názvem ve vyhledávací cesta používaná systémem `LoadLibrary`, jako je například aktuální adresář, který může být zaregistrované před adresáře systému-li nouzový režim hledání knihovny DLL je zakázané. Nouzový režim hledání knihovny DLL umístí aktuální adresář uživatele později v pořadí hledání a je povolená ve výchozím nastavení systému Windows XP SP2 a novější verze. Další informace najdete v tématu [pořadí hledání knihoven DLL](/windows/desktop/Dlls/dynamic-link-library-search-order).

Pokud zadáte možnost propojení `/DEPENDENTLOADFLAG:0xA00` (hodnota kombinované příznaky `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), pak i v případě, že v počítači uživatele je zakázána Nouzový režim hledání knihovny DLL, je omezený na chráněných adresářů, které jsou pro útočníka obtížnější cesta hledání knihoven DLL Změňte. Informace o příznaky, které jsou k dispozici a jejich symbolické a číselné hodnoty, najdete v článku *dwFlags* popis parametru v [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru DEPENDENTLOADFLAG ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte parametr do **další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Odkaz na MSVC linkeru](linking.md)
- [Možnosti Linkeru MSVC](linker-options.md)
- [Propojení spustitelného souboru s knihovnou DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Propojení spustitelného souboru s knihovnou DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)
- [Pořadí hledání knihoven DLL](/windows/desktop/Dlls/dynamic-link-library-search-order)
