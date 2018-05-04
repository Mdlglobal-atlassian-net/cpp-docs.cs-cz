---
title: Export funkcí z knihovny DLL podle pořadových nikoli podle názvu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- NONAME
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b05f3e429406b3c24c7a21ce9ee8e10fe19c14b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu
Nejjednodušší způsob, jak funkce exportu z vaší knihovny DLL je k jejich exportování podle názvu. To se stane, když používáte **__declspec(dllexport)**, např. Ale místo toho můžete exportovat funkce podle pořadí. S touto technikou, musíte použít soubor .def místo **__declspec(dllexport)**. K určení pořadového čísla funkce, připojí k názvu funkce v souboru .def jeho pořadí. Informace o určování pořadí najdete v tématu [export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md).  
  
> [!TIP]
>  Pokud chcete optimalizovat velikost souboru knihovny DLL, použijte **NONAME** atribut na každé exportované funkci. S **NONAME** atribut pořadová čísla jsou uložené v knihovnu DLL export tabulky namísto názvů funkce. Pokud exportujete mnoho funkcí, může to být značné úspory.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Použít soubor .def exportování podle pořadí](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Použijte __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)