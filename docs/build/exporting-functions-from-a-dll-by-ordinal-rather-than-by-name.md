---
title: "Export funkcí z knihovny DLL podle pořadových nikoli podle názvu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17b49cc54336f596d6815a2ebe53e60ed2dd51e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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