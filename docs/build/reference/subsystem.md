---
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: 5fda93951918357de5441022f1cc6ea81a522ef6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415133"
---
# <a name="subsystem"></a>/SUBSYSTEM

Určuje prostředí spuštění, který se vyžaduje spustitelná bitová kopie.

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>Poznámky

Tato možnost upraví obrázek k označení, který podsystém musí vyvolat operační systém pro spuštění.

Můžete určit kterékoli z následujících subsystémů:

**BOOT_APPLICATION**<br/>
Aplikace, která běží v prostředí spouštění Windows. Další informace o spouštěcích aplikacích najdete v tématu [o poskytovateli WMI BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**KONZOLY**<br/>
Aplikace znakového režimu Windows. Operační systém poskytuje konzolu pro konzolové aplikace.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Obrázek Extensible Firmware Interface (EFI)

Možnosti subsystému EFI popisují spustitelné bitové kopie, které běží v prostředí Extensible Firmware Interface. Toto prostředí je obvykle součástí hardware a spustí se před načtením operačního systému. Hlavní rozdíly mezi typy obrázků EFI jsou umístění v paměti, která obrázek nahrán a akce, která se provede, když vrátí volání image. Bitová kopie EFI_APPLICATION je uvolněna při vrácení ovládacího prvku. Je bitová kopie EFI_BOOT_SERVICE_DRIVER nebo EFI_RUNTIME_DRIVER je uvolněna pouze v případě, že ovládací prvek vrácen chybový kód. Bitová kopie EFI_ROM je spouštěna z paměti ROM. Další informace najdete v tématu specifikace na [Unified EFI Forum](http://www.uefi.org/) webu.

**NATIVNÍ**<br/>
Kód, který běží bez prostředí podsystému – například ovladače zařízení režimu jádra a nativní systémové procesy. Tato možnost je obvykle vyhrazena pro funkce systému Windows.

**POSIX**<br/>
Aplikace, která běží v subsystému POSIX spouštět ve Windows.

**SYSTÉM WINDOWS**<br/>
Aplikace, která běží v grafickém prostředí Windows. To zahrnuje aplikací klasické pracovní plochy a aplikace pro univerzální platformu Windows (UPW).

**WINDOWSCE**<br/>
Podsystém WINDOWSCE označuje, že aplikace je určena pro spuštění na zařízení, které má verzi jádra Windows CE. Verze jádra obsahují počítače PocketPC, Windows Mobile, Windows Phone 7, Windows CE verze 1.0 6.0R3 a Windows Embedded Compact 7.

Volitelný `major` a `minor` hodnoty určují minimální požadovanou verzi zadaného subsystému:

- Část celého čísla, čísla verze – část vlevo od desetinné čárky, je reprezentována `major`.

- Desetinnou část čísla verze – část vpravo od desetinné čárky, je reprezentována `minor`.

- Hodnoty `major` a `minor` musí být v rozsahu 0 až 65535.

Volba subsystému ovlivňuje výchozí počáteční adresu programu. Další informace najdete v tématu [/Entry (Symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md), linker/Entry:*funkce* možnost.

Další informace, včetně minimální a výchozí hodnoty pro číslo hlavní verze a podverze pro každý subsystém naleznete v tématu [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) – možnost linkeru.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](../../build/reference/editbin-options.md)
