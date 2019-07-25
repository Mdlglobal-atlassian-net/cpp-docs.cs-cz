---
title: Používání operátorů extrakce
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 7950984973f8df236905128ce4b5336ecb874b7f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458040"
---
# <a name="using-extraction-operators"></a>Používání operátorů extrakce

Operátor extrakce (`>>`), který je přednaprogramován pro všechny standardní C++ datové typy, představuje nejjednodušší způsob, jak získat bajty z objektu vstupního datového proudu.

Operátory extrakce textu formátovaného textu závisejí na mezerách pro oddělení hodnot příchozích dat. To je nevhodné, pokud textové pole obsahuje více slov nebo oddělovače čísel. V takovém případě je jednou alternativou použití neformátované vstupní členské funkce [IStream:: getline](../standard-library/basic-istream-class.md#getline) ke čtení bloku textu s mezerami, které jsou součástí vložených znaků, a pak Analyzujte blok pomocí speciálních funkcí. Další metodou je odvození třídy vstupního datového proudu s členskou funkcí `GetNextToken`, jako například, která může volat členy IStream k extrakci a formátování znakových dat.

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)
