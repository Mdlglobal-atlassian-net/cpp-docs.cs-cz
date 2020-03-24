---
title: Závažná chyba nástroje NMAKE U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 3eda424574dfa48901cf4dc6aea3b28beb739dc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193716"
---
# <a name="nmake-fatal-error-u1035"></a>Závažná chyba nástroje NMAKE U1035

Chyba syntaxe: byl očekáván oddělovač ': ' nebo ' = '

Očekávala se dvojtečka ( **:** ) nebo rovnítko ( **=** ).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Dvojtečka nesledovala cíl.

1. Dvojtečka a žádná mezera (například:) Následuje cíl s jedním písmenem. NMAKE ho interpretoval jako specifikaci jednotky.

1. Dvojtečka nesledovala pravidlo odvození.

1. Na definici makra nebyl následovat rovnítko.

1. Znak následovaný zpětným lomítkem ( **\\** ), který se použil k pokračování příkazu na nový řádek.

1. Zobrazil se řetězec, který nedodržuje žádné pravidlo syntaxe NMAKE.

1. Soubor pravidel byl formátován procesorem slov.
