---
title: "Postupy: zahrnutí prostředků v době kompilace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
dev_langs: C++
helpviewer_keywords:
- compiling source code, including resources
- comments [C++], compiled files
- resources [Visual Studio], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ea8ba64c7dbf609eb23fb2d7d0e0b739d06dc0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-include-resources-at-compile-time"></a>Postupy: Zahrnutí prostředků v čase kompilace
Obvykle je snadný a pohodlný pro práci s výchozí uspořádání všechny prostředky v souboru skriptu (.rc) jeden prostředek. Však přidáním prostředků v dalších souborů do aktuálního projektu v době kompilace tak, že je v uvedete **kompilaci direktivy** pole [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md).  
  
 Tady je několik důvodů umístit prostředky v souboru než hlavní soubor:  
  
-   K přidání komentářů se příkazy prostředků, které nebudou získat odstraněny při uložení souboru .rc.  
  
     Editory prostředků nečtou soubory .rc nebo resource.h přímo. Kompilátor prostředků je zkompiluje do .aps soubory, které se spotřebovávají editory prostředků. Tento soubor je krok kompilace a ukládá jenom symbolický data. Jako normální kompilaci proces, informace, které není symbolický (například komentáře) se zahodí během kompilace. Vždy, když soubor .aps získá synchronizována se soubor, znovu vygeneruje soubor (například když uložíte, editor prostředků přepíše .rc soubor a soubor resource.h). Všechny změny prostředků sami zůstanou zahrnuté v souboru .rc, ale komentáře vždy budou ztraceny po .rc soubor se přepíše.  
  
-   Zahrnout prostředky, které již byla vyvinuta a testována a nepotřebujete další úpravy. (Všechny soubory, které jsou zahrnuty, ale nemáte rozšíření .rc nebudou upravovat editory prostředků.)  
  
-   Chcete-li zahrnout zdroje, které jsou používány několik různých projektů nebo které jsou součástí zdrojového kódu Správa verzí a proto musí existovat v centrálním umístění, kde změny bude mít vliv na všechny projekty.  
  
-   Zahrnout prostředky (například RCDATA prostředky), které jsou ve vlastním formátu. Prostředky RCDATA může mít zvláštní požadavky. Výraz nelze použít například jako hodnota pro pole nameID. Najdete v článku [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] Další informace naleznete v dokumentaci.  
  
 Pokud máte ve existující soubory .rc, které splnit některý z těchto podmínek části, byste měli umístit v oddílech v jednom nebo více oddělené soubory .rc a zahrnout je do vašeho projektu pomocí [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md). *Projectname*.rc2 soubor vytvořený v podadresáři \res nový projekt se používá pro tento účel.  
  
### <a name="to-include-resources-in-your-project-at-compile-time"></a>Zahrnout prostředky ve vašem projektu v době kompilace  
  
1.  Umístíte prostředky v souboru skriptu prostředků s jedinečný název souboru. Nepoužívejte *projectname*.rc, protože to je název souboru pro soubor skriptu hlavní prostředků.  
  
2.  Klikněte pravým tlačítkem na soubor (v [zobrazení prostředků](../windows/resource-view-window.md)) a zvolte **prostředek zahrnuje** z místní nabídky.  
  
3.  V **kompilaci direktivy** pole, přidejte [#include](../preprocessor/hash-include-directive-c-cpp.md) kompilátoru směrnice na nový soubor prostředků v souboru hlavní prostředků ve vývojovém prostředí.  
  
     Prostředky v souborů zahrnutých tímto způsobem jsou vytvářeny součástí spustitelný soubor v době kompilace. Nejsou přímo k dispozici pro úpravy nebo změna, když pracujete na vaší hlavní projektového souboru. Budete muset otevřít soubory zahrnuté .rc samostatně. Všechny soubory, které jsou zahrnuty, ale nemáte rozšíření .rc nebude možné upravovat pomocí editory prostředků.  
  

  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)