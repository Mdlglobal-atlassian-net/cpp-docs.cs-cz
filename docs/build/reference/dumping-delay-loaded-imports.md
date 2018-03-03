---
title: "Vypsání importy s odloženým načtením | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3800d4863bc1aa3e3c847ff0cea886be2fede985
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dumping-delay-loaded-imports"></a>Výpis importu se zpožděným načtením
Importy s odloženým načtením můžete vypsat pomocí [/Imports dumpbin](../../build/reference/imports-dumpbin.md) a zobrazí se mírně liší informace než importuje standard. Tyto jsou rozdělen na vlastní část/Imports vypsání a jsou explicitně označeny jako importy s odloženým načtením. Pokud je uvolnit informace obsažené v bitové kopii, která poznamenat. Pokud je přítomen vazby informací, je třeba časového razítka cílový DLL poznamenat spolu s vázané adresy import.  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)