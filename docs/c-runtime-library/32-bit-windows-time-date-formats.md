---
title: Formáty data a času Windows 32-bit
ms.date: 11/04/2016
f1_keywords:
- vc.time
helpviewer_keywords:
- 32-bit Windows
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
ms.openlocfilehash: 4827f82df08273dfa369d6242b9fe2be84875128
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746354"
---
# <a name="32-bit-windows-timedate-formats"></a>Formáty času a data 32bitového systému Windows

Datum a čas souboru jsou uloženy jednotlivě, pomocí jako bitová pole celých čísel bez znaménka. Datum a čas souboru jsou zkomprimována následujícím způsobem:

### <a name="time"></a>Čas

|Bitová pozice:|0   1   2   3   4|5   6   7   8   9   A|B   C   D   E   F|
|-------------------|-----------------------|---------------------------|-----------------------|
|Délka:|5|6|5|
|Obsah:|hodiny|minuty|zvýší na 2 sekundy|
|Rozsah hodnot:|0-23|0-59|0 – 29 v 2-druhá intervaly|

### <a name="date"></a>Datum

|Bitová pozice:|0   1   2   3   4   5   6|7   8   9   A|B   C   D   E   F|
|-------------------|-------------------------------|-------------------|-----------------------|
|Délka:|7|4|5|
|Obsah:|rok|měsíc|den|
|Rozsah hodnot:|0-119|1-12|1-31|
||(relativní vůči adresáři 1980)|||

## <a name="see-also"></a>Viz také:

[Globální konstanty](../c-runtime-library/global-constants.md)
