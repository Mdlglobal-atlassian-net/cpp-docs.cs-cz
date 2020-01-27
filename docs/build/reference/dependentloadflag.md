---
title: /DEPENDENTLOADFLAG (nastavení výchozích příznaků načítání závislých knihoven DLL)
description: Možnost/DEPENDENTLOADFLAG nastaví výchozí závislé příznaky načtení pro knihovny DLL načtené tímto modulem.
ms.date: 01/22/2020
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 5e31a0d747e7186814cba3ae1c4cf243569d87a8
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725705"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (nastavení výchozích příznaků načítání závislých knihoven DLL)

::: moniker range="vs-2015"

Možnost **/DEPENDENTLOADFLAG** vyžaduje Visual Studio 2017 nebo novější.

::: moniker-end

::: moniker range=">=vs-2017"

Nastaví výchozí příznaky zatížení, které se použijí, když operační systém vyřeší staticky propojený import modulu.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Arguments

*load_flags*<br/>
Volitelná celočíselná hodnota, která určuje příznaky zatížení, které mají být použity při překladu staticky propojených závislostí importu modulu. Výchozí hodnota je 0. Seznam podporovaných hodnot příznaků najdete v `LOAD_LIBRARY_SEARCH_*`ch položkách v [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="remarks"></a>Poznámky

Když operační systém vyřeší staticky propojený import modulu, používá [výchozí pořadí hledání](/windows/win32/dlls/dynamic-link-library-search-order). Pomocí možnosti **/DEPENDENTLOADFLAG** zadejte hodnotu *load_flags* , která mění cestu pro hledání použitou k vyřešení těchto importů. V podporovaných operačních systémech se změní pořadí hledání statického řešení importu, podobně jako [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) při použití parametrů `LOAD_LIBRARY_SEARCH`. Informace o pořadí hledání nastaveném pomocí *load_flags*najdete v tématu [pořadí hledání pomocí příznaků LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

Tento příznak lze použít k tomu, aby jeden vektor [útoku na knihovnu DLL](/windows/win32/dlls/dynamic-link-library-security) byl obtížnější. Zvažte například aplikaci, která má staticky propojenou knihovnu DLL:

- Útočník by mohl nakládat knihovnu DLL se stejným názvem dříve v cestě pro vyhledávání rozlišení importu, jako je například adresář aplikace. Chráněné adresáře jsou obtížnější, ale nejsou možné, aby se mohl útočník změnit.

- Pokud knihovna DLL chybí v adresářích aplikace,%Windows%\System32 a% Windows%, řešení importu spadá do aktuálního adresáře. Útočník by mohl nasázet knihovnu DLL.

V obou případech, pokud zadáte možnost odkazu `/DEPENDENTLOADFLAG:0x800` (hodnota `LOAD_LIBRARY_SEARCH_SYSTEM32`příznak), cesta hledání modulu je omezená na adresář%Windows%\System32. V ostatních adresářích nabízí ochranu před útoky na výsadbu. Další informace najdete v tématu [zabezpečení knihovny Dynamic-Link](/windows/win32/dlls/dynamic-link-library-security).

Chcete-li zobrazit hodnotu nastavenou možností **/DEPENDENTLOADFLAG** v jakékoli knihovně DLL, použijte příkaz [DUMPBIN](dumpbin-reference.md) s možností [/LOADCONFIG](loadconfig.md) .

Možnost **/DEPENDENTLOADFLAG** je v aplikaci Visual Studio 2017 novinkou. Platí jenom pro aplikace, které běží na Windows 10 RS1 a novějších verzích. Tato možnost je ignorována jinými operačními systémy, ve kterých je spuštěna aplikace.

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Nastavení Možnosti linkeru DEPENDENTLOADFLAG ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **příkazového řádku** > **linkeru** .

1. Zadejte možnost v části **Další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
- [Implicitně propojit spustitelný soubor s knihovnou DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Určete, kterou propojovací metodu použít](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)
- [Zabezpečení knihovny Dynamic-Link](/windows/win32/dlls/dynamic-link-library-security)

::: moniker-end
