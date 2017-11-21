---
title: "Vypsání importy s odloženým načtením | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2104165bf466473d89270eb502e3357713579f38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dumping-delay-loaded-imports"></a>Výpis importu se zpožděným načtením
Importy s odloženým načtením můžete vypsat pomocí [/Imports dumpbin](../../build/reference/imports-dumpbin.md) a zobrazí se mírně liší informace než importuje standard. Tyto jsou rozdělen na vlastní část/Imports vypsání a jsou explicitně označeny jako importy s odloženým načtením. Pokud je uvolnit informace obsažené v bitové kopii, která poznamenat. Pokud je přítomen vazby informací, je třeba časového razítka cílový DLL poznamenat spolu s vázané adresy import.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)