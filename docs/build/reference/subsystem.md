---
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem_editbin
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: 708bfcce3e6d6616116bcc08441f374b46914c82
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438859"
---
# <a name="subsystem"></a>/SUBSYSTEM

Určuje spouštěcí prostředí vyžadované spustitelným obrázkem.

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>Poznámky

Tato možnost upraví image, aby označovala, který podsystém musí operační systém vyvolat ke spuštění.

Můžete zadat libovolný z následujících subsystémů:

**BOOT_APPLICATION**<br/>
Aplikace, která běží ve spouštěcím prostředí systému Windows. Další informace o spouštěcích aplikacích najdete v tématu [o poskytovateli rozhraní WMI BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**STROMU**<br/>
Aplikace v režimu znaků systému Windows. Operační systém poskytuje konzolovou aplikaci pro konzolové aplikace.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Obrázek EFI (Extensible Firmware Interface)

Možnosti subsystému EFI popisují spustitelné bitové kopie, které běží v prostředí Extensible Firmware Interface. Toto prostředí se obvykle poskytuje s hardwarem a spouští se před tím, než se načte operační systém. Hlavní rozdíly mezi typy imagí rozhraní EFI jsou paměťové umístění, do kterého je bitová kopie načtena, a akci, která je provedena v případě, že volání obrázku vrátí. Při návratu ovládacího prvku se obrázek EFI_APPLICATION uvolní. EFI_BOOT_SERVICE_DRIVER nebo EFI_RUNTIME_DRIVER jsou uvolněny pouze v případě, že se ovládací prvek vrátí s kódem chyby. Z paměti ROM se spustí EFI_ROM image. Další informace najdete v tématu specifikace na webu [Unified EFI Forum](https://www.uefi.org/) .

**NATIVNÍ**<br/>
Kód, který běží bez prostředí subsystému, například ovladače zařízení režimu jádra a nativní systémové procesy. Tato možnost je obvykle vyhrazena pro funkce systému Windows.

**Standard**<br/>
Aplikace, která běží v subsystému POSIX v systému Windows.

**SYSTÉMU**<br/>
Aplikace, která běží v grafickém prostředí systému Windows. To zahrnuje desktopové aplikace a aplikace Univerzální platforma Windows (UWP).

**WINDOWSCE**<br/>
Podsystém WINDOWSCE označuje, že aplikace je určená ke spuštění na zařízení, které má verzi systém Windows CE jádra. Mezi verze jádra patří PocketPC, Windows Mobile, Windows Phone 7, systém Windows CE V 1.0 – 6.0 R3 a Windows Embedded Compact 7.

Volitelné `major` a hodnoty `minor` určují minimální požadovanou verzi zadaného subsystému:

- Část čísla verze celé číslo – část nalevo od desetinné čárky, je reprezentována `major`.

- Zlomková část čísla verze – část napravo od desetinné čárky, je reprezentována `minor`.

- Hodnoty `major` a `minor` musí být od 0 do 65 535.

Volba subsystému má vliv na výchozí počáteční adresu programu. Další informace naleznete v tématu [/entry (symbol vstupního bodu)](entry-entry-point-symbol.md), parametr linker/ENTRY:*Function* .

Další informace, včetně minimální a výchozí hodnoty pro čísla hlavních a dílčích verzí každého subsystému, naleznete v možnosti linker [/Subsystem](subsystem-specify-subsystem.md) .

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](editbin-options.md)
