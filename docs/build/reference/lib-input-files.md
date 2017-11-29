---
title: "Vstupní soubory LIB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Lib
dev_langs: C++
helpviewer_keywords: input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f956dedb8be270eb9974fa035d38e7fbb6714499
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lib-input-files"></a>Vstupní soubory LIB
Vstupní soubory LIB očekávanou závisí na režimu, ve kterém se právě používá, jak je znázorněno v následující tabulce.  
  
|Režim|Vstup|  
|----------|-----------|  
|Výchozí (vytváříte nebo upravujete knihovnu)|Soubory COFF objektu (.obj), knihoven COFF (LIB), soubory objektů (.obj) 32-bit objektu modelu formátu (OMF)|  
|Extrahování člena s/extract|Knihovna COFF (LIB)|  
|Vytváření exportu souboru a importovat knihovna/def|Soubor definice modulu (.def), soubory COFF objektů (.obj), knihoven COFF (LIB), 32bitové OMF – soubory objektů (.obj)|  
  
> [!NOTE]
>  Knihovny OMF vytvořená 16bitové verzi LIB nelze použít jako vstup na 32bitové verzi LIB.  
  
## <a name="see-also"></a>Viz také  
 [Přehled LIB](../../build/reference/overview-of-lib.md)