---
title: "Předdefinované symboly systému Win32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols, Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 865d61611546e2550aaa241220dc226cea9f9b81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="win32-predefined-symbols"></a>Předdefinované symboly systému Win32
Tyto symboly jsou definovány v záhlaví souborů Win32 a podporují standardní funkce aplikací systému Windows a akce. Tyto symboly jsou používány především s společné prvky uživatelského rozhraní. Při práci s ovládacími prvky v editory prostředků, zobrazí se tyto symboly v [vlastnosti – okno](/visualstudio/ide/reference/properties-window) přidružené běžné ovládací prvky. Například pokud vaše panelu nástrojů by měla zobrazovat ikona aplikace, na ikonu bude spojený s symbol IDI_SMALL v okně Vlastnosti.  
  
|||  
|-|-|  
|IDABORT|Řízení: Tlačítko dialogovém přerušení|  
|IDC_STATIC|Ovládací prvek: Statický text v dialogovém okně|  
|IDCANCEL|Ovládacího prvku: Tlačítko Zrušit pole dialogové okno|  
|IDD_ABOUTBOX|Dialogové okno: Produktu o dialogové okno|  
|IDI_PROJECTNAME|Ikona: Aktuální projekt – ikona|  
|IDI_SMALL|Ikona: Aktuální projekt malé ikony|  
|IDIGNORE|Ovládací prvek: Použít klepnutím na tlačítko Ignorovat v dialogová okna|  
|IDM_ABOUT|Položka nabídky: Používá pomoci... O...|  
|IDM_EXIT|Položka nabídky: Používá se souborem... Ukončení...|  
|IDNO|Ovládací prvek: Žádné tlačítko dialogu|  
|IDOK|Ovládacího prvku: Tlačítko pole OK dialogové okno|  
|IDRETRY|Řízení: Tlačítko dialogovém opakování|  
|IDS_APP_TITLE|Řetězec: Název aktuální aplikace|  
|IDYES|Ovládací prvek: Dialogové okno Ano tlačítko.|  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)   
 [Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)