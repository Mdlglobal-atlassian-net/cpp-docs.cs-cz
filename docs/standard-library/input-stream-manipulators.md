---
title: Manipulátory vstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: d9a6f00f1b5a52d4d388ace376676b45547bdd49
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451032"
---
# <a name="input-stream-manipulators"></a>Manipulátory vstupního datového proudu

Pro`ios` třídu je definováno mnoho různých manipulátorů, jako je [setprecision](../standard-library/iomanip-functions.md#setprecision), a proto se aplikují na vstupní datové proudy. Několik manipulací ale ve skutečnosti ovlivňuje vstupní objekty datového proudu. Z těch, které jsou, nejdůležitějšími jsou manipulace s číselnou soustavou `dec`, `oct`, a `hex`, které určují základ pro převod, který se používá s čísly ze vstupního datového proudu.

Při extrakci `hex` manipulátor umožňuje zpracování různých vstupních formátů. Například c, C, 0xC, 0xC, 0Xc a 0XC jsou interpretovány jako desítkové celé číslo 12. Libovolný znak jiný než 0 až 9, a až F, a až f, x a X ukončí číselný převod. Proto je sekvence `"124n5"` převedena na číslo 124 s nastavenou bitovou sadou [basic_ios:: selhání](../standard-library/basic-ios-class.md#fail) .

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)
