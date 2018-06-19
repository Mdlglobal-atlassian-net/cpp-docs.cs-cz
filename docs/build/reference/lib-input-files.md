---
title: Vstupní soubory LIB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 140a0f1d9ef6fdb3ca5e6d6977804684c88af1fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371964"
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
 [Přehled knihovny LIB](../../build/reference/overview-of-lib.md)