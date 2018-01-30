---
title: "Vstupní datový proud manipulátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce3f1b99fe44d07a8793501c800f32077509ec0d
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="input-stream-manipulators"></a>Manipulátory vstupního datového proudu
Mnoho manipulátory, jako například [setprecision](../standard-library/iomanip-functions.md#setprecision), jsou definovány pro `ios` třídy a proto použít pro vstupní datové proudy. Několik manipulátory, ale ve skutečnosti ovlivnit objektů vstupního datového proudu. Z těch, které provádějí, nejdůležitější jsou základ – manipulátory, `dec`, `oct`, a `hex`, které určují, převod základní použít s čísla ze vstupního datového proudu.  
  
 Na extrakci `hex` manipulator umožňuje zpracování různými vstupní formáty. Například c C, 0xc, 0xC, 0Xc a 0XC všechny interpretovány jako desetinné číslo 12. Libovolný znak než 0 až 9, A až F, a až f, x a X ukončí číselný převod. Proto pořadí `"124n5"` jsou převedeny na číslo 124 s [basic_ios::fail](../standard-library/basic-ios-class.md#fail) sadu bitů.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

