---
title: Vstupní datový proud manipulátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30f642dc4942491bd73265e3d647d3281f97c1e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="input-stream-manipulators"></a>Manipulátory vstupního datového proudu

Mnoho manipulátory, jako například [setprecision](../standard-library/iomanip-functions.md#setprecision), jsou definovány pro `ios` třídy a proto použít pro vstupní datové proudy. Několik manipulátory, ale ve skutečnosti ovlivnit objektů vstupního datového proudu. Z těch, které provádějí, nejdůležitější jsou základ – manipulátory, `dec`, `oct`, a `hex`, které určují, převod základní použít s čísla ze vstupního datového proudu.

Na extrakci `hex` manipulator umožňuje zpracování různými vstupní formáty. Například c C, 0xc, 0xC, 0Xc a 0XC všechny interpretovány jako desetinné číslo 12. Libovolný znak než 0 až 9, A až F, a až f, x a X ukončí číselný převod. Proto pořadí `"124n5"` jsou převedeny na číslo 124 s [basic_ios::fail](../standard-library/basic-ios-class.md#fail) sadu bitů.

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
