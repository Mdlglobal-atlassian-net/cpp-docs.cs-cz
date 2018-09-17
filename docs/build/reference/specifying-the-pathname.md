---
title: Určení názvu cesty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86052d6ca6e40926ed8d99990520044cef351d3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719313"
---
# <a name="specifying-the-pathname"></a>Určení názvu cesty

Jednotlivé možnosti výstupního souboru přijímá *cesta* argument, který můžete zadat umístění a název výstupního souboru. Název jednotky, adresář a název souboru může obsahovat argument. Žádné místo smí mezi možností a argumentem.

Pokud *cesta* zahrnovat název souboru bez přípony, kompilátor poskytuje výstup výchozí příponou. Pokud *cesta* zahrnuje do adresáře, ale žádný název souboru, kompilátor vytvoří soubor s výchozím názvem v zadaném adresáři. Výchozí název je založen na základní název zdrojového souboru a výchozí rozšíření založené na typ výstupního souboru. Pokud toto *cesta* zcela, kompilátor vytvoří soubor s výchozím názvem ve výchozím adresáři.

Další možností *cesta* argument může být název zařízení (AUX, CON, PRN nebo NUL) místo názvu souboru. Nepoužívejte mezery mezi parametrem a název zařízení nebo dvojtečka jako součást názvu zařízení.

|Název zařízení|Představuje|
|-----------------|----------------|
|AUX|Pomocné zařízení|
|CON|Konzola|
|PRN|Tiskárny|
|NUL|Null zařízení (vytvořen žádný soubor)|

## <a name="example"></a>Příklad

Následující příkaz odešle soubor mapy tiskárny:

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>Viz také

[Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)