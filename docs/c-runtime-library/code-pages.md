---
title: "Znakové stránky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.international
dev_langs: C++
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 02c1b7de9a8ed5f560a5999af453970785c487f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="code-pages"></a>Znakové stránky
A `code page` je znaková sada, která může obsahovat čísla, interpunkčních znamének a další zvláštní znaky. Různé jazyky a národní prostředí může používat různé znakové stránky. Například ANSI znaková stránka 1252 slouží pro angličtinu a většina evropských jazyků; Výrobce OEM znaková stránka 932 se používá pro japonské Kanji.  
  
 Znaková stránka může být reprezentován v tabulce jako mapování znaků hodnoty jednobajtové nebo vícebajtové hodnoty. Mnoho znakové stránky sdílet sadu znaků v rozsahu 0x00 – 0x7F znaků ASCII.  
  
 Běhové knihovny Microsoft používá následující typy znakové stránky:  
  
-   Výchozí systémová znaková stránka ANSI. Ve výchozím nastavení při spuštění spuštění systému automaticky nastaví vícebajtové znakové stránky na stránku výchozího systému ANSI kód, který se získávají z operačního systému. Volání:  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     také nastaví ANSI výchozí systémová znaková stránka národního prostředí.  
  
-   Znaková stránka národního prostředí. Chování počet běhové rutiny je závislá na aktuální nastavení národního prostředí, které zahrnuje znaková stránka národního prostředí. (Další informace najdete v tématu [rutiny závislých na národním prostředí](../c-runtime-library/locale.md).) Ve výchozím nastavení používají všechny rutiny závislých na národním prostředí v běhové knihovny Microsoft znakové stránky, která odpovídá na "C", národní prostředí. Při spuštění můžete změnit nebo dotaz znaková stránka národního prostředí používá v volání [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   Vícebajtové znakové stránky. Chování pro většinu rutin vícebajtových znaků v běhové knihovny závisí na aktuální vícebajtové znakové stránky. Ve výchozím nastavení použijte tyto rutiny ANSI výchozí systémová znaková stránka. Při spuštění se můžete dotazovat a změnit vícebajtové znakové stránky s [_getmbcp –](../c-runtime-library/reference/getmbcp.md) a [_setmbcp](../c-runtime-library/reference/setmbcp.md), v uvedeném pořadí.  
  
-   ANSI tak, aby odpovídaly národního prostředí, ve kterém programy C provedli tradičně je definována národního prostředí "C". Znaková stránka národního prostředí "C" ("C" kódové stránky) odpovídá znaková sada ASCII. Například v národním prostředí "C" `islower` vrací hodnotu true pro hodnoty 0x61 - pouze 0x7A. V jiné národním prostředí `islower` může vrátit hodnotu true pro tyto a také jiné hodnoty, podle definice toto národní prostředí.  
  
## <a name="see-also"></a>Viz také  
 [Internacionalizace](../c-runtime-library/internationalization.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)