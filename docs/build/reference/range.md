---
title: /RANGE
ms.date: 11/04/2016
f1_keywords:
- /RANGE
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
ms.openlocfilehash: c631057e47e1a52a58d2b1304133dfdfc008ae14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319704"
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

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
