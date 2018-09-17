---
title: – V ROZSAHU | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e7525b8c1872616182141d624bff8f94571952
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712189"
---
# <a name="range"></a>/RANGE

Změní výstup dumpbin při použití s další možnosti dumpbin, jako je například /RAWDATA nebo /DISASM.

## <a name="syntax"></a>Syntaxe

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>Parametry

*vaMin*<br/>
Virtuální adresa, na které má operace dumpbin zahájíte.

*vaMax*<br/>
(Volitelné) Virtuální adresu, na které má operace dumpbin pro ukončení. Pokud není zadán, dumpbin přejdete na konec souboru.

## <a name="remarks"></a>Poznámky

Pokud chcete zobrazit virtuální adresy pro bitovou kopii, použijte soubor mapy pro bitovou kopii (RVA + Base), **/DISASM** nebo **/HEADERS** – možnost nástroje dumpbin, nebo v okně zpětný překlad v ladicím programu sady Visual Studio.

## <a name="example"></a>Příklad

V tomto příkladu **/rozsahu** se používá k úpravě zobrazení **/disasm** možnost. V tomto příkladu výchozí hodnota je vyjádřena jako desítkové číslo a koncová hodnota je určena jako šestnáctkové číslo.

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)