---
title: Vstup a výstup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09212570dec6c64687a8b8b4b30f95174c4000ff
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="input-and-output"></a>Vstup a výstup

Funkce vstupně-výstupní operace čtení a zápisu dat do a z soubory a zařízení. Soubor vstupně-výstupních operací provést v režimu textových nebo binární. Běhové knihovny Microsoft má tři typy vstupně-výstupních operací funkce:

- [Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md) funkce považovat za datový proud jednotlivých znaků.

- [I/O nízké úrovně](../c-runtime-library/low-level-i-o.md) vyvolání funkce operačního systému přímo pro operaci nižší úrovni než poskytované datového proudu vstupně-výstupní operace.

- [Konzoly a portu vstupně-výstupních operací](../c-runtime-library/console-and-port-i-o.md) funkce číst nebo zapisovat přímo do konzoly (klávesnice a obrazovky) nebo k portu vstupně-výstupní operace (například port tiskárny).

   > [!NOTE]
   > Protože jsou tyto funkce datového proudu do vyrovnávací paměti a nízké úrovně funkce nejsou, jsou tyto dva typy funkcí obecně kompatibilní. Pro zpracování určitého souboru, použijte výlučně datový proud nebo funkce na nižší úrovni.

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
