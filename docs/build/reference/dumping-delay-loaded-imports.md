---
title: Vypsání importy s odloženým načtením | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13f832f0ea7aaf7b766141ce7df4f83f21e1cdca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="dumping-delay-loaded-imports"></a>Výpis importu se zpožděným načtením
Importy s odloženým načtením můžete vypsat pomocí [/Imports dumpbin](../../build/reference/imports-dumpbin.md) a zobrazí se mírně liší informace než importuje standard. Tyto jsou rozdělen na vlastní část/Imports vypsání a jsou explicitně označeny jako importy s odloženým načtením. Pokud je uvolnit informace obsažené v bitové kopii, která poznamenat. Pokud je přítomen vazby informací, je třeba časového razítka cílový DLL poznamenat spolu s vázané adresy import.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)