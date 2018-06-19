---
title: UNIX | Microsoft Docs
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
ms.openlocfilehash: c2403eb0fbe19f83df3909c9d8b765f00fed82c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409316"
---
# <a name="unix"></a>UNIX
Pokud máte v plánu k portu programy pro UNIX, postupujte podle těchto pokynů:  
  
-   Neodebírejte hlavičkových souborů z podadresáře SYS. Soubory hlaviček SYS můžete umístit jinde pouze v případě, že neplánujete přenosu programy a UNIX.  
  
-   Použijte oddělovač cesty UNIX kompatibilní v rutin, které přijímají řetězce představující cesty a názvy souborů jako argumenty. UNIX podporuje pouze dopředné lomítko (/) pro tento účel, zatímco Win32 operační systémy podporují i zpětné lomítko (\\) a lomítkem (/). Proto tato dokumentace používá UNIX kompatibilní lomítka jako oddělovače cestu v `#include` příkazy, například. (Ale operační systém Windows příkazovém prostředí CMD. EXE nepodporuje dopředné lomítko v příkazech zadat na příkazovém řádku.)  
  
-   Pomocí cesty a názvy souborů, které fungují správně v systému UNIX, který je malá a velká písmena. Systém souborů přidělení tabulky (FAT) soubor v operačních systémech Win32 není velká a malá písmena; systém souborů NTFS zachovává případ výpisech adresářů, ale ignoruje velikost písmen v hledání souborů a další operace systému.  
  
    > [!NOTE]
    >  V této verzi Visual C++ informace o kompatibilitě UNIX odebral z funkce popisy.  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita](../c-runtime-library/compatibility.md)