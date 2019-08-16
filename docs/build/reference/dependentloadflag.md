---
title: /DEPENDENTLOADFLAG (nastavení výchozích příznaků načítání závislých knihoven DLL)
description: Možnost/DEPENDENTLOADFLAG nastaví výchozí příznaky pro knihovny DLL načtené pomocí funkce LoadLibrary.
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 072fa1103d049c7d5c395ae88d268f3b47e20b4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492953"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (nastavení výchozích příznaků načítání závislých knihoven DLL)

Nastaví výchozí příznaky načtení používané při `LoadLibrary` použití k načtení knihoven DLL.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTLOADFLAG** [ **:** _loadflags_]

### <a name="arguments"></a>Arguments

*loadflags*<br/>
Volitelná celočíselná celočíselná hodnota typu "C", která je v desítkové soustavě typu Decimal, osmičková s úvodní `0x`nulou, nebo šestnáctková s přední hodnotou, která určuje příznaky závislého zatížení pro použití na všechna volání [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . Výchozí hodnota je 0.

## <a name="remarks"></a>Poznámky

Tato možnost je v aplikaci Visual Studio 2017 novinkou a platí jenom pro aplikace, které běží na Windows 10 RS1 a novějších verzích. Tato možnost je ignorována jinými operačními systémy, ve kterých je spuštěna aplikace.

V podporovaných operačních systémech Tato možnost má vliv na změnu volání `LoadLibrary("dependent.dll")` na `LoadLibraryEx("dependent.dll", 0, loadflags)`ekvivalent. Volání [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) nejsou nijak ovlivněna. Tato možnost se neaplikuje rekurzivně na knihovny DLL načtené vaší aplikací.

Pomocí tohoto příznaku lze zabránit útokům na rozmnožovací knihovnu DLL. Například pokud aplikace používá `LoadLibrary` k načtení závislé knihovny DLL, útočník by mohl vytvořit knihovnu DLL se stejným názvem v cestě hledání `LoadLibrary`, kterou používá, jako je například aktuální adresář, který může být zkontrolován před systémovými adresáři, pokud je zabezpečený režim vyhledávání DLL zabezpečen. Bezpečný režim hledání knihovny DLL umístí aktuální adresář uživatele později do pořadí hledání a ve výchozím nastavení je povolen v systému Windows XP SP2 a novějších verzích. Další informace najdete v tématu [pořadí hledání dynamické knihovny](/windows/win32/Dlls/dynamic-link-library-search-order).

Zadáte-li možnost `/DEPENDENTLOADFLAG:0xA00` odkaz (hodnota kombinovaných příznaků `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), a to i v případě, že je v počítači uživatele zakázán režim vyhledávání bezpečných knihoven DLL, je cesta pro hledání knihovny DLL omezena na chráněné adresáře, které jsou obtížnější pro útočníka. mění. Informace o dostupných příznacích a jejich symbolické a číselné hodnoty naleznete v popisu parametru *dwFlags* v [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Nastavení Možnosti linkeru DEPENDENTLOADFLAG ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazový řádek** **linkeru** >  **vlastností** > konfigurace.

1. Zadejte možnost v části **Další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
- [Propojení spustitelného souboru s knihovnou DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Propojení spustitelného souboru s knihovnou DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)
