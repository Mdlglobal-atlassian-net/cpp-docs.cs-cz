---
title: UNIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- unix
dev_langs:
- C++
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d0343a7a508e09e3bd7779308cb40972965a716
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032949"
---
# <a name="unix"></a>UNIX

Pokud plánujete přenést svých programů určených pro UNIX, postupujte podle následujících pokynů:

- Neodebírejte hlavičkové soubory z podadresáře SYS. Soubory hlaviček SYS můžete umístit kdekoli pouze v případě, že nemáte v plánu k přenosu svých programů určených pro systém UNIX.

- Použijte oddělovač cesty kompatibilního se systémem UNIX ve rutin, které přijímají řetězce představující cesty a názvy souborů jako argumenty. UNIX podporuje pouze dopředné lomítko (/) pro tento účel, zatímco Win32 operační systémy podporují oba zpětné lomítko (\\) a lomítkem (/). Proto tato dokumentace používá kompatibilního se systémem UNIX lomítka jako oddělovače cesty v `#include` příkazy pro příklad. (Ale operační systém Windows příkazové okno, které cmd Soubor EXE, nepodporuje lomítko v příkazy zadané na příkazovém řádku.)

- Pomocí cesty a názvy souborů, které fungují správně v systému UNIX, což je velká a malá písmena. Systém souborů (FAT table) přidělení soubor v operační systémy Win32 není malá a velká písmena; systém souborů NTFS zachová případ výpisech adresářů, ale ignoruje velikost písmen v hledání souborů a dalších operací systému.

    > [!NOTE]
    >  V této verzi systému Visual C++ informace o kompatibilitě systému UNIX byl odebrán z funkce popisy.

## <a name="see-also"></a>Viz také

[Kompatibilita](../c-runtime-library/compatibility.md)