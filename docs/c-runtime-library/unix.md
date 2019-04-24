---
title: UNIX
ms.date: 11/04/2016
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: edabb639d8f45680415473ad7b017d426b931ab5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304186"
---
# <a name="unix"></a>UNIX

Pokud plánujete přenést svých programů určených pro UNIX, postupujte podle následujících pokynů:

- Neodebírejte hlavičkové soubory z podadresáře SYS. Soubory hlaviček SYS můžete umístit kdekoli pouze v případě, že nemáte v plánu k přenosu svých programů určených pro systém UNIX.

- Použijte oddělovač cesty kompatibilního se systémem UNIX ve rutin, které přijímají řetězce představující cesty a názvy souborů jako argumenty. UNIX podporuje pouze dopředné lomítko (/) pro tento účel, zatímco Win32 operační systémy podporují oba zpětné lomítko (\\) a lomítkem (/). Proto tato dokumentace používá kompatibilního se systémem UNIX lomítka jako oddělovače cesty v `#include` příkazy pro příklad. (Ale operační systém Windows příkazové okno, které cmd Soubor EXE, nepodporuje lomítko v příkazy zadané na příkazovém řádku.)

- Pomocí cesty a názvy souborů, které fungují správně v systému UNIX, což je velká a malá písmena. Systém souborů (FAT table) přidělení soubor v operační systémy Win32 není malá a velká písmena; systém souborů NTFS zachová případ výpisech adresářů, ale ignoruje velikost písmen v hledání souborů a dalších operací systému.

    > [!NOTE]
    >  V této verzi systému Visual C++ informace o kompatibilitě systému UNIX byl odebrán z funkce popisy.

## <a name="see-also"></a>Viz také:

[Kompatibilita](../c-runtime-library/compatibility.md)
