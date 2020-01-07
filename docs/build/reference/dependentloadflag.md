---
title: /DEPENDENTLOADFLAG (nastavení výchozích příznaků načítání závislých knihoven DLL)
description: Možnost/DEPENDENTLOADFLAG nastaví výchozí příznaky pro knihovny DLL načtené pomocí funkce LoadLibrary.
ms.date: 12/22/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 3a403f22c88ccd3e25ba95c183656ad2ffafd05a
ms.sourcegitcommit: ef34a11cb04511221bf5c7b9f4f55ad91a7a603f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2019
ms.locfileid: "75329995"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (nastavení výchozích příznaků načítání závislých knihoven DLL)

Nastaví výchozí příznaky načtení používané při použití `LoadLibrary` k načtení knihoven DLL.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Arguments

*load_flags*<br/>
Volitelná celočíselná celočíselná hodnota "C" ve formátu Decimal, osmičková s počáteční nulou nebo hexadecimální s počátečním `0x`, která určuje příznaky závislého načtení pro použití na všechna volání [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . Výchozí hodnota je 0.

## <a name="remarks"></a>Poznámky

Tato možnost je v aplikaci Visual Studio 2017 novinkou. Platí jenom pro aplikace, které běží na Windows 10 RS1 a novějších verzích. Tato možnost je ignorována jinými operačními systémy, ve kterých je spuštěna aplikace.

V podporovaných operačních systémech má tato možnost vliv na změnu volání `LoadLibrary("dependent.dll")` na ekvivalent `LoadLibraryEx("dependent.dll", 0, load_flags)`. Volání [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) nejsou nijak ovlivněna. Tato možnost se rekurzivně neaplikuje na knihovny DLL načtené vaší aplikací.

Tento příznak lze použít k obtížnějšímu [útoku na rozmnožovací knihovnu DLL](/windows/win32/dlls/dynamic-link-library-security) . Například pokud aplikace používá `LoadLibrary` k načtení závislé knihovny DLL, útočník by mohl vytvořit knihovnu DLL se stejným názvem v cestě hledání, kterou používá `LoadLibrary`, jako je například aktuální adresář, který může být zkontrolován před systémovými adresáři, pokud je vypnutý režim bezpečného vyhledávání DLL. Bezpečný režim hledání knihovny DLL umístí aktuální adresář uživatele později do pořadí hledání a ve výchozím nastavení je povolen v systému Windows XP SP2 a novějších verzích. Další informace najdete v tématu [pořadí hledání dynamické knihovny](/windows/win32/Dlls/dynamic-link-library-search-order).

Zadáte-li možnost propojení `/DEPENDENTLOADFLAG:0xA00` (hodnota kombinovaných příznaků `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), pak i v případě, že je v počítači uživatele zakázán režim vyhledávání v zabezpečené knihovně DLL, je cesta pro vyhledávání knihovny DLL omezena na adresář aplikace a za ním i adresář%Windows%\System32. Možnost `/DEPENDENTLOADFLAG:0x800` je ještě více omezující a omezuje hledání do adresáře%Windows%\System32. Chráněné adresáře jsou obtížnější, ale nejsou možné, aby se mohl útočník změnit. Informace o dostupných příznacích a jejich symbolické a číselné hodnoty naleznete v popisu parametru *dwFlags* v [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw). Informace o pořadí hledání, které se používá při použití různých příznaků závislého zatížení, najdete v tématu [pořadí hledání pomocí příznaků LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Nastavení Možnosti linkeru DEPENDENTLOADFLAG ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **příkazového řádku** > **linkeru** .

1. Zadejte možnost v části **Další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
- [Propojení spustitelného souboru s knihovnou DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Propojení spustitelného souboru s knihovnou DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)
