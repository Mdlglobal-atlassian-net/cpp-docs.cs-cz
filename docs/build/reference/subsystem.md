---
title: -SUBSYSTEM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c12df1a2166c9ef5a1af8a33a5764a8899909edb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377620"
---
# <a name="subsystem"></a>/SUBSYSTEM
Určuje prostředí pro spuštění, který je požadován spustitelné bitové kopie.  
  
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|  
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost slouží k úpravě bitovou kopii k označení které subsystém, operační systém musí vyvolat pro spuštění.  
  
 Můžete zadat jakýkoli subsystémů následující:  
  
 BOOT_APPLICATION  
 Aplikace, která běží v prostředí spouštění systému Windows. Další informace o spouštění aplikací najdete v tématu [o BCD WMI poskytovatel](http://msdn.microsoft.com/library/aa362639.aspx).  
  
 KONZOLA  
 Aplikace systému Windows režim znaků. Operační systém poskytuje konzoli pro konzolové aplikace.  
  
 Obrázek Extensible Firmware rozhraní EFI)  
 Možnosti subsystému EFI popisují spustitelné bitové kopie, které běží v prostředí Extensible Firmware Interface. Toto prostředí se většinou poskytuje s hardwarem a provede předtím, než je načtený operační systém. Hlavní rozdíly mezi typy obrázků EFI jsou umístění v paměti, který bitovou kopii je načten do a akce, která je provedená při volání do bitové kopie. Bitová kopie EFI_APPLICATION je odpojen, když se vrátí ovládací prvek. EFI_BOOT_SERVICE_DRIVER nebo EFI_RUNTIME_DRIVER je odpojen pouze v případě, že je ovládací prvek vrátí s kódem chyby. Obrázek EFI_ROM se spustí z ROM. Další informace najdete v tématu specifikace na [Unified EFI Forum](http://www.uefi.org/) webu.  
  
 NATIVNÍ  
 Kód, který spouští bez subsystém prostředí – například ovladačů zařízení v režimu jádra a nativní systémových procesů. Tato možnost je obvykle vyhrazený pro funkce systému Windows.  
  
 POSIX  
 Aplikaci, která běží v subsystému POSIX v systému Windows.  
  
 WINDOWS  
 Aplikaci, která běží v grafickém prostředí systému Windows. To zahrnuje aplikace klasické pracovní plochy a aplikace pro univerzální platformu Windows (UWP).  
  
 WINDOWSCE  
 Subsystém WINDOWSCE označuje, že aplikace je určený pro spouštění v zařízení, které má verzi jádra Windows CE. Verze jádra obsahují počítače PocketPC, Windows Mobile, Windows Phone 7, Windows CE verze 1.0 6.0R3 a systém Windows Embedded Compact 7.  
  
 Volitelné `major` a `minor` hodnoty určují minimální požadovaná verze zadané subsystému:  
  
-   Celé číslo součástí číslo verze – část směrem doleva od desetinné čárky – je reprezentována `major`.  
  
-   Zlomkové části čísla verze – část vpravo od desetinné čárky – je reprezentována `minor`.  
  
-   Hodnoty `major` a `minor` musí být od 0 do 65 535.  
  
 Volba subsystému ovlivní výchozí počáteční adresa programu. Další informace najdete v tématu [/Entry (Symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md), linkeru/Entry:*funkce* možnost.  
  
 Další informace, včetně minimální a výchozí hodnoty pro hlavní verze a podverze čísla pro každý subsystém, najdete v článku [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) – možnost linkeru.  
  
## <a name="see-also"></a>Viz také  
 [EDITBIN – možnosti](../../build/reference/editbin-options.md)