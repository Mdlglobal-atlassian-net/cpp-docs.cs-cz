---
title: Určení názvu cesty
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: f83adcb87994d13edd1c1579183377a365e2051e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638357"
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

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)