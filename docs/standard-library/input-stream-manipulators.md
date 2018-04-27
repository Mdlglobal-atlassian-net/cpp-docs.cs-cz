---
title: Vstupní datový proud manipulátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4f7542579ade578f449a621028d210186bcbbf8e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="input-stream-manipulators"></a>Manipulátory vstupního datového proudu

Mnoho manipulátory, jako například [setprecision](../standard-library/iomanip-functions.md#setprecision), jsou definovány pro `ios` třídy a proto použít pro vstupní datové proudy. Několik manipulátory, ale ve skutečnosti ovlivnit objektů vstupního datového proudu. Z těch, které provádějí, nejdůležitější jsou základ – manipulátory, `dec`, `oct`, a `hex`, které určují, převod základní použít s čísla ze vstupního datového proudu.

Na extrakci `hex` manipulator umožňuje zpracování různými vstupní formáty. Například c C, 0xc, 0xC, 0Xc a 0XC všechny interpretovány jako desetinné číslo 12. Libovolný znak než 0 až 9, A až F, a až f, x a X ukončí číselný převod. Proto pořadí `"124n5"` jsou převedeny na číslo 124 s [basic_ios::fail](../standard-library/basic-ios-class.md#fail) sadu bitů.

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
