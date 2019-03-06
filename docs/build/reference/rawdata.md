---
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: 4e884ba8bca7b3ccdf900c7da2c43dd741c03d12
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413365"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazí nezpracované obsah jednotlivých oddílů v souboru. Argumenty řídit formát zobrazení, jak je znázorněno níže:

|Argument|Výsledek|
|--------------|------------|
|1|Výchozí nastavení Obsah se zobrazí šestnáctkové bajty a taky jako znaků ASCII, pokud mají tištěné reprezentace.|
|2|Obsah se zobrazí jako šestnáctkové hodnoty 2 bajtů.|
|4|Obsah se zobrazí jako šestnáctkové hodnoty 4 bajty.|
|8|Obsah se zobrazí jako šestnáctkové hodnoty 8 bajtů.|
|NONE|Nezpracovaná data je potlačeno. Tento argument je vhodné pro řízení výstup/ALL.|
|*Číslo*|Zobrazené řádky jsou nastavena na šířku, která obsahuje `number` hodnot pro každý řádek.|

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
