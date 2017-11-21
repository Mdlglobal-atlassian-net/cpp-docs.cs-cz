---
title: "Vstupní datový proud manipulátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4aaea7ac729eeb34c224e55883fe4397b97d3e62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="input-stream-manipulators"></a>Manipulátory vstupního datového proudu
Mnoho manipulátory, jako je například [setprecision]--brokenlink--(.. / Topic/not%20found:3ddde610-70cc-4cfa-8a89-3e83d1d356a8.md#setprecision), jsou definovány pro `ios` třídy a proto použít pro vstupní datové proudy. Několik manipulátory, ale ve skutečnosti ovlivnit objektů vstupního datového proudu. Z těch, které provádějí, nejdůležitější jsou základ – manipulátory, `dec`, `oct`, a `hex`, které určují, převod základní použít s čísla ze vstupního datového proudu.  
  
 Na extrakci `hex` manipulator umožňuje zpracování různými vstupní formáty. Například c C, 0xc, 0xC, 0Xc a 0XC všechny interpretovány jako desetinné číslo 12. Libovolný znak než 0 až 9, A až F, a až f, x a X ukončí číselný převod. Proto pořadí `"124n5"` jsou převedeny na číslo 124 s [basic_ios::fail](../standard-library/basic-ios-class.md#fail) sadu bitů.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní datové proudy](../standard-library/input-streams.md)

