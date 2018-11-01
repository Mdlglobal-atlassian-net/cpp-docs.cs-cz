---
title: /SUBSYSTEM (Zadat subsystém)
ms.date: 11/04/2016
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
ms.openlocfilehash: 3d808f86a9ea3b34da0dccae18ecc000ca364f0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518388"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Zadat subsystém)

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>Arguments

**BOOT_APPLICATION**<br/>
Aplikace, která běží v prostředí spouštění Windows. Další informace o spouštěcích aplikacích najdete v tématu [o BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**KONZOLY**<br/>
Aplikace znakového režimu systému Win32. Operační systém poskytuje konzolu pro konzolové aplikace. Pokud `main` nebo `wmain` je definována pro nativní kód `int main(array<String ^> ^)` je definována pro spravovaný kód, nebo zcela sestavení aplikace s použitím `/clr:safe`, KONZOLA je výchozí hodnota.

**EFI_APPLICATION**<br/>
**BITOVÁ KOPIE EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Subsystémy Extensible Firmware Interface. V tématu Specifikace rozhraní EFI pro další informace. Příklady naleznete v tématu na webu společnosti Intel. Minimální verze a výchozí verze je 1.0.

**NATIVNÍ**<br/>
Ovladače režimu jádra Windows NT. Tato možnost je obvykle vyhrazena pro součásti systému Windows. Pokud [/DRIVER:WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) není zadán, výchozí hodnota je NATIVNÍ.

**POSIX**<br/>
Aplikace, která běží v subsystému POSIX v systému Windows NT.

**SYSTÉM WINDOWS**<br/>
Aplikace nevyžaduje konzolu, pravděpodobně, protože vytváří vlastní okna pro interakci s uživatelem. Pokud `WinMain` nebo `wWinMain` je definována pro nativní kód, nebo `WinMain(HISTANCE *, HINSTANCE *, char *, int)` nebo `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` je definována pro spravovaný kód, je WINDOWS výchozí hodnota.

*hlavní* a *podverze*<br/>
(Volitelné) Zadejte minimální požadovanou verzi subsystému. Argumenty jsou desetinná čísla v rozmezí 0 až 65535. Viz poznámky pro další informace. Neexistují žádná horní mez pro čísla verzí.

## <a name="remarks"></a>Poznámky

**/Subsystem** Určuje prostředí pro spustitelný soubor.

Volba subsystému ovlivňuje symbol vstupního bodu (nebo funkci vstupního bodu), který vybere linkeru.

Volitelné minimální a výchozí *hlavní* a *menší* čísla verzí pro subsystémy jsou následující.

|Subsystém|Minimální|Výchozí|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|KONZOLY|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|SYSTÉM WINDOWS|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|NATIVNÍ (DRIVER: WDM)|1,00 (x 86) 1.10 (x64, ARM)|1,00 (x 86) 1.10 (x64, ARM)|
|NATIVNÍ (bez /DRIVER:WDM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION, BITOVÁ KOPIE EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte složku Linkeru.

1. Vyberte **systému** stránku vlastností.

1. Upravit `SubSystem` vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)