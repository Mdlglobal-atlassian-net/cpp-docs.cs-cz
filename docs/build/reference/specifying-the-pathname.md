---
title: Určení názvu cesty
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: dcff3610255c40f4e06201e52a53eb5dd965a4be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317936"
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

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
